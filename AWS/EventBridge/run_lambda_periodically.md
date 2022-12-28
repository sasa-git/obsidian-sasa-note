[AWS Lambdaで遊ぼう #2 Lambda関数を定期実行する](https://zenn.dev/nakam_aws/articles/47be7b2c5a952e)

[チュートリアル: EventBridge を使用した AWS Lambda 関数のスケジュール](https://docs.aws.amazon.com/ja_jp/eventbridge/latest/userguide/eb-run-lambda-schedule.html)

eventbridgeでlambda定期実行するとき、コンソール上でターゲットを作成した場合、自動でlambda トリガー(permission)が追加されるが、terraformなどを使う場合は手動で作る必要がある

[Lambda 関数が EventBridge ルールによってトリガーされなかったのはなぜですか?](https://aws.amazon.com/jp/premiumsupport/knowledge-center/eventbridge-lambda-not-triggered/)

[Resource: aws_lambda_permission](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lambda_permission)

`lambda permissionのsource_arn` には `aws_cloudwatch_event_rule` のARNを指定すること。`aws_cloudwatch_event_target` のARNではないぞ！ 
`aws_cloudwatch_event_target` のarn属性にはlambdaのarnが参照されているぞ！！

https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/lambda_permission#source_arn  
> For EventBridge events, this should be the ARN of the EventBridge Rule.

`aws_cloudwatch_event_rule` の `schedule_expression` パラメータの例
https://docs.aws.amazon.com/ja_jp/AmazonCloudWatch/latest/events/ScheduledEvents.html#RateExpressions

```
  schedule_expression = "rate(1 day)"
```

[AWS Lambdaで遊ぼう #2 Lambda関数を定期実行する](https://www.benjamin.co.jp/blog/technologies/lambda-2-eventbridge/)

