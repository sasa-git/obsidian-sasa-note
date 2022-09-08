[Plug pipeline](https://hexdocs.pm/phoenix/Phoenix.Controller.html#module-plug-pipeline)

> ルーターと同様に、コントローラーにも独自のプラグ パイプラインがあります。ただし、ルーターとは異なり、コントローラーには単一のパイプラインがあります。
> `:authenticate`プラグはアクションの前に呼び出されます。プラグが`Plug.Conn.halt/1`を呼び出すと(デフォルトでコントローラーにインポートされます)、パイプラインが停止し、アクションは呼び出されません。

```elixir
defmodule MyAppWeb.UserController do
  use MyAppWeb, :controller

  plug :authenticate, usernames: ["jose", "eric", "sonny"]

  def show(conn, params) do
    # authenticated users only
  end

  defp authenticate(conn, options) do
    if get_session(conn, :username) in options[:usernames] do
      conn
    else
      conn |> redirect(to: "/") |> halt()
    end
  end
end
```

[Overriding action/2 for custom arguments](https://hexdocs.pm/phoenix/Phoenix.Controller.html#module-overriding-action-2-for-custom-arguments)

> Phoenixaction/2は、ルーターから一致した関数を呼び出すプラグをコントローラーに挿入します。デフォルトでは、conn と params を渡します。場合によってaction/2は、コントローラーのプラグをオーバーライドすると、接続から繰り返し取得する必要がある引数をアクションに挿入するのに便利な方法になります。たとえばconn.assigns.current_user、接続に を保存し、コントローラーのすべてのアクションに対してユーザーにすばやくアクセスしたい場合を想像してください。

