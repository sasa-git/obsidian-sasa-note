wafで使うパスの指定は、`"^\\/?admin.*$"`で`"^\/?admin.*$"`と入力されるようになる

```tf
resource "aws_wafv2_regex_pattern_set" "web_admin" {
  count = local.waf_enable ? 1 : 0

  scope              = "REGIONAL"

  regular_expression {
    regex_string = "^\\/?admin.*$"
  }
}
```