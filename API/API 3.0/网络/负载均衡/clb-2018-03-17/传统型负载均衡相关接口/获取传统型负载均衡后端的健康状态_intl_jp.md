## 1. API説明

APIリクエストドメイン名：clb.tencentcloudapi.com。

DescribeClassicalLBHealthStatusは、従来型CLBバックエンドの正常性状態を取得するために使用されます。

デフォルトのAPIリクエスト頻度制限：20回/秒。

注意：このAPIは金融区地域をサポートします。金融区と非金融区は分離されており、相互通信できないため、共通パラメータRegionが金融区地域（例えば、ap-shanghai-fsi）の場合は、金融区地域のドメイン名を同時に指定する必要があります。Region地域と一致するようにするのは一番です。例：clb.ap-shanghai-fsi.tencentcloudapi.com。



## 2. 入力パラメータ

次のリクエストパラメータリストには、APIリクエストパラメータと一部の共通パラメータのみがリストされています。完全な共通パラメータのリストについては、[共通リクエストパラメータ](/document/api/214/30670)を参照してください。

| パラメータ名 | 必須項目 | タイプ | 説明 |
|---------|---------|---------|---------|
| Action | はい | String | 共通パラメータ、このAPIの値：DescribeClassicalLBHealthStatus |
| Version | はい | String | 共通パラメータ、このAPIの値：2018-03-17 |
| Region | はい | String | 共通パラメータ、詳細については、製品がサポートする[地域リスト](/document/api/214/30670#.E5.9C.B0.E5.9F.9F.E5.88.97.E8.A1.A8)を参照してください。 |
| LoadBalancerId | はい | String | ロードバランサーインスタンスID |
| ListenerId | いいえ | String | CLBリスナーID |

## 3. 出力パラメータ

| パラメータ名 | タイプ | 説明 |
|---------|---------|---------|
| HealthList | Array of [ClassicalHealth](/document/api/214/30694#ClassicalHealth) | バックエンドの正常性リスト<br/>注意：このフィールドはnullを返す可能性があり、有効値を取得できないことを表します。|
| RequestId | String | 唯一のリクエストID、リクエストごとに返します。問題を特定するときに、このリクエストのRequestIdが必要です。|

## 4. 例

### 例1 従来型CLBのRSの正常性情報の取得

#### 入力例

```
https://clb.tencentcloudapi.com/?Action=DescribeClassicalLBHealthStatus
&LoadBalancerId=lb-a3u5l5zc
&<共通リクエストパラメータ>
```

#####　出力例

```
{
    "Response": {
        "HealthList": [
            {
                "IP": "10.142.9.250",
                "Port": 1111,
                "ListenerPort": 111,
                "Protocol": "TCP",
                "HealthStatus": 0
            },
            {
                "IP": "10.104.63.53",
                "Port": 1111,
                "ListenerPort": 111,
                "Protocol": "TCP",
                "HealthStatus": 0
            },
            {
                "IP": "10.104.126.68",
                "Port": 1111,
                "ListenerPort": 111,
                "Protocol": "TCP",
                "HealthStatus": 0
            },
            {
                "IP": "10.142.9.250",
                "Port": 12312,
                "ListenerPort": 1213,
                "Protocol": "UDP",
                "HealthStatus": 1
            },
            {
                "IP": "10.104.126.68",
                "Port": 12312,
                "ListenerPort": 1213,
                "Protocol": "UDP",
                "HealthStatus": 1
            },
            {
                "IP": "10.104.63.53",
                "Port": 12312,
                "ListenerPort": 1213,
                "Protocol": "UDP",
                "HealthStatus": 1
            }
        ],
        "RequestId": "b18d94ba-94fa-4c59-b66c-840d11a6a0f3"
    }
}
```


## 5. 開発者リソース

### API Explorer

**このツールはオンライン呼び出し、署名の検証、SDKコード生成と高速検索APIなどの機能を提供し、クラウドAPI使用の難易度を大幅に低減することができるため、お勧めします。**

* [API 3.0 Explorer](https://console.cloud.tencent.com/api/explorer?Product=clb&Version=2018-03-17&Action=DescribeClassicalLBHealthStatus)

### SDK

クラウドAPI 3.0は、API呼び出しを容易にするために複数のプログラミング言語をサポートする、関連開発ツールセット（SDK）を提供します。

* [Tencent Cloud SDK 3.0 for Python](https://github.com/TencentCloud/tencentcloud-sdk-python)
* [Tencent Cloud SDK 3.0 for Java](https://github.com/TencentCloud/tencentcloud-sdk-java)
* [Tencent Cloud SDK 3.0 for PHP](https://github.com/TencentCloud/tencentcloud-sdk-php)
* [Tencent Cloud SDK 3.0 for Go](https://github.com/TencentCloud/tencentcloud-sdk-go)
* [Tencent Cloud SDK 3.0 for NodeJS](https://github.com/TencentCloud/tencentcloud-sdk-nodejs)
* [Tencent Cloud SDK 3.0 for .NET](https://github.com/TencentCloud/tencentcloud-sdk-dotnet)

### TCCLI

* [Tencent Cloud CLI 3.0](https://cloud.tencent.com/document/product/440/6176)

## 6. エラーコード

以下に、APIビジネスロジックに関連するエラーコードのみをリストします。その他のエラーコードについては、[共通エラーコード](/document/api/214/30673#.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81)を参照してください。

| エラーコード | 説明 |
|---------|---------|
| FailedOperation | 操作失敗 |
| InternalError | 内部エラー |
| InvalidParameter | パラメータエラー。 |
| InvalidParameterValue | パラメータ値エラー |
| LimitExceeded | 割り当て量の制限を超えました |
| ResourceInsufficient | リソースが足りません |
| UnauthorizedOperation | 操作が承認されていません |

