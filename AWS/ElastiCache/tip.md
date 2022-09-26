[ElastiCache がフェイルオーバーした際に気をつけるべき redis-rb の利用方法について](https://qiita.com/dany1468/items/8946cd5e4c853b48bffd)

[AWS ElasticCacheのRedisをDefault設定で使ったときのConnection Leakの解決方法](https://hackerslab.aktsk.jp/technology/aws-elasticcache-timeout-parameter/)  
カスタムパラメータグループを用意して、timeoutの設定を60秒とかにしておこう。正しくConnectionを切断できていないとたまり続けてエラーになることがあるかも

