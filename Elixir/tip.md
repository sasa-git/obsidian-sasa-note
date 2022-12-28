[【Elixir】if や case の中で代入・束縛を行うべきでない](https://snamiki1212.com/elixir-not-to-bind-in-block)

[Elixir convert struct to map](https://stackoverflow.com/questions/36512627/elixir-convert-struct-to-map)  

```elixir
defmodule User do
  defstruct [:name]
end

Map.from_struct(%User{name: "valim"})
#=> %{name: "valim"}
```

[Elixir マップの値を更新する方法３選](https://thr3a.hatenablog.com/entry/20210103/1609636577)

[Elixir - do nothing under particular case condition](https://stackoverflow.com/questions/43647101/elixir-do-nothing-under-particular-case-condition)

[文字列testとかで使えそうな関数](https://elixirschool.com/ja/lessons/basics/strings#duplicate-6)  

```elixir
iex> String.duplicate("*", 12)
"************"
```

[内報表記のフィルターと:intoオプション](https://elixirschool.com/ja/lessons/basics/comprehensions#%E3%83%95%E3%82%A3%E3%83%AB%E3%82%BF-1)

> フィルタは内包表記のためのある種のガードと考えることができます。フィルタされた値が false か nil を返す場合には、最終的なリストから取り除かれます。ある範囲をループし偶数のみ気にすることにしましょう。値が偶数かどうかはIntegerモジュールの is_even/1 を用います。

```
iex> import Integer
iex> for x <- 1..100,
  is_even(x),
  rem(x, 3) == 0, do: x
[6, 12, 18, 24, 30, 36, 42, 48, 54, 60, 66, 72, 78, 84, 90, 96]
```

> リストではなく、他のものを生成したい場合はどうすれば良いでしょうか。 :into オプションを使えば可能です！ 一般的な目安として、 :into は Collectable プロトコルを実装している構造体を指定できます。

```elixir
iex> for {k, v} <- [one: 1, two: 2, three: 3], into: %{}, do: {k, v}
%{one: 1, three: 3, two: 2}

iex> for c <- [72, 101, 108, 108, 111], into: "", do: <<c>>
"Hello"
```

[credoを使ってElixirでRuboCopみたいにlintチェックをしよう！](https://qiita.com/letusfly85/items/cf225814608251b2f65c)

[Config](https://hexdocs.pm/elixir/1.13/Config.html#import_config/1)

[Elixirのコードレビューで出るやつ](https://dev.to/seizans/elixir-4djj)

[Elixir Best Practices - Deeply Nested Maps](https://dockyard.com/blog/2016/02/01/elixir-best-practices-deeply-nested-maps)

[PhoenixのLogger](https://ymmtmsys.hatenablog.com/entry/2015/08/15/151841)

[【Elixir/Phoenix】paramsライブラリでリクエストパラメータのバリデーションとキャストを楽ちんに行う](https://qiita.com/shkomine/items/98bb5c401e4267f43571)

[ElixirでBehaviourを使用してDIPを実現する基礎知識](https://sanposhiho.com/posts/elixir-behaviour/)

