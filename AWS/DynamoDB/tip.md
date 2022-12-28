[Amazon DynamoDB制限事項](https://qiita.com/inouet/items/269185c80ad36bee8702)

[Amazon DynamoDB のサービス、アカウント、およびテーブルのクォータ](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/ServiceQuotas.html)

[DymanoDBについての備忘録](https://qiita.com/paper2/items/d52c2f78ee946dd18826)

\* [DynamoDBをゲームアプリで使う際の課題と対策（前編）](https://tech.drecom.co.jp/ac2021-how-to-use-dynamodb-in-game-apps-part1/)

[Amazon DynamoDB でサポートされるデータ型と命名規則](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/HowItWorks.NamingRulesDataTypes.html)

[Lambda(python3.6)を使って大量のデータをDynamoDBに追加するときはbatch_writerが便利](https://dev.classmethod.jp/articles/lambda-python-dynamodb/)

[読み込み整合性](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/HowItWorks.ReadConsistency.html)

[DynamoDBでデータを更新する際に使うUpdateExpressionについて一通りまとめてみた](https://dev.classmethod.jp/articles/dynamodb-update-expression-actions/)

[DynamoDBから効率的に大量のデータを取得する方法](https://future-architect.github.io/articles/20210225/)

[TTL を有効化した DynamoDB でちょっと焦った話](https://blog.serverworks.co.jp/tech/2020/06/25/post-87641/)  
> TTL を有効にした DynamoDB に対して有効期限切れのレコードを PutItem すると何も起きない

[DynamoDBキャパシティーモードの切替](https://oji-cloud.net/2019/07/30/post-2572/)

[DynamoDB のプロビジョンされた容量テーブルの設定の管理](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/ProvisionedThroughput.html)

[DynamoDB でのエラー処理](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/Programming.Errors.html)

[DynamoDB でのスキャンの使用](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/Scan.html)

[Amazon DynamoDB のサービス、アカウント、およびテーブルのクォータ](https://docs.aws.amazon.com/ja_jp/amazondynamodb/latest/developerguide/ServiceQuotas.html#default-limits-throughput-capacity-modes)

[execute_statement(LastEvaluatedKey)](https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/dynamodb.html#DynamoDB.Client.query)

[[AWS]boto3で、DynamoDBにクエリをかけるとき、制限件数以上のデータを最後まで取得する](http://blog.livedoor.jp/sce_info3-craft/archives/9431327.html)

> 1.1クエリあたり取得できるのは1MBまで

```
import boto3
dynamodb = boto3.resource('dynamodb')
table = dynamodb.Table("テーブル名")
ExclusiveStartKey = None
while True:
    if ExclusiveStartKey == None:
        response = table.query(KeyConditionExpression="検索キー条件", Limit=最大取得件数)
    else:
        response =  table.query(KeyConditionExpression="検索キー条件", Limit=最大取得件数, ExclusiveStartKey=ExclusiveStartKey)
    if ("LastEvaluatedKey" in response) == True:
        ExclusiveStartKey = response["LastEvaluatedKey"]
    else:
        break
```

