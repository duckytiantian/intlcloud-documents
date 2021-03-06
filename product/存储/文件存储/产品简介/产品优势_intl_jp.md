### CFSの使用利点

#### 統合管理

- CFSはPOSIXとファイルシステムアクセスセマンティクス（例えば、データ厳密一貫性とファイルロック）を提供できます。Tencent Cloud CVMインスタンスは標準OSでコマンドをマウントし、NFS v3.0/v4.0プロトコルを通じてCFSファイルストレージをマウントできます。
- CFSはコンソール画面を提供することにより、ファイルシステムを容易に作成、構成し、ファイルシステムの配置と保守などの複雑な作業を軽減できます。

#### 自動拡張

- CFSはファイル容量の大きさによってファイルシステムのストレージ容量を自動的に拡張し、また、リクエストとアプリケーションを中止しません。専有にストレージリソースを確保しながら、管理の手間を軽減します。


#### 安全、信頼できる

- CFSは非常に高い可用性と信頼性があり、各CFSインスタンスはAvailability Zoneに複数の冗長があります。
- CFSはPOSIX権限によりファイルシステムへのアクセスを厳密にコントロールし、基本ネットワークまたはVPCネットワークを使用するときに権限グループに合わせてアクセス権限のコントロールを実現できます。

#### コストが低い

- CFSは需要容量を動的調整でき、ストレージを事前に調整、構成する必要がありません。最低消費または前期配置、後期保守費用がなく、使用量だけで料金を支払います。
- 複数のCVMはNFSプロトコルを通じて同一ストレージスペースを共有できます。別のストレージサービスの重複購入、キャッシュ検討の必要がありません。


### CFSとクラウドディスクの適用シナリオの区別

種別 | ファイルストレージCFS | クラウドディスク
------- | ------- | -------
スループットレベル | 単一クライアント100MB/s（上限1.5GB/s） | 上限600MB/s
共有性 | Yes  | No
冗長 | 3部 | 3部
使用方式 | マウント後そのまま使用 | ファイルシステムのインストールが必要


### CFSとCVMでのNAS構築との総保有コスト（TCO）の比較

種別 | ファイルストレージCFS | CVMでのNAS構築
------- | ------- | -------
使用ストレージ容量 | 1 TB | 1 TB
ストレージ容量の全部購入 | 1 TB | 2 TB（85%のディスク利用率を考慮して、1205 GBの高性能クラウドディスク2枚をマスタースレーブとして購入する
使用ストレージ容量 | 1 TB | 1 TB
ストレージリソースコスト（1年） | 7127（従量制課金0.58元/GB/月） | 4300（年額/月額0.35元/GB/月）
リソースコストの計算（1年） | 0元（ファイルサーバー構築不要、マウントして使用できる） | 23744元（CVMインスタンス2台をマスタースレーブとして使用し、仕様はシリーズ1-標準型-8コア-32 GBメモリ）
総保有コスト（1年） | 7004 | 28044
月ごとの1 GBあたりのコスト | 0.58 | 2.28





