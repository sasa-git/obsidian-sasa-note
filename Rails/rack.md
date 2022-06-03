[【Ruby】Rack の env に格納される "CONTENT_TYPE" が なぜ大文字・アンダースコア区切りなのか調べてみた](https://blog.serverworks.co.jp/rack_env_content_type)

[ヘッダのキーが変わるところのソース](https://github.com/rails/rails/blob/3872bc0e54d32e8bf3a6299b0bfe173d94b072fc/actionpack/lib/action_dispatch/http/headers.rb#L121)

[4.2 JSONパラメータ](https://railsguides.jp/action_controller_overview.html#json%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF)  
リクエストのContent-Typeヘッダーでapplication/jsonを指定すると、Railsがパラメータを自動的にparamsハッシュに読み込み、以後は通常のparamsハッシュと同様に操作できるようになります。