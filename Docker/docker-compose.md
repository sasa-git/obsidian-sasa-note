[docker-compose build](https://docs.docker.jp/compose/reference/build.html) 
> --parallel              並列にイメージを構築

[docker-composeを跨いだコンテナ間の名前解決について](https://qiita.com/negineri/items/793f7da3694f819b3b49#docker-compose%E3%81%A8%E5%90%8D%E5%89%8D%E8%A7%A3%E6%B1%BA)

replicasがある場合、`loadtest-cluster-slave-1`のようなドメインで解決できる。 Taurus/jmeter-log/jmeter-distributed.md 参照

[Compose における環境変数](https://matsuand.github.io/docs.docker.jp.onthefly/compose/environment-variables/)  
`.env`ファイルをディレクトリ内に置けばそれを読みに行ってくれる

[新しい docker compose](https://zenn.dev/skanehira/articles/2021-06-03-new-docker-compose)

> Docker Compose CLIとは
> 簡単にいうとdocker-composeのGo実装です。docker-composeと互換しています。
> docker-composeに置き換わることを目標としていて、実装はcompose-specの仕様に準拠しています。
> 既存docker-composeのメンテナンスは継続されるそうです。

> docker-compose.yamlのパースライブラリcompose-goが公開されている
> Docker Compose CLIもそれを利用している
> compose関連のツールの作成が楽になる
> buildkitがデフォルト有効になっている
> Goによる実装なので、既存のエコシステム（Docker CLIのSDKなど）を利用できる
> 実際内部ではSDKを使ってDocker Engineとやりとりしている

