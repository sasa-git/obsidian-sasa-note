[使ってない依存パッケージがmix.lockに残ってるとき](https://joe-noh.hatenablog.com/entry/2018/02/25/165317)  
`$ mix deps.unlock --unused`

[ライブラリ探すのに良さそうなサイト](https://libs.garden/elixir/search?q=redis+session)

[mix.exsのapplicationsとextra_applicationsは何が違うのか](https://qiita.com/Tsuyoshi84/items/26eb65e92c7974dd163c)

[EnumType](https://hexdocs.pm/enum_type/readme.html)

[How to download or save files locally in Phoenix](https://stackoverflow.com/questions/49610937/how-to-download-or-save-files-locally-in-phoenix)  

```elixir
path = Application.app_dir(:my_app, "priv/prospectus.pdf")
send_download(conn, {:file, path})
```

[Phoenix File Download](https://elixirforum.com/t/phoenix-file-download/13793)

https://hexdocs.pm/phoenix/Phoenix.Controller.html#send_download/3

[Testing AWS in Elixir](https://andrealeopardi.com/posts/testing-aws-in-elixir/)

[Mocking with s3 ex_aws_s3](https://elixirforum.com/t/mocking-with-s3-ex-aws-s3/26094)

[LiveViewで認証付きのチャットアプリを構築する](https://www.870labo.com/posts/create-chat-app-with-liveview-part6)

[作って学ぶPhoenix LiveView、チャットアプリの作成](https://qiita.com/pojiro/items/dc8c9d97be82f91560bf)

[Phoenix 1.3のディレクトリ構造とContext](https://qiita.com/shufo/items/f0c85a100728a39dde13)

[Phoenixでcookieを取得／発行（システム間連携やサードパーティcookie利用、レガシーシステム接続で役立つ）](https://qiita.com/piacerex/items/46df95fd5c1dd75b3f96#cookie%E3%81%AE%E5%8F%96%E5%BE%97)

[Reading custom request headers](https://elixirforum.com/t/reading-custom-request-headers/11731)

[mcrumm/live_upload_example](https://github.com/mcrumm/live_upload_example)

[daisyUIを組み込んだPhoenixアプリをDockerで本番展開しようとしたらデコった内容が反映されないときに確認すること](https://qiita.com/torifukukaiou/items/9a4b9add065219db339c)

[Get current environment name](https://stackoverflow.com/questions/35010950/get-current-environment-name)

> Mix.env() doesn't work in production or other environments where you use compiled releases (built using Exrm / Distillery) or when Mix just isn't available.
> `config :your_app, env: config_env()`

