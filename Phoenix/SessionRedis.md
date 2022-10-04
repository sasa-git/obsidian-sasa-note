## phoenix のセッション管理にredisを使う

主に2種類あるが、PhoenixSessionRedisを利用

[PhoenixSessionRedis](https://hexdocs.pm/phoenix_session_redis/PhoenixSessionRedis.html)
[Github](https://github.com/igrs/phoenix_session_redis)

以下の設定がないと動かない(ここで沼った)から注意！

```mix.exs
# :poolboyを追加
def application do
    [
      mod: {SampleWeb.Application, []},
      extra_applications: [:logger, :poolboy, :runtime_tools, :gettext]
    ]
  end
```

これが最近でメンテナンスされているもの。こっちを使った方がいいかも？
[redbird](https://github.com/thoughtbot/redbird)

↓もあるが、動かなかった
[plug_session_redis](https://github.com/aposto/plug_session_redis)

古い情報
[今更ながらPhoenixでRedisをsessionに使う](https://qiita.com/h-tko/items/044c8964353d00b2bfc6)



## Session Storeについて

[Plug: Session stores](https://hexdocs.pm/plug/Plug.Session.html#module-session-stores)

