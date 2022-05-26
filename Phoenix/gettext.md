> 上記のように、（関数ではなく）Gettextマクロを使用すると、Gettextはコンパイル時にこれらの変換を操作できます。これを使用して、ソースコードからPOTファイルに翻訳を自動的に抽出できます（ソースコードに追加されたときにPOTファイルに翻訳を手動で追加する必要はありません）。これgettext.extractはまさにこれを行います。ソースコードに新しい翻訳がある場合は常に、runninggettext.extractは既存のPOTファイルを変更されたコードベースと同期します。Mix.Tasks.Gettext.Extract抽出プロセスの詳細については、ドキュメントをお読みください 。
> 
> POTファイルは単なるテンプレートファイルであり、その中の翻訳には実際には翻訳された文字列は含まれていません。POTファイルは次のようになります。
[コンパイル時の機能](https://hexdocs.pm/gettext/Gettext.html#module-compile-time-features)

[Phoenixで多言語化(i18n)](https://qiita.com/shufo/items/8ba11c065edc4ad1229e)

[Translating Phoenix Applications with GNU gettext](https://phrase.com/blog/posts/i18n-for-phoenix-applications-with-gettext/)

[Elixir で Gettext を使う](https://blog.emattsan.org/entry/2018/02/27/214329)

[I18n With Phoenix](https://www.wbotelhos.com/i18n-with-phoenix)

