[AWS Lambda の新機能 – コンテナイメージのサポート](https://aws.amazon.com/jp/blogs/news/new-for-aws-lambda-container-image-support/)

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

[コンテナイメージとして定義された関数の呼び出し](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/invocation-images.html)

[コンテナだけどサーバーレス！ AWS Lambda の最新機能をご紹介](https://dev.classmethod.jp/articles/awssummit2021-lambda-container-support/)

[コンテナイメージで Python Lambda 関数をデプロイする](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/python-image.html)

[awslambdaric](https://pypi.org/project/awslambdaric/)

[Lambda コンテナイメージをローカルでテストする](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/images-test.html)

[Lambda Container Image Runtime 躓きメモ](https://zenn.dev/sandship/articles/7c00a06fe3ba8d)

[カスタムランタイム の Lambda をコンテナイメージ化してみた](https://sadayoshi-tada.hatenablog.com/entry/2021/01/29/090600)

[LambdaをカスタムDockerランタイムで開発する方法](https://future-architect.github.io/articles/20210914a/)

Dockerfile 例

```Dockerfile
FROM public.ecr.aws/lambda/python:3.9

ENV AWS_CLI_VERSION=2.0.30

COPY app.py ${LAMBDA_TASK_ROOT}
COPY .env ${LAMBDA_TASK_ROOT}
COPY requirements.txt ${LAMBDA_TASK_ROOT}
COPY templates/ ${LAMBDA_TASK_ROOT}/templates/

RUN set -ex \
  && yum update -y && yum install -y \
    unzip \
    tar \
    gzip

RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-${AWS_CLI_VERSION}.zip" -o "/tmp/awscliv2.zip" \
  && unzip /tmp/awscliv2.zip -d /tmp/ \
  && /tmp/aws/install \
  && rm -rf /tmp/aws*

RUN curl -o kubectl -sL "https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl" \
  && chmod +x ./kubectl \
  && mv ./kubectl /usr/local/bin/kubectl

RUN curl -sL "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp \
  && mv /tmp/eksctl /usr/local/bin


RUN pip3 install -r requirements.txt --target "${LAMBDA_TASK_ROOT}" \
  && mkdir -p ${LAMBDA_TASK_ROOT}/templates/output

CMD ["app.handler"]
```

カスタムランタイムのイメージの参考  
[【AWS】Lambdaがコンテナイメージに対応！お手軽にAWS CLIなどの実行スケジュールも組める！](https://noname.work/2612.html)

ALB x Lambda  
[ターゲットとしての Lambda 関数](https://docs.aws.amazon.com/ja_jp/elasticloadbalancing/latest/application/lambda-functions.html#enable-health-checks-lambda)

M1 macなどarm アーキテクチャでbuildしたイメージは、関数作成時にarm64を指定すること！  
[arm64 アーキテクチャの Lambda 関数で Runtime.InvalidEntrypoint が発生するときの対処方法](https://dev.classmethod.jp/articles/tsnote-runtime-invalidentrypoint-occurs-in-arm64-lambda-function/)

