# MongoDB資源

##定義
MongoDB 是開源的文件式資料庫，提供高效能、高可用性和原子的擴展(automatic scaling)。

### 文件式資料庫
一筆記錄在MongoDB中是一個文件，這裡文件指的是用欄位和值成對組成的資料結構。MongoDB文件類似JSON物件。欄位的值可以是其他的文件、陣列以及文件的陣列。使用文件的好處是:
- 文件在許多程式語言中都是原生的物件類型
- 內嵌文件和陣列減少昂貴的join成本
- 動態schema 支援豐富的多樣型態

## 主要特點
### 高效能
MongoDB提供高效能的資料保存，特別是:

- 支援內嵌資料模型，降低資料庫系統的I/O
- 索引支援快速查詢，並且包含內嵌文件、陣列的鍵值

### 高可用性
為達到高可用性，MongoDB的複寫功能，稱作replica sets，提供
- 原子式的錯誤回復
- 資料冗餘

replica set是一組MongoDB 伺服器，用來組持相同的資料集，提供資料冗餘並增加資料可用性。


### 原子式擴展
MongoDB核心功能就提供橫向擴展能力
- 原子式shading將資料分散在叢集機器上
- Replica sets can provide eventually-consistent reads for low-latency high throughput deployments.

ref: http://docs.mongodb.org/manual/core/introduction/


## MongoDB初步
> mongod& #在背景執行mongo server

> mongo #執行mongo shell

## Sharding
[Mongo DB Sharding 心得筆記 (一)](http://leehom59.blogspot.tw/2011/11/mongo-db-sharding.html)
[Mongo DB - RepliSet Mode 懶人設定筆記](http://leehom59.blogspot.tw/2011/12/mongo-db-repliset-mode.html)

> Written with [StackEdit](https://stackedit.io/).
