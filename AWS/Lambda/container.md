[【速報】Lambdaのパッケージフォーマットとしてコンテナイメージがサポートされるようになりました！！ #reinvent](https://dev.classmethod.jp/articles/lambda-support-oci-container-image/)

> サポートされないLambdaの機能  
> パッケージ形式としてコンテナイメージを選択した場合、以下の機能は利用できません、
>
> - Lambda Layers
>   - 複数のコンテナイメージで同じライブラリを利用したい場合、対象のライブラリを全てのコンテナイメージに導入しておく必要があります。
> - コード署名の検証

[Lambda 関数の Inactive 状態を回避するにはどうすればよいですか？](https://dev.classmethod.jp/articles/tsnote-aws-lambda-how-can-i-avoid-the-inactive-state-of-the-lambda-function/)

> 数週間利用しないと Inactive 状態になり、Inactive 状態だと呼び出しに失敗します
> 方法
> 1. プロビジョニング済み同時実行を設定する
> 2. 定期的に Lambda 関数を呼び出す
