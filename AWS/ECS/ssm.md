[Session Manager のカスタム IAM ロールを作成](https://docs.aws.amazon.com/ja_jp/systems-manager/latest/userguide/getting-started-create-iam-instance-profile.html)

[Systems Manager Parameter Store を使用して機密データを指定する]()
```json
    "secrets": [{
      "name": "environment_variable_name",
      "valueFrom": "arn:aws:ssm:region:aws_account_id:parameter/parameter_name"
    }]
```

parameter_nameの部分をコンソールに出てくるパラメータ名に置き換えればおk

