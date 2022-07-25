[Pythonを使ってAmazon S3にファイルをアップロードする](https://qiita.com/honda28/items/bf71c2b39e8ab109fda3)  
using client()

[boto3を使ってS3にファイルのアップ＆ダウンロード](https://qiita.com/yuni/items/e68c14a63e3a2eaaae71)  
using resource()

[boto3を使いdynamoDBに上書きさせずにデータを保存](https://hacknote.jp/archives/25554/)

```py
# {key: "hoge", value: "hoge"}がすでにDynamoDB上に存在
table.put_item(
    Item={
        'key': "hoge",
        'value': "piyo"
    },
    ConditionExpression='attribute_not_exists(key)'
)
# すでにkey="hoge"のデータが保存されているので上書きせずエラーを返す
```

[Python (boto3) で DynamoDB の条件付き項目追加・更新をやってみる](https://michimani.net/post/aws-operate-dynamodb-by-python/)

[DynamoDBの query() で FilterExpression を使ってデータ取得条件を設定する](https://dev.classmethod.jp/articles/dynamodb-query-use-filterexpression/)

[比較演算子および関数リファレンス](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/Expressions.OperatorsAndFunctions.html)

