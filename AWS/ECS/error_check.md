ECSでタスク起動時にエラーになった時の対処例

- タスクはprivate subnet上で起動

```
ResourceInitializationError: unable to pull secrets or registry auth: execution resource retrieval failed: unable to retrieve secrets from ssm: service call has been retried 5 time(s): RequestCanceled: request context canceled caused by: context deadline exceeded
```

- RUNNINGにならず即STOPだった
- cloudwatchにログがなかった

以上からもコンテナではなくECSでのエラーそうだなとわかる

[Amazon ECS で「unable to pull secrets or registry auth」(シークレットまたはレジストリ認証をプルできません) というエラーのトラブルシューティング方法を教えてください。](https://aws.amazon.com/jp/premiumsupport/knowledge-center/ecs-unable-to-pull-secrets/)

にもあるように、ルートをチェックしてみると、privateサブネットのルートテーブルにNAT行きのレコードがなかった。

NATレコードを追加したら動くように！