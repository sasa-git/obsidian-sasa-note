[【Elixir】moxを使用してmock用いたテストを書く](https://sanposhiho.com/posts/elixir-mox/)

前提知識:  
[ElixirでBehaviourを使用してDIPを実現する基礎知識](https://sanposhiho.com/posts/elixir-behaviour/)

参考(extwitter):
[extwitter](https://github.com/parroty/extwitter/blob/master/lib/extwitter/behaviour.ex)

Behaviourは、モジュールの抽象化をおこなっているモジュール
moxは、Behavioutを指定することで、それをもとにmockを生成してくれる

Behaviourモジュールがあって、その下にmockと実際の環境で使うモジュールの実態がさくらんぼみたいな形でぶら下がってると想像すると良さそう  
これで、テスト環境では外部APIを叩かず、mockで返すようにする、といったことができる

