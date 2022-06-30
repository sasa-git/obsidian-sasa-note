[Python の Lambda 関数ハンドラー](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/python-handler.html)


bodyの値には、dictではなくstringにしておく必要がある！
```python
import os
import json
        
def lambda_handler(event, context):
    json_region = os.environ['AWS_REGION']
    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "application/json"
        },
        "body": json.dumps({
            "Region ": json_region
        })
    }
```