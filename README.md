# MoleAPI - LazyCat App

[MoleAPI](https://github.com/ca-x/moleapi)（自托管 API 工作台：请求调试、脚本数据集、OAuth 调试，配套离线 Tauri 桌面客户端）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/ca-x/moleapi` 经 `ghcr.nju.edu.cn` 加速拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：每日检查上游 semver tag，发现新版本自动构建发布。
- **双商店发布**：私有商店（MiaoMiao）+ 官方商店（审核 1-3 个工作日）。

## 说明

- 单容器（Rust + 内嵌 Web，端口 8787），数据卷 `/lzcapp/var/moleapi:/data`（默认 SQLite）
- **首次使用**：首个账号通过 setup token 注册（token 在容器日志输出）；之后是否开放自助注册由部署参数控制（默认关闭）
- 内网 API 调试需在部署参数开启"允许内网调试"（`MOLEAPI_ALLOW_PRIVATE_NETWORK`）
- 数据库可切换 PostgreSQL/MySQL（`MOLEAPI_DATABASE_URL`，默认 SQLite 即可）
- 健康检查 `/`

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
