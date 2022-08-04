[13. Remote Testing](https://jmeter.apache.org/usermanual/remote-test.html)  
公式doc

```
13.3 ヒント
JMeter/RMI では、クライアントからサーバーへの接続が必要です。これは、選択したポート (デフォルトは1099 ) を使用します。
JMeter/RMI では、サンプル結果をサーバーからクライアントに返すために逆接続も必要です。
これらは大きな番号のポートを使用します。これらのポートは、jmeter.properties内のclient.rmi.localportというjmeter
プロパティによって制御できます。 これがゼロ以外の場合、クライアント エンジンのローカル ポート番号のベースとして使用されます。現時点では、JMeter はclient.rmi.localportで定義されたポートから始まる最大 3 つのポートを開きます。
```

[テスト実施#7_マスタスレーブ構成を用いた負荷テストの行い方](https://ptune.jp/tech/how-to-perform-a-load-test-using-a-master-slave-configuration/)  
わかりやすい。スレーブ利用時の注意点が書かれている

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
