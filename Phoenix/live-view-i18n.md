assign()時に@localeの変更を検知して再レンダリングが行われる

assign()で入れたキーバリューはsocket.assignsで参照できる。renderは更新されたsocket.assignsを受け取り、変更箇所を再レンダリングして返す→これで英語-日本語の切り替えができる
`The render/1 callback receives the socket.assigns and is responsible for returning rendered content. `

render()内にlocale: @locale を入れておくことで_footer.html 自体が再レンダリングされるため、芋づる式に_footer 内のgettext()も更新される

https://elixirforum.com/t/how-to-force-reevaluation-of-eex-tags-in-live-view-for-live-updating-gettext/32881

[Using Gettext for internationalization](https://hexdocs.pm/phoenix_live_view/using-gettext.html)
