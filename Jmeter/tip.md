[JMeter簡易リファレンス](http://sy5.sakura.ne.jp/jmeter/ref/preprocessorsindex.html)  
カウンタ, 正規表現抽出とか色々参考になる

[jmeterで使えるfunction](https://y0m0r.hateblo.jp/entry/20130208/1360327614)

Jsonの値をjmeterのシナリオ上で保存する時、正規表現抽出よりもJson Extractorを使った方がいい

[JMeter's JSON Path Extractor Plugin - Advanced Usage Scenarios](https://www.blazemeter.com/blog/json-path-extractor-jmeter)
↑のが参考になる

[How to Use the JSON Extractor For Testing](https://www.blazemeter.com/blog/json-extractor)

[JSON/YAML Path Extractor](https://jmeter-plugins.org/wiki/JSONPathExtractor/)

json内のキーの指定方法は、JSONPath式というのを使う

ドット表記・ブラケット表記がある

> JSONPath expressions can use the dot–notation
> 
> $.store.book[0].title
> 
> or the bracket–notation
> 
> $['store']['book'][0]['title']

> The following XPath expression
> 
> /store/book[1]/title
> 
> would look like
> 
> x.store.book[0].title
> 
> or
> 
> x['store']['book'][0]['title']

[# JSONPath - JSON の XPath](https://goessner.net/articles/JsonPath/)  
↑JSONPathの例もあるからおすすめ

[20. Functions and Variables](https://jmeter.apache.org/usermanual/functions.html)

[Jmeterの機能いろいろメモ](https://qiita.com/Natsumi_Shimizu/items/bf9061c4fb42685194d0#%E3%83%A9%E3%83%B3%E3%83%80%E3%83%A0%E3%81%AA%E6%95%B0%E5%AD%97%E3%82%92%E5%85%A5%E3%82%8C%E3%81%9F%E3%81%84random-variable)

[JMeterでJSON形式のデータをPOSTリクエストで送信する方法](https://hiyo-ac.hatenablog.com/entry/2019/08/31/224056)

[jMeterでjson形式のデータをpostする](https://qiita.com/gonshi_com/items/29310a419cde8d19768e)

`{"key": "value", "num": 123}` のような形式で書く。シングルクオーテーション `'` は受け付けない


[JMeterの変数と関数について : 概要、便利な関数、ハマりどころ/便利どころ](https://qiita.com/malbare932/items/b94223e1ebf2653e7b65)
> ハマりどころ : スクリプティング系のエレメント内における処理順序
> 「後処理」カテゴリなどで利用されるBeanShell・JavaScript等によるスクリプトにおいては、
> 
> まず最初に${}に対する展開が行われ、
> その結果として得られたスクリプトが実行される
> という順序で処理が行われます。また、その際は${}が""や''で囲われていても展開されます。このことに注意してスクリプトを実装しないと、型エラー等に惑わされて苦> しむことになります。
> もっとも、スクリプト内で変数を参照・設定する場合はvars.get/vars.putを使えるので、そちらを使う方がトラブルが少なく済むのではないかとも思われます。


正規表現抽出の例  
[JMeterで、viewのidを引き継いでリクエストを行う](https://ds-infolib.hcltechsw.com/ldd/ddwiki.nsf/page.xsp?documentId=C4919A9018A5FDDA85257D34004345BC&action=openDocument)  
[JMeterでリクエストパラメータを使いまわす](https://tm8r.hateblo.jp/entry/20130306/1362580220)  
[【JMeter】前のレスポンスの値を次のリクエストに渡す方法](https://bbh.bz/2020/04/09/jmeter-create-request-using-pre-response/)  

[JMeter Server 起動が java.rm.server.ExportException でFailするときのFix を考える](https://qiita.com/TsuyoshiUshio@github/items/f24bf4d12e2280fe16d6)

