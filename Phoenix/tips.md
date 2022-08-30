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