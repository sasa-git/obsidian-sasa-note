[mysqldumpまとめ](https://qiita.com/PlanetMeron/items/3a41e14607a65bc9b60c)

```
# データベース
$ mysqldump -u USER_NAME -p -h HOST_NAME DB_NAME > OUTPUT_FILE_NAME

# テーブル
$ mysqldump -u USER_NAME -p -h HOST_NAME DB_NAME TABLE_NAME > OUTPUT_FILE_NAME

# テーブルの定義とデータのダンプ
$ mysqldump -u USER_NAME -p -h HOST_NAME -A -n > OUTPUT_FILE_NAME 


# 出力されたスクリプトファイルの実行
$ mysql -u USER_NAME -p -h HOST_NAME DB_NAME < OUTPUT_FILE_NAME
```

[データベースの内容を残しながらMySQLのバージョンを更新する](https://hacknote.jp/archives/37441/)

```
$ mysqldump -u root wordpress > dump.sql

$ mysql -uwpuser -p -Dwordpress < dump.sql
```