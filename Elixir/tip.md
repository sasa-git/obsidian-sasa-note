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

