[Post with JSON data](https://github.com/locustio/locust/issues/157)

```
payload = {'some':'payload'}
headers = {'content-type': 'application/json'}
r = l.client.post("/post/endpoint", data=json.dumps(payload), headers=headers, catch_response=True)
```

https://docs.locust.io/en/stable/api.html#locust.clients.HttpSession.post

https://docs.locust.io/en/latest/api.html#httpsession-class

Webリクエストを実行し、リクエスト間で（セッション）Cookieを保持するためのクラス（Webサイトにログインおよびログアウトできるようにするため）。イナゴが統計を表示できるように、各リクエストはログに記録されます。

これはpython-requestの requests.Sessionクラスのわずかに拡張されたバージョンであり、ほとんどの場合、このクラスはまったく同じように機能します。ただし、リクエストを行うためのメソッド（get、post、delete、put、head、options、patch、request）は、URLのパス部分のみであるurl引数を取ることができるようになりました。

[GitHub](https://github.com/locustio/locust/blob/master/locust/clients.py#L26)

[Python, RequestsでWeb APIを呼び出し（データ取得・操作）](https://note.nkmk.me/python-requests-web-api/)

post()の引数jsonはRequestsのバージョン2.4.2から追加された。jsonに指定することで辞書が自動的に文字列に変換され、リクエストヘッダのContent-Typeもapplication/jsonに変更される。

引数dataを使う場合は、標準ライブラリのjsonモジュールをインポートした上でjson.dumps(item_data)で辞書を文字列に変換して指定する（data=json.dumps(item_data)）。この場合、リクエストヘッダheadersのContent-Typeをapplication/jsonに指定しておく必要がある。