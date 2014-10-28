# 使用Docker Image建立 iThome Member測試環境

## 將專案程式碼拉回本地端

 1. 建立~/Code/ithome目錄 &&  cd ~/Code/ithome
 2. 將專案拉回本地端 
 > git clone https://xxx@bitbucket.org/ithome/member.git  #因為是private專案，XXXX是bitbucket的username，可直接上bitbuket上查看HTTPS的路徑

## 匯入docker image

 1. 取得專案的image檔
 2. sudo docker load -i /path/to/xxx.tar

## 啟動docker Image
以下指令會啟動：

 - apache(port 3000)
 - mysql
 - phpmyadmin
 - ssh server(port 2222)
 - 將~/Code/ithome/member 路徑 mount 到/var/ithome/member

> suod docker run -d -p 2222:22 -p 3000:80 -v  ~/Code/ithome/member:/var/ithome/member ithome/member

## 結束Docker
檢查目前的執行中的image
> sudo docker ps 

記下CONTAINER ID之後

> sudo docker stop <container id>

## 存取Docker各項服務方法

### phpmyadmin
存取路徑：http://localhost:3000/phpmyadmin
帳號：root
密碼留白

### ssh
> ssh root@localhost -p 2222 
> \#密碼：admin


## 其他注意事項

 1. 對資料庫的修改在結束之後並不會保留下來，如果需要保留修改，則需要對docker image commit
 2. 如果對一直執行sudo覺得麻煩的話，可以把自己的帳號加入到docker groups
 
> usermod -a -G docker your-username   
> \#執行後需登出再登入才會生效

