[フォームの自動補完を無効にするには](https://developer.mozilla.org/ja/docs/Web/Security/Securing_your_site/Turning_off_form_autocompletion#The_autocomplete_attribute_and_login_fields)

`<input>`に`autocomplete="new-password"` を設定すると自動入力を停止する

> 現代的なブラウザーでは、パスワードを一括管理する機能が実装されています。ユーザーがウェブサイトでユーザー名とパスワードを入力した際、ブラウザーはその値を記> 憶するかユーザーに尋ねます。ユーザーがそのウェブサイトを再び訪れた際には、ログイン欄がブラウザーに保存された値で自動入力されます。
> 
> 加えて、ユーザーがマスターパスワードを設定すると、ログイン情報をマスターパスワードで暗号化した状態でブラウザーに保存することができます。
> 
> マスターパスワードが用いられない場合でも、ブラウザーのパスワード管理機能は純粋にセキュリティの向上につながります。パスワードをブラウザーが保存すればユーザ> ーは覚えなくてもよいため、覚えなければならない場合よりも強固なパスワードをユーザーが設定できるようになります。
> 
> このような理由から、現代的なブラウザーの多くはログイン欄における autocomplete="off" に対応していません。

[フッターをページの最下部に固定](https://qiita.com/d0ne1s/items/5c629bc543e70ed2bf98)

基本的にはflex使った方が楽

```html
<body>
  <header>ヘッダー</header>
  <main>コンテンツ</main>
  <footer>フッター</footer>
</body>
```

```css
body {
  display: flex;
  flex-flow: column;
  min-height: 100vh; /* ←これがミソ */
}
main {
  flex: 1;
}
```

[CSS Tooltip](https://www.w3schools.com/css/css_tooltip.asp#gsc.tab=0)

[How TO - CSS/JS Modal](https://www.w3schools.com/howto/howto_css_modals.asp)