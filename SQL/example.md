```
"users" というユーザーのテーブルがあって、"created_at" という日付型のカラムに登録日が保存されているとします。

このとき、「ある月ごとの新規登録ユーザー数」は以下の SQL などで求められます。

SELECT
DATE_FORMAT(created_at, '%Y%m') AS 年月,
COUNT(*) AS 登録ユーザー数
FROM
users
GROUP BY
DATE_FORMAT(created_at, '%Y%m')
```

その月の時点でのユーザー数の合計も同時に求めたい
```sql
SELECT DATE_FORMAT(u1.created_at, '%Y%m') AS 年月,
COUNT(*) AS 登録ユーザー数,
( select count(*) from users u2 where DATE_FORMAT(u2.created_at, '%Y%m')<=DATE_FORMAT(u1.created_at, '%Y%m') ) 累計ユーザー数
FROM users u1
GROUP BY DATE_FORMAT(created_at, '%Y%m')
```


