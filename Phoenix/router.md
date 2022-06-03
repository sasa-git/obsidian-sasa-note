[router.ex: /users/44 ←44をつけたくない時](https://hexdocs.pm/phoenix/Phoenix.Router.html#resources/4-options)

> :singleton-IDを参照せずにクライアントによって検索されるシングルトンリソースのルートを定義します。詳細については、以下をお読みください
> シングルトンリソース
> IDを参照せずにリソースを検索する必要がある場合、特定のコンテキストで1つのエントリしか含まれていないため、この:singleton オプションを使用して、そのような単一のリソースに固有のルートのセットを生成できます。
>
>GET /user=>:show
>GET /user/new=>:new
>POST /user=>:create
>GET /user/edit=>:edit
>PATCH /user=>:update
>PUT /user=>:update
>DELETE /user=>:delete
>使用例：
>
>resources "/account", AccountController, only: [:show], singleton: true

