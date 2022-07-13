[terraform import したものを取り消したい](https://qiita.com/yyoshiki41/items/57ad95846fa36b3fc4a6)  

```sh
# 既存のresourceをインポート
$ terraform import aws_iam_user.foo foo
# やっぱり取り消したい
$ terraform state rm aws_iam_user.foo
```

[Terraformなら簡単に全AWSリソースに共通タグを設定できます](https://dev.classmethod.jp/articles/terraform-aws-provider-default-tags/)

```terraform
provider "aws" {
  region = "ap-northeast-1"
  default_tags {
    tags = {
      env = "dev"
    }
  }
}
```