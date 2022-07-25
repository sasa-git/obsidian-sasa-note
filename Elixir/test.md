[テスト](https://elixirschool.com/ja/lessons/testing/basics#%E3%83%A2%E3%83%83%E3%82%AF-4)

[Mox(外部 API 利用時のテスト方法)](https://hexdocs.pm/mox/Mox.html)

[Mox(Elixir school)](https://elixirschool.com/ja/lessons/testing/mox)

[Bypass(外部 API 利用時のテスト方法。でも Mox の方が使いやすそう)](https://elixirschool.com/ja/lessons/testing/bypass)

感覚としては、Bypass は HTTP レベルでモックを作り、Mox は関数レベルでモックを作るイメージ

[Behaviour と Mix.Config で切り替え可能な Stub を実装する](https://qiita.com/tuchiro/items/a13592b242009e902b20)

[`test`フォルダの下の独自のファイルで定義されたテストヘルパーがロードされていません。（そしてなぜElixirLSはtest_helper.exsの内容を無視するのですか？）](https://elixirforum.com/t/test-helpers-defined-in-their-own-files-under-the-test-folder-not-loaded-and-why-elixirls-ignores-test-helper-exs-contents/44028)

testのsupportファイルなどは`test/support/xxx.ex`のような形で入れてあげれば大丈夫

