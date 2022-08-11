[【速報】Lambdaのパッケージフォーマットとしてコンテナイメージがサポートされるようになりました！！ #reinvent](https://dev.classmethod.jp/articles/lambda-support-oci-container-image/)

> サポートされないLambdaの機能  
> パッケージ形式としてコンテナイメージを選択した場合、以下の機能は利用できません、
>
> - Lambda Layers
>   - 複数のコンテナイメージで同じライブラリを利用したい場合、対象のライブラリを全てのコンテナイメージに導入しておく必要があります。
> - コード署名の検証
