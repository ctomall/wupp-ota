# wupp-ota

Wupp 中文版（`com.wupp.zh`）的公网 OTA 更新源。

## 目录内容

每次发布在该仓库创建 GitHub Release，并上传 5 个资产：

| 资产 | 说明 |
| --- | --- |
| `Wupp-<ver>-arm64-v8a.apk` | 64 位安装包 |
| `Wupp-<ver>-universal.apk` | 全架构安装包 |
| `manifest.json` | 更新清单（版本、产物、SHA-256） |
| `manifest.sig.b64` | 清单的 ECDSA P-256 签名（base64 DER） |
| `SHA256SUMS.txt` | 产物校验和 |

客户端内置公钥校验 `manifest.sig.b64`，验签失败一律视为「没有更新」。

## 客户端如何取

清单地址：

```
https://github.com/ctomall/wupp-ota/releases/latest/download/manifest.json
```

签名走同目录的 `manifest.sig.b64`（客户端自动拼接），或用 `?sig=<urlencoded>` 显式指定。

## 发布流程

见主仓库 `ota/build-release.ps1` 与 `ota/publish-ota.yml`。
