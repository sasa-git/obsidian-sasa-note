```json
{ "store": {
    "book": [ 
      { "category": "reference",
        "author": "Nigel Rees",
        "title": "Sayings of the Century",
        "price": 8.95
      },
      { "category": "fiction",
        "author": "Evelyn Waugh",
        "title": "Sword of Honour",
        "price": 12.99
      },
      { "category": "fiction",
        "author": "Herman Melville",
        "title": "Moby Dick",
        "isbn": "0-553-21311-3",
        "price": 8.99
      },
      { "category": "fiction",
        "author": "J. R. R. Tolkien",
        "title": "The Lord of the Rings",
        "isbn": "0-395-19395-8",
        "price": 22.99
      }
    ],
    "bicycle": {
      "color": "red",
      "price": 19.95
    }
  }
}
```


|XPath|JSONPath|結果|
| --- | --- | --- |
|/store/book/author|$.store.book[*].author|ストア内のすべての書籍の著者|
|//author|$..author|すべての著者|
|/store/*|$.store.*|いくつかの本と赤い自転車です。|
|/store//price|$.store..price|店内のすべての価格。|
|//book[3]|$..book[2]|3冊目|
|//book[last()]|$..book[(@.length-1)], $..book[-1:]|順番の最後の本。|
|//book[position()<3]|$..book[0,1], $..book[:2]\最初の二冊|
|//book[isbn]|$..book[?(@.isbn)]|isbn番号ですべての本をフィルタリング|
|//book[price<10]|$..book[?(@.price<10)]|10 冊より安いすべての本をフィルタリングする|
|//*|$..*|XML ドキュメント内のすべての要素。JSON 構造のすべてのメンバー。|

https://goessner.net/articles/JsonPath/ より
