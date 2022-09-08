[レスポンシブの実装が今までと変わる！ CSSの新機能コンテナクエリと:has()疑似クラス、最初に理解しておきたい基礎知識を解説](https://coliss.com/articles/build-websites/operation/css/container-and-has-in-chrome105.html)

Modal  
[モーダル要素の実装に便利なCSSの新機能「:modal疑似クラス」、主要ブラウザのすべてにサポートされました](https://coliss.com/articles/build-websites/operation/css/modal-css-pseudo-class.html)

```js
BUTTONS.forEach((BUTTON) => {
  BUTTON.addEventListener("click", (e) => {
    let modalStyle;
    switch (BUTTON.getAttribute("data-modal")) {
      case "true":
        modalStyle = "showModal"; // HTMLDialogElement.showModal()
        break;
      case "false":
        modalStyle = "show"; // HTMLDialogElement.show()
        break;
      default:
        modalStyle = "close"; // HTMLDialogElement.close()
    }
    DIALOG[modalStyle](); //ここでHTMLDialogElement.[modalStyle]()が呼ばれる
  });
});
```

[HTMLDialogElement](https://developer.mozilla.org/ja/docs/Web/API/HTMLDialogElement)
