[[小ネタ]AWS WAFを使って特定のURLにIP制限を設定する。](https://dev.classmethod.jp/articles/awswaf-access-deny/)

[AWS WAFV2でIPアドレス制限してみた](https://dev.classmethod.jp/articles/how-to-use-aws-waf-v2-to-filter-incoming-traffic-based-ip-address/)

[terraformで Cloudfront に WAF2 を使って特定のパスやAPIにIP制限をする](https://qiita.com/eretica/items/6e9516ea8dd8ba073347)  
`admin/` 以下のサイトをアクセス制限したいとき

```terraform
  regular_expression {
    regex_string = "^\\/?admin.*$"
  }
```

`"^\\/?admin.*$"` で、WAF上では `"^\/?admin.*$"` という扱いになるから、terraform上では`\\`で正しい

