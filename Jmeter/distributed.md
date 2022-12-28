[13. Remote Testing](https://jmeter.apache.org/usermanual/remote-test.html)  
公式doc

```
13.3 ヒント
JMeter/RMI では、クライアントからサーバーへの接続が必要です。これは、選択したポート (デフォルトは1099 ) を使用します。
JMeter/RMI では、サンプル結果をサーバーからクライアントに返すために逆接続も必要です。
これらは大きな番号のポートを使用します。これらのポートは、jmeter.properties内のclient.rmi.localportというjmeter
プロパティによって制御できます。 これがゼロ以外の場合、クライアント エンジンのローカル ポート番号のベースとして使用されます。現時点では、JMeter はclient.rmi.localportで定義されたポートから始まる最大 3 つのポートを開きます。
```

🌟[テスト実施#7_マスタスレーブ構成を用いた負荷テストの行い方](https://ptune.jp/tech/how-to-perform-a-load-test-using-a-master-slave-configuration/)  
わかりやすい。スレーブ利用時の注意点が書かれている

> 指定したスレッド数で、各スレーブサーバから実行されます。スレーブサーバの台数を増やしたにもかかわらず、スレッド数の変更をしないと合計スレッド数が一気に大きくなってしまいます。
> たとえば、スレッド数100でスレーブ1台のみで実行した場合はスレッド数は100となり、スレーブ2台の場合は「100×2」でスレッド数200になります。JMeterの負荷分散のつもりが、急激な負荷上昇につながるので注意しましょう。

[JMeter の Master/Slave 構成のコンフィグレーションと実行](https://qiita.com/TsuyoshiUshio@github/items/f8752b08e3b2267878f2)

[JMeter Client/Server Remote Testing on Docker](https://qiita.com/h-r-k-matsumoto/items/50b5d92a3edebb09a4fd)

Docker composeを使わない、純粋にDockerだけでclient/server構成を作っている例。パラメータの説明が詳しくありわかりやすい。

```
Server
server_port , server.rmi.localportで使うポートを指定して、-p20000:20000 でポートを空ける。
server.rmi.ssl.disable=true はSSLは利用しないので、無効化。
java.rmi.server.hostnameではClientからはホストのIPでつけつけるので、ホストのIPを $(host $(hostname)| awk '{print $4}') で埋め込み。
Cleint<->Server間の通信が多い(数千qps以上)ので、Statisticalで通信量削減します。

Client
client.rmi.localport=20001 でポート番号を固定化。最大3つ使われるので、 -p20001:20001 -p20002:20002 -p20003:20003 でポートを空ける。
server.rmi.ssl.disable=true はSSLは利用しないので、無効化。
java.rmi.server.hostnameではClientからはホストのIPでつけつけるので、ホストのIPを $(host $(hostname)| awk '{print $4}') で埋め込み。
remote_hosts でリモートサーバー指定。
-t でスクリプトファイル、 -l で結果ファイルを指定します。
```



[Mac の JMeter クライアントから EC2 環境の JMeter サーバを使って負荷試験を行う](https://satotech.hatenablog.com/entry/20141214/1418560404)  
自分の Mac を JMeter クライアント にして、EC2 上の JMeter サーバ を使う設定。以下のようなパラメータの内容が載っている

```
# JMeter サーバの設定、起動
server_port=24000                   # JMeter 接続に使用するサーバ側のポート
server.rmi.localhostname=127.0.0.1  # サーバ側で RMI 通信に使用するローカルホスト名
server.rmi.localport=26000          # サーバ側で RMI 通信に使用するポート

# JMeter クライアント側の設定
remote_hosts=127.0.0.1:24000    # JMeter クライアントが使用する JMeter サーバの情報
client.rmi.localport=25000      # JMeter クライアントが RMI 通信で受信に使用するポート
mode=Statistical                # JMeter サーバからの結果の通知方法
```

[クラスター構成のJmeterで負荷試験](https://qiita.com/sh_tomato/items/77963c733a572c8acafd#%E3%82%B9%E3%83%AC%E3%83%BC%E3%83%96%E3%82%B5%E3%83%BC%E3%83%90%E3%83%BC%E3%81%AE%E3%82%BB%E3%83%83%E3%83%88%E3%82%A2%E3%83%83%E3%83%97)

[java.rmiプロパティ](https://docs.oracle.com/javase/jp/8/docs/technotes/guides/rmi/javarmiproperties.html#:~:text=java.rmi.server.hostname,%E6%96%87%E5%AD%97%E5%88%97%E3%82%92%E8%A1%A8%E3%81%97%E3%81%BE%E3%81%99%E3%80%82)

```
java.rmi.server.hostname
このプロパティの値は、リモート・オブジェクト上のメソッドの呼出しをクライアントから可能にするために、ローカルに作成されたリモート・オブジェクトのリモート・スタブに関連付けられるホスト名文字列を表します。このプロパティのデフォルト値はローカル・ホストのIPアドレス(ドットで区切られた形式)です。
```

[13. リモートテスト](https://jmeter.apache.org/usermanual/remote-test.html#tips)

[プロキシ環境下で JMeter を CLI から Server-Client 構成で実行する](https://techblog.sakurug.co.jp/article/000202/#JMeter%20Server%20%E3%81%AE%E8%B5%B7%E5%8B%95)  
-> パラメータの説明が豊富


```
sudo docker run -it --rm \
     -p20000:20000 \
     justb4/jmeter:5.4 \
     -s -n -j /dev/stdout \
     -Dserver_port=20000 -Dserver.rmi.localport=20000 \
     -Dserver.rmi.ssl.disable=true \
     -Djava.rmi.server.hostname=$(host $(hostname)| awk '{print $4}') \
     -Jmode=Statistical
```

> -p20000:20000 20000 番ポートを空ける
> -Dserver_port=20000 -Dserver.rmi.localport=20000 使用するポートを指定する
> -Dserver.rmi.ssl.disable=true SSLを無効化
> -Djava.rmi.server.hostname=$(hostname -i | awk '{print $1}')
> RMI（Remote Method Invocation）の設定。自身のホストサーバのIPアドレスを取得する
> -Jmode=Statistical Cleint - Server間の通信量が多いため Statistical を設定して通信量を削減

```
# JMeterClient の起動
./run.sh -Dlog_level.jmeter=DEBUG \
        -Djava.rmi.server.hostname=$(hostname -i | awk '{print $1}') \
        -Dclient.rmi.localport=20001 \
        -Dserver.rmi.ssl.disable=true \
        -Jremote_hosts=${server-IPAddress}:20000 \
        -Jmode=Statistical \
        -n -t test/test.jmx -l test/test.jtl \
        -j test/jmeter.log \
        -e -o report -r -X
```

> -Dlog_level.jmeter=DEBUG JMeter のログレベル
> -Djava.rmi.server.hostname=$(hostname -i | awk '{print $1}')
> RMI（Remote Method Invocation）の設定。自身のホストサーバのIPアドレスを取得する
> -Dclient.rmi.localport=20001 デフォルトではポート番号が動的に使用されてしまうため固定化する
> -Dserver.rmi.ssl.disable=true SSLを無効化
> -Jremote_hosts=${server-IPAddress}:20000 リモートサーバのIPアドレスとポート番号を指定（リモートサーバは 20000 ポートを空けます）
> -Jmode=Statistical Cleint - Server間の通信量が多いため Statistical を設定して通信量を削減
> -n JMeter をCLIモードで実行
> -t JMeter のシナリオファイルを指定
> -l JMeter の結果ファイルを指定
> -j JMeter のログファイルを指定
> -e JMeter 実行後にダッシュボードのレポートファイル作成
> -o ダッシュボードのレポートファイルを指定
> -r remote_hosts で指定されたサーバでテストを実行
> -X テスト終了時にサーバを終了（ログアウト）する


いろんな例

https://github.com/apolloclark/jmeter

[distributed-jmeter-docker](https://github.com/pedrocesarti/distributed-jmeter-docker/blob/master/scripts/docker-entrypoint.sh)  
https://github.com/pedrocesarti/distributed-jmeter-docker/blob/master/k8s/templates/jmeter-server-service.yaml

