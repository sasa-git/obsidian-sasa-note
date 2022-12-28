[Pythonのast.literal_eval()で文字列をリストや辞書に変換](https://note.nkmk.me/python-ast-literal-eval/)

[Pythonで辞書のキー・値の存在を確認、取得（検索）](https://note.nkmk.me/python-dict-in-values-items/)

[【python】辞書(dict)をコピーする方法【参照渡し、値渡し、キーと値コピー】](https://python-academia.com/dict-copy/)

[Pythonでリスト（配列）の要素を削除するclear, pop, remove, del](https://note.nkmk.me/python-list-clear-pop-remove-del/)

[Pythonのfilter()でリストから条件を満たす要素を抽出・削除](https://note.nkmk.me/python-filter-usage/)

[[Python] for文処理が1行で書ける！素敵なリスト内包表記](https://www.yoheim.net/blog.php?q=20150702)

[Pythonのmap()でリストの要素に関数・処理を適用](https://note.nkmk.me/python-map-usage/)

[2つの辞書をマージする](https://www.python.ambitious-engineer.com/archives/1763)

```python
dict1 = {"a":1, "b":2}
dict2 = {"c":3, "d":4}
 
dict1.update(dict2) # dict1にdict2をマージする
print(dict1)
# {'a': 1, 'b': 2, 'c': 3, 'd': 4}

dict1 = {"a":1, "b":2}
dict2 = {"c":3, "d":4}
dict3 = dict(dict1, **dict2) # 第２引数はキーワード引数とする
print(dict3)
# {'b': 2, 'a': 1, 'd': 4, 'c': 3}
```


[Pythonの辞書（dict）のforループ処理（keys, values, items）](https://note.nkmk.me/python-dict-keys-values-items/)  
> 各要素のキーkeyと値valueの両方に対してforループ処理を行いたい場合は、items()メソッドを使う。

