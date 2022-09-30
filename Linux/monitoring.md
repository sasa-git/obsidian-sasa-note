[Amazon Linuxでmonitを使ってカジュアルにプロセス監視する！](https://qiita.com/tmknom/items/5204b2920bfab01a1289)

[Monit で pidfile が存在しないプロセスを監視する](https://akishin.hatenablog.jp/entry/20130802/1375399909)

例
```
check process diced matching "diced"
  start program = "/usr/local/DiCE/diced -d -l"
  stop  program = "/usr/bin/pkill diced"
  if 5 restarts within 5 cycles then unmonitor
```

[monitで手軽にプロセスの監視を行う](https://qiita.com/mobius01/items/6e7567509bd893be0e3e)

[Monitでサーバー監視（基本的な設定、CPU、メモリリソースの監視設定）](https://www.conversion.co.jp/tecblog/20200807/)

[【細かすぎて伝わらないかもしれない tips】時代はイミュータブルインフラストラクチャだけど, 敢えて monit について書いてみる](https://inokara.hateblo.jp/entry/2019/03/21/093051)

