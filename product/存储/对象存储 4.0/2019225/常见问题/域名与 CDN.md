### COS 文件更新（重新上传或删除）时，CDN 仍然保存缓存内容，造成与源站不一致。能否在 COS 更新时自动刷新 CDN 的缓存？

COS 本身不支持自动刷新 CDN 缓存，您可以联合无服务器云函数 SCF 来设置自动刷新 CDN 缓存，详情请参阅 [使用 SCF 自动刷新被 CDN 缓存的 COS 资源 ](https://cloud.tencent.com/document/product/436/30434) 文档。

### 在控制台进行域名管理时，总是提示“请至少启用一个可用密钥”该如何处理？

请登录 [访问管理控制台](https://console.cloud.tencent.com/cam/capi) 查看是否已启用云 API 密钥。

- 若未启用云 API 密钥，请创建密钥并启用后再进行域名管理。
- 若已启用云 API 密钥仍有提示，请确认您当前操作的账号是否为子账号（协作者或子用户）：
  - 若为子账号，请登录主账号确认已启用云 API 密钥；
  - 若为主账号，请刷新浏览器缓存，重新登录腾讯云账号。

### 如何使用自有域名访问对象？

可通过绑定自定义域名实现。详情请参阅 [自定义加速域名](https://cloud.tencent.com/document/product/436/18424#.E8.87.AA.E5.AE.9A.E4.B9.89.E5.8A.A0.E9.80.9F.E5.9F.9F.E5.90.8D)。

### COS 是否支持 HTTPS 访问？

支持。COS 在所有 [可用地域](https://cloud.tencent.com/document/product/436/6224) 的访问节点都提供了 SSL 传输的支持，且在 SDK 和控制台都默认启用 HTTPS。**COS 强烈建议您使用 HTTPS 保护传输的数据链路，使用不加密的 HTTP 连接将可能面临链路被监听或数据被窃取的风险。**

### COS 是否支持 CDN HTTPS 回源 COS？

支持。

### 使用自定义域名需要先备案？

是的。目前接入 COS 的域名都需要备案，不论国内还是海外。

### 如何对 COS 中的文件生成一个临时 URL？

具体操作请参阅 [预签名授权下载](https://cloud.tencent.com/document/product/436/14116)。

### 私有读存储桶能否通过 CDN 加速访问？

可以，但是需要进行授权相关配置。具体配置请参阅 CDN 加速概述文档的 [私有读存储桶](https://cloud.tencent.com/document/product/436/18669#.E7.A7.81.E6.9C.89.E8.AF.BB.E5.AD.98.E5.82.A8.E6.A1.B6) 部分。

### 为何在 CDN 控制台变更源站后，COS 控制台里的原自定义域名就消失了？
>!一旦您使用了 v5 版本控制台，并带有 v4 域名配置，COS 的 v5 控制台则无法显示新域名。

请检查您的存储桶中是否配置了 v4 版本域名（JSON 域名），请将 v4 版本域名配置修改为 v5 版本域名（XML 域名）。


