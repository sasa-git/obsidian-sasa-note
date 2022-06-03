[4.2 JSONパラメータ](https://railsguides.jp/action_controller_overview.html#json%E3%83%91%E3%83%A9%E3%83%A1%E3%83%BC%E3%82%BF)

>Webサービスを開発していると、パラメータをJSONフォーマットで受け取りたくなることがありま>す。リクエストのContent-Typeヘッダーでapplication/jsonを指定すると、Railsがパラメー>タを自動的にparamsハッシュに読み込み、以後は通常のparamsハッシュと同様に操作できるように>なります。
>
>たとえば、以下のJSONコンテンツを送信したとします。
>
>{ "company": { "name": "acme", "address": "123 Carrot Street" } }
>コントローラのparams[:company]は、{ "name" => "acme", "address" => "123 Carrot >Street" }という値を受け取ります。

