由於Docker唯讀container的特性，學習Docker時，應該很快就會遇到可讀寫資料該怎麼處理的問題。

像是開發專案的程式碼，或是資料庫的資料，或是某些經常異動又需要留存的log。為了這些異動而commit container並不合理。

當然，docker設計了volumn的作法，可以把host的資料夾或檔案mount進container之中，這的確是解決了大多時候的需求，但如果考量到開發環境時，希望contanier可以經常抽換組合或重複利用的話，這種mount的方式，好像又有點問題。

[Persistent volumes with Docker - Data-only container pattern](http://www.tech-d.net/2013/12/16/persistent-volumes-with-docker-container-as-volume-pattern/) 這篇文章介紹了建立一個container，專作資料儲存之用，可以解決上述的狀況。


### 名詞解釋
- AUFS
