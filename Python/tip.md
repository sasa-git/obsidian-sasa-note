[Python の ast モジュール入門 (抽象構文木を辿る)](https://qiita.com/t2y/items/0964d01bf3db0233e3c1)

[[Locust/request.md]]

[Python で Faker を使ってダミーデータを作成する](https://qiita.com/yunosuken/items/5835b6ba26981c56eeda)

[Pythonでクラス変数とインスタンス変数を取り違えてハマった](https://qiita.com/7shi/items/d37493c58a8bb8d7beed)  
> インスタンス変数はコンストラクタで初期化しましょう。

[Pythonではインスタンス変数をクラス定義直下に書いてはいけない(戒め)](https://qiita.com/kxphotographer/items/60588b7c747094eba9f1)

[rand_str 関数を実装する](https://maku77.github.io/python/numstr/random-string.html)

```py
import random

def rand_str(length):
    chars = '23456789abcdefghijkmnopqrstuvwxzy'
    return ''.join([random.choice(chars) for _ in range(length)])

if __name__ == '__main__':
    print(rand_str(7))
```

[Python で kubernetes を操作する超入門](https://hawksnowlog.blogspot.com/2021/03/getting-started-with-python-kubernetes-api.html#redis-%E3%81%AE-service-%E3%82%92%E4%BD%9C%E6%88%90%E3%81%99%E3%82%8B)

[Pythonのos.getenvとos.environ.getの違い](https://qiita.com/1ntegrale9/items/94ec4437f763aa623965)

[[python]print文で色をつけてみよう](https://www.nomuramath.com/kv8wr0mp/)

[python: getattr](https://qiita.com/nabenabe0928/items/255b571c62c1b1d69ad4)

[Pythonでパケットキャプチャ(pcapy)](https://rawgit.com/CoreSecurity/pcapy/master/pcapy.html#idp1073151854112)

[【Python】subprocessのよく使う奴だけまとめたサンプルコード集](https://www.mathkuro.com/python/subprocess-popular-usage/)

[真理値判定](https://docs.python.org/ja/3/library/stdtypes.html?highlight=dict)

> 主な組み込みオブジェクトで偽と判定されるものを次に示します:
> 
> 偽であると定義されている定数: None と False
> 
> 数値型におけるゼロ: 0, 0.0, 0j, Decimal(0), Fraction(0, 1)
> 
> 空のシーケンスまたはコレクション: '', (), [], {}, set(), range(0)

[Pythonのf文字列（フォーマット済み文字列リテラル）の使い方](https://note.nkmk.me/python-f-strings/)
> 文字列メソッドformat()と同様に、f文字列中に波括弧{}を記述したい場合は{{, }}のように2回続けて書く。

