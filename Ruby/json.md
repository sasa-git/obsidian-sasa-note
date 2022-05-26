https://www.sejuku.net/blog/74120
JSON.parseとは
JSON.parseとは、JSON(ジェイソン)形式の文字列をRubyのHash(ハッシュ)形式に変換するためのメソッドです。

使いかた：

```
JSON.parse(JSON文字列, オプション={})
# オプション(任意)
# :max_nesting → JSON文字列のネストの深さ。デフォルトは19
# :symbolize_names → 変換したHashのキーをシンボルにする場合はtrue
このJSON.parseは、Rails用のメソッドではなくRubyのメソッドなのでご注意ください。
```

次項では、JSON.parseの使いかたを見ていきましょう。

JSON.parseのサンプル
JSON形式の文字列をHashに変換するサンプルプログラムを紹介します。

サンプル：

```
> #JSONデータ
> json_str = '{"rails": {"json": "12345"}}'
> hash = JSON.parse(json_str)
> hash["rails"]
=> {"json"=>"12345"}
```

このようにJSONからHashに変換できました。

JSON.parseのサンプル(シンボルキー)
変換したハッシュのシンボルに変換する例もみてみましょう。

サンプル：

```
> json_str = '{"rails": {"json": "12345"}}'
> hash = JSON.parse(json_str, symbolize_names: true)
> hash[:rails]
=> {:json=>"12345"}
```

