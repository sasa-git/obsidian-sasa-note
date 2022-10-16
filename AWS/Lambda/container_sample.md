## API Gatewayを使って色々試す
HTTP APIとREST APIでのlambdaに入力されるデータの違い

HTTP APIはBase64エンコードされるため、デコードする必要がある！  
[API GatewayのHTTP APIのbodyがbase64でエンコードされている件](https://pomblue.hatenablog.com/entry/2021/06/06/221831)

HTTP API

```json
> curl "https://38r96v1ql4.execute-api.ap-northeast-1.amazonaws.com/?test=hogehoge" -X POST -d '{"message": "hello"}'

{
  "version": "2.0",
  "routeKey": "ANY /",
  "rawPath": "/",
  "rawQueryString": "test=hogehoge",
  "headers": {
      "accept": "*/*",
      "content-length": "20",
      "content-type": "application/x-www-form-urlencoded",
      "host": "38r96v1ql4.execute-api.ap-northeast-1.amazonaws.com",
      "user-agent": "curl/7.79.1",
      "x-amzn-trace-id": "Root=1-634baed9-6391a3951fdf4fb5660afdf9",
      "x-forwarded-for": "118.240.140.151",
      "x-forwarded-port": "443",
      "x-forwarded-proto": "https"
  },
  "queryStringParameters": {
      "test": "hogehoge"
  },
  "requestContext": {
      "accountId": "002558080376",
      "apiId": "38r96v1ql4",
      "domainName": "38r96v1ql4.execute-api.ap-northeast-1.amazonaws.com",
      "domainPrefix": "38r96v1ql4",
      "http": {
          "method": "POST",
          "path": "/",
          "protocol": "HTTP/1.1",
          "sourceIp": "118.240.140.151",
          "userAgent": "curl/7.79.1"
      },
      "requestId": "aFhB_h1yNjMEM0A=",
      "routeKey": "ANY /",
      "stage": "$default",
      "time": "16/Oct/2022:07:12:25 +0000",
      "timeEpoch": 1665904345332
  },
  "body": "eyJtZXNzYWdlIjogImhlbGxvIn0=",
  "isBase64Encoded": true
    }
```

REST API

```json
> curl "https://u5rextjav3.execute-api.ap-northeast-1.amazonaws.com/test-lambda-container-rest?test=hogehoge" -X POST -d '{"message": "hello"}'

      {
        "resource": "/",
        "path": "/",
        "httpMethod": "POST",
        "headers": {
            "accept": "*/*",
            "content-type": "application/x-www-form-urlencoded",
            "Host": "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com",
            "User-Agent": "curl/7.79.1",
            "X-Amzn-Trace-Id": "Root=1-634bae7d-0f5072476a8dcca147ecdaf2",
            "X-Forwarded-For": "118.240.140.151",
            "X-Forwarded-Port": "443",
            "X-Forwarded-Proto": "https"
        },
        "multiValueHeaders": {
            "accept": [
                "*/*"
            ],
            "content-type": [
                "application/x-www-form-urlencoded"
            ],
            "Host": [
                "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com"
            ],
            "User-Agent": [
                "curl/7.79.1"
            ],
            "X-Amzn-Trace-Id": [
                "Root=1-634bae7d-0f5072476a8dcca147ecdaf2"
            ],
            "X-Forwarded-For": [
                "118.240.140.151"
            ],
            "X-Forwarded-Port": [
                "443"
            ],
            "X-Forwarded-Proto": [
                "https"
            ]
        },
        "queryStringParameters": {
            "test": "hogehoge"
        },
        "multiValueQueryStringParameters": {
            "test": [
                "hogehoge"
            ]
        },
        "pathParameters": null,
        "stageVariables": null,
        "requestContext": {
            "resourceId": "stbb6f2189",
            "resourcePath": "/",
            "httpMethod": "POST",
            "extendedRequestId": "aFgzlElaNjMFpLg=",
            "requestTime": "16/Oct/2022:07:10:53 +0000",
            "path": "/test-lambda-container-rest",
            "accountId": "002558080376",
            "protocol": "HTTP/1.1",
            "stage": "test-lambda-container-rest",
            "domainPrefix": "u5rextjav3",
            "requestTimeEpoch": 1665904253180,
            "requestId": "4d715359-3ff5-4f61-bf77-b942dc0ddb76",
            "identity": {
                "cognitoIdentityPoolId": null,
                "accountId": null,
                "cognitoIdentityId": null,
                "caller": null,
                "sourceIp": "118.240.140.151",
                "principalOrgId": null,
                "accessKey": null,
                "cognitoAuthenticationType": null,
                "cognitoAuthenticationProvider": null,
                "userArn": null,
                "userAgent": "curl/7.79.1",
                "user": null
            },
            "domainName": "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com",
            "apiId": "u5rextjav3"
        },
        "body": "{\"message\": \"hello\"}",
        "isBase64Encoded": false
      }
```

Function URLを使ってみる

[Lambda 関数 URL の作成と管理](https://docs.aws.amazon.com/ja_jp/lambda/latest/dg/urls-configuration.html)

[【AWS】LambdaにHTTPSエンドポイントが実装されたので使ってみた【Golang】](https://graff-it-i.com/2022/04/09/lambda-function-urls/)

[[アップデート]LambdaがHTTPSエンドポイントから実行可能になる、AWS Lambda Function URLsの機能が追加されました！](https://dev.classmethod.jp/articles/aws-lambda-function-urls-built-in-https-endpoints/)

Postmanを使った例  
[[新機能] AWS Lambda Function URLで簡単にLambda関数を実行する](https://tech.nri-net.com/entry/lambda_url)



AWS_IAMの認証タイプで使う場合は、awscurlなどを使ってリクエストを投げる

```json
# アクセスキー・シークレットキーを指定していないときは、`.aws`にあるデフォルトのprofileを読み込む
> awscurl --service lambda --region ap-northeast-1 https://zx4rwxdw67uwnnqye6bceoxu7u0jhkxu.lambda-url.ap-northeast-1.on.aws/

{
  "version": "2.0",
  "routeKey": "$default",
  "rawPath": "/",
  "rawQueryString": "",
  "headers": {
    "x-amz-content-sha256": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",
    "x-amzn-tls-version": "TLSv1.2",
    "x-amz-date": "20221016T072130Z",
    "x-forwarded-proto": "https",
    "x-forwarded-port": "443",
    "x-forwarded-for": "240d:1a:1b8:8c00:44ce:434:1dca:c8e0",
    "accept": "application/xml",
    "x-amzn-tls-cipher-suite": "ECDHE-RSA-AES128-GCM-SHA256",
    "x-amzn-trace-id": "Root=1-634bb0fb-546940a469ee96f86e20cdf8",
    "host": "zx4rwxdw67uwnnqye6bceoxu7u0jhkxu.lambda-url.ap-northeast-1.on.aws",
    "content-type": "application/json",
    "accept-encoding": "gzip, deflate",
    "user-agent": "python-requests/2.26.0"
  },
  "requestContext": {
    "accountId": "002558080376",
    "apiId": "zx4rwxdw67uwnnqye6bceoxu7u0jhkxu",
    "authorizer": {
      "iam": {
        "accessKey": "AKIAQBGDZGV4MC23TRQQ",
        "accountId": "002558080376",
        "callerId": "002558080376",
        "cognitoIdentity": null,
        "principalOrgId": null,
        "userArn": "arn:aws:iam::002558080376:root",
        "userId": "002558080376"
      }
    },
    "domainName": "zx4rwxdw67uwnnqye6bceoxu7u0jhkxu.lambda-url.ap-northeast-1.on.aws",
    "domainPrefix": "zx4rwxdw67uwnnqye6bceoxu7u0jhkxu",
    "http": {
      "method": "GET",
      "path": "/",
      "protocol": "HTTP/1.1",
      "sourceIp": "240d:1a:1b8:8c00:44ce:434:1dca:c8e0",
      "userAgent": "python-requests/2.26.0"
    },
    "requestId": "a4fc2946-dad2-4f49-989a-6ffa34e99268",
    "routeKey": "$default",
    "stage": "$default",
    "time": "16/Oct/2022:07:21:31 +0000",
    "timeEpoch": 1665904891284
  },
  "isBase64Encoded": false
}
```

aws_lambda_powertoolsを使って得られるログ情報

lambdaのpythonコード

```python
from os.path import join, dirname
from dotenv import load_dotenv
import os
import json
from aws_lambda_powertools import Logger

dotenv_path = join(dirname(__file__), '.env')
load_dotenv(dotenv_path=dotenv_path)

logger = Logger(level='INFO', service='sample-lambda')

def handler(event, context):
  logger.info(event)

  return {
    'statusCode': 200,
    'headers': {"Content-Type": "application/json"},
    'body': json.dumps(event),
    'isBase64Encoded': False
  }

```

得られるログ情報

```json
> curl "https://u5rextjav3.execute-api.ap-northeast-1.amazonaws.com/test-lambda-container-rest?test=hogehoge" -X POST -d '{"message": "hello"}'

{
    "level": "INFO",
    "location": "handler:13",
    "message": {
        "resource": "/",
        "path": "/",
        "httpMethod": "POST",
        "headers": {
            "accept": "*/*",
            "content-type": "application/x-www-form-urlencoded",
            "Host": "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com",
            "User-Agent": "curl/7.79.1",
            "X-Amzn-Trace-Id": "Root=1-634bae7d-0f5072476a8dcca147ecdaf2",
            "X-Forwarded-For": "118.240.140.151",
            "X-Forwarded-Port": "443",
            "X-Forwarded-Proto": "https"
        },
        "multiValueHeaders": {
            "accept": [
                "*/*"
            ],
            "content-type": [
                "application/x-www-form-urlencoded"
            ],
            "Host": [
                "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com"
            ],
            "User-Agent": [
                "curl/7.79.1"
            ],
            "X-Amzn-Trace-Id": [
                "Root=1-634bae7d-0f5072476a8dcca147ecdaf2"
            ],
            "X-Forwarded-For": [
                "118.240.140.151"
            ],
            "X-Forwarded-Port": [
                "443"
            ],
            "X-Forwarded-Proto": [
                "https"
            ]
        },
        "queryStringParameters": {
            "test": "hogehoge"
        },
        "multiValueQueryStringParameters": {
            "test": [
                "hogehoge"
            ]
        },
        "pathParameters": null,
        "stageVariables": null,
        "requestContext": {
            "resourceId": "stbb6f2189",
            "resourcePath": "/",
            "httpMethod": "POST",
            "extendedRequestId": "aFgzlElaNjMFpLg=",
            "requestTime": "16/Oct/2022:07:10:53 +0000",
            "path": "/test-lambda-container-rest",
            "accountId": "002558080376",
            "protocol": "HTTP/1.1",
            "stage": "test-lambda-container-rest",
            "domainPrefix": "u5rextjav3",
            "requestTimeEpoch": 1665904253180,
            "requestId": "4d715359-3ff5-4f61-bf77-b942dc0ddb76",
            "identity": {
                "cognitoIdentityPoolId": null,
                "accountId": null,
                "cognitoIdentityId": null,
                "caller": null,
                "sourceIp": "118.240.140.151",
                "principalOrgId": null,
                "accessKey": null,
                "cognitoAuthenticationType": null,
                "cognitoAuthenticationProvider": null,
                "userArn": null,
                "userAgent": "curl/7.79.1",
                "user": null
            },
            "domainName": "u5rextjav3.execute-api.ap-northeast-1.amazonaws.com",
            "apiId": "u5rextjav3"
        },
        "body": "{\"message\": \"hello\"}",
        "isBase64Encoded": false
    },
    "timestamp": "2022-10-16 07:10:53,748+0000",
    "service": "sample-lambda",
    "xray_trace_id": "1-634bae7d-0f5072476a8dcca147ecdaf2"
}

```
