有個專案，使用的是centos 5.5的作業系統，PHP是5.1版本，最近需要維護更新，缺少測試機的環境，剛好是個測試docker的好機會。

手邊沒有多餘的機器，所以就開了一臺EC2來使用，預計等到上線之後就可以關掉。

一開始也有想過會不會剛好EC2有Centos 5.5的Image，也沒有必要再過一層docker，不過沒有找到剛好合用的，那就還是依原計劃用Docker吧。

規劃的測試機的運作方式是:

* 開發人員從本地端更新code到testing這個branch
* 推code到bitbucket
* 由bitbucket通知測試機更新Code
* 測試機從bitbuket更新code到機器上mirror的repo
* 透過設定GIT_WORK_TREE的方式，checkout testing的code到網站所在的目錄下(這樣可以避免將git的資料放在網站的目錄下，造成潛在的風險)

至於具體作法可以參考這一篇: [Automated git deployments from Bitbucket](http://jonathannicol.com/blog/2013/11/19/automated-git-deployments-from-bitbucket/)

其實需要做的步驟不多，但是卡關卡蠻久的。原因在後頭容我娓娓道來。但我們先看一下如何用Docker來做測試機。

## 前有攔路虎
最初的想法，就是將web與db各用一個image來做。web使用的是 centos:centos5，db用的是centurylink/mysql。 不過web image再依專案的需求，加上php、httpd和ssh server等。

這個組合很容易建立起來，但是前方的難關也很快出現，跟Bitbucket的同步一直失敗。

先是查httpd的log，看起來bitbuket的POST有作用，bitbuket的payload也都有正確的載到log中(用上文的`file_put_contents('deploy.log', serialize($_POST['payload']), FILE_APPEND);`來查)。但是程式碼就是無法正確更新。

找了半天後來發現php缺少json的模組，要打算安裝它的時候，發現yum套件不支援，想要自己compiled，卻發現又少東少西的，這個環境要弄到可以正常跑，還要花不少力氣。

因為目前的環境已經可以跑專案了，只是無法自動同步，為了自動同步這件事再花時間調整，時間上有點不上算，於是決定換個作法。



## 用Fig搭建環境

fig.yml
> web:
  image: ithome/centos5
  ports:
    - "80:80"
    - "2222:22"
  links:
    - db
  volumes_from:
    - datacode
db:
  image: centurylink/mysql
  ports:
    - "3306:3306"
  environment:
    MYSQL_DATABASE: project
    MYSQL_USER: username
    MYSQL_PASSWORD: password
datacode:
  image: ithome/data-code
  volumes:
    - /var/www/Code:/var/www/project