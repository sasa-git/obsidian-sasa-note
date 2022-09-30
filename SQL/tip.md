[MySQLのデータディレクトリを移動する](https://qiita.com/ShuM/items/1a960b4ef53f8a08dd5a)  
情報古そう

[主キーとIndexについて整理する](https://qiita.com/pirorirori_n712/items/b47ade3fdaf8b4a109ba)

[DBのインデックスと複合インデックス](https://qiita.com/towtow/items/4089dad004b7c25985e3)

[MySQL クエリキャッシュの概要と導入・評価方法](https://weblabo.oscasierra.net/mysql-query-cache/)

[【図解】B-treeを理解し、複合インデックスの順番を正しく作る](https://nishinatoshiharu.com/overview-multicolumn-indexes/)

[MySQLにおける、複合Indexを貼る際の良い順番とは](https://tech.excite.co.jp/entry/2021/04/27/150029)

[MySQL クエリキャッシュ値設定と確認方法](https://qiita.com/tukiyo3/items/797f9916e6494ec33991)

```
mysql> SHOW STATUS LIKE'Qcache%'; # でキャッシュを見てみる
# Qcache_queries_in_cacheという値が0になってなければ、クリアをキャッシュしてみる
mysql> RESET QUERY CACHE; 
mysql> flush tables; # これでもクエリキャッシュを削除できる
```

[FLUSH 構文](http://download.nust.na/pub6/mysql/doc/refman/5.1-olh/ja/flush.html)

[問合せキャッシュのステータスとメンテナンス](https://dev.mysql.com/doc/refman/5.6/en/query-cache-status-and-maintenance.html)
