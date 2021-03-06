﻿##　操作シナリオ
本項では、TencentDB for Redis のコンソールでインスタンスの全データを消去するプロセスについて説明します。
>!
>- インスタンスを消去した後、データをリカバリすることはできません。必ずデータをバックアップしてから消去してください。
>- データ消去の操作は、インスタンスが外部に提供するサービスに影響を与えます。また、消去操作中は、インスタンスにアクセスすることができません。ご注意ください。


## 操作手順

1. [Redis コンソール](https://console.cloud.tencent.com/redis)にログインし、インスタンスリストでインスタンス名をクリックしてインスタンスの詳細ページに移動します。
2. インスタンス詳細のページで【インスタンスの消去】をクリックします。
![](https://main.qcloudimg.com/raw/9b025e0cd830dfe053bfece421b34792.png)
3. インスタンス消去のページでインスタンスのパスワードを入力し、【OK】をクリックします。
 >!ここで入力するパスワードは、インスタンスにアクセスする際に使用する「インスタンス ID：インスタンスパスワード」の接続パスワードではなく、ユーザーが設定したインスタンスのパスワードです。
4. タスクを送信すると、インスタンスのステータスが【消去中】と表示されます。消去タスクの完了後、インスタンスのステータスが【実行中】と表示されたら正常に使用できます。


	
