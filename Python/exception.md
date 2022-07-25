[Pythonの例外をサクサク理解しよう](https://atmarkit.itmedia.co.jp/ait/articles/1701/13/news028_3.html)

> このコードでは「as e」として変数eに例外オブジェクトを取得している。例外オブジェクトのメンバ「args」には通常、エラーメッセージが格納されている。そのため「e.args」とすればエラーメッセージにアクセスできるが、単に「e」とするだけでもこれを取得できるように準備されている。その違いが分かるように、3つのexcept節にある関数print呼び出しではそれぞれ「e」のみ、「e.args」のみ、その両方を出力するようにしてある。実行結果は次のようになる。

```py
>>> for item in ['1/0', 'hoge + 2', '1 + str(100)']:
...   try:
...     print(eval(item))
...   except ZeroDivisionError as e:
...     print('devision by zero:', e)
...   except NameError as e:
...     print('undefined name:', e.args)
...   except TypeError as e:
...     print('incompatible types:', e, e.args)
...
devision by zero: division by zero
undefined name: ("name 'hoge' is not defined",)
incompatible types: unsupported operand type(s) for +: 'int' and 'str'
   ("unsupported operand type(s) for +: 'int' and 'str'",)
```

[【Python】エラー発生時にプログラムを止めないで続ける方法：例外処理（try、except）](https://office54.net/python/basic/exception-try-except)

