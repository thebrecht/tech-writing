# 利用 Vagrant 和 Virtual Box 搭建 Wordpress 開發環境

由於開發 Wordpress 需要有Web Server、資料庫和PHP的環境，為了減化開發時的複雜性，又不想在電腦上安裝平時用不到的伺服器軟體，最好的方式便是用虛擬機器隔離開。

為達到這個目的，我們會使用Vagrant這個虛擬機器管理工具和Virtual Box這個虛擬機器軟體。

## 安裝開發環境所需工具
- 下載並安裝 VirtualBox 4.3.x(https://www.virtualbox.org/wiki/Downloads)
- 下載並安裝 Vagrant 1.6.x (http://www.vagrantup.com/downloads.html)

## 安裝Vagrant 外掛
請在命令列底下執行以下執行(cmd.exe)

- vagrant-hostsupdater 用來協助處理開發時的網址設定
> vagrant plugin install vagrant-hostsupdater #執行執令

- vagrant-triggers 協助進階指令執行的外掛
> vagrant plugin install vagrant-triggers #執行指令

## 下載 Vagrant 為 Wordpress 開發準備的程式
- 建立 wordpress-dev 目錄
- 下載相關檔案到wordpress-dev 目錄 https://github.com/varying-vagrant-vagrants/vvv/releases
- 在該目錄解開後，執行下面指令 
> vagrant up #開始一連串的環境設定執行，時間會有點久


## wordpress 
網址: http://local.wordpress.dev
帳號: admin
密碼: password


### 參考資料
- https://github.com/Varying-Vagrant-Vagrants/VVV
