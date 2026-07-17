# OpenCodex LAN Codex Guide

> Share one OpenCodex instance with Codex on another trusted LAN computer.

[中文说明](#中文) | [English](#english)

```mermaid
flowchart LR
    B["Computer B<br/>Codex"] -->|"LAN request + API token"| A["Computer A<br/>OpenCodex"]
    A --> O["OpenAI / Codex account"]
    A --> X["xAI / Grok"]
    A --> N["NVIDIA / Other providers"]
```

## 快速使用：把下面两段分别发给 A、B 电脑上的 Codex

先将 `<A_HOST_IP>` 替换为 A 电脑的局域网 IP，将 `<YOUR_API_TOKEN>` 替换为你自行生成的长随机 token。两台电脑的 token 必须完全一致，且只应在可信局域网内使用。

### A 电脑：部署 OpenCodex 服务端

```text
请直接执行：在这台 Windows 电脑上把 OpenCodex 配置为局域网服务端。将其监听地址设置为 0.0.0.0、固定端口设置为 10100，设置用户环境变量 OPENCODEX_API_AUTH_TOKEN=<YOUR_API_TOKEN>，创建 Windows 防火墙入站规则放行 TCP 10100，然后重启 OpenCodex。最后验证 http://127.0.0.1:10100/healthz 返回成功，并告诉我这台电脑的局域网 IPv4 地址。不要把 token 写入任何公开文件，也不要将 10100 端口暴露到公网。
```

### B 电脑：连接 A 电脑的 OpenCodex

```text
请直接执行：把这台 Windows 电脑上的 Codex 配置为通过局域网连接 A 电脑的 OpenCodex。设置用户环境变量 OPENCODEX_API_AUTH_TOKEN=<YOUR_API_TOKEN>；检查并修改 Codex 的 config.toml，删除任何根级 openai_base_url 配置，设置 model_provider = "opencodex"，添加或更新 [model_providers.opencodex]：base_url = "http://<A_HOST_IP>:10100/v1"、wire_api = "responses"、requires_openai_auth = true、env_http_headers = { "x-opencodex-api-key" = "OPENCODEX_API_AUTH_TOKEN" }。保留或补齐可用的 model_catalog_json，重启 Codex，并验证 http://<A_HOST_IP>:10100/api/providers 返回 200。不要把 token 写入公开文件。
```

## 中文

这个仓库说明如何让 A 电脑运行 `opencodex`，并让同一局域网内的 B 电脑上的 `Codex` 将模型请求转发到 A 电脑。B 电脑仍使用自己的 Codex 客户端，但可以复用 A 电脑已经接入的模型和 Provider。

适合以下场景：

- A 电脑负责运行和维护 `opencodex`。
- B 电脑只安装并登录 `Codex`，无需再部署一套 OpenCodex 服务。
- 两台设备位于同一个可信局域网。

完整安装、Windows 防火墙、Token 配置、模型目录同步、验证与排障，请阅读：[完整中文教程](./LAN-CODEX-TUTORIAL.md)

### 安全提示

- 仅在自己信任的局域网中开放服务。
- API Token 相当于访问凭证，不要截图、不要提交到 Git，也不要发送给不可信的人。
- 不要将服务端口直接暴露到公网；如需远程使用，请先做好访问控制与加密。

## English

This repository explains how to run `opencodex` on Computer A and route Codex requests from Computer B through that trusted local-network server. Computer B still uses its own Codex client, while requests can use the models and providers configured on Computer A.

This guide is intended for a trusted LAN where:

- Computer A runs and maintains `opencodex`.
- Computer B runs and signs in to `Codex`; it does not need another OpenCodex service.
- Both computers can reach each other on the same local network.

For the full setup, Windows Firewall rules, token configuration, model catalog sync, verification, and troubleshooting, see the [full Chinese guide](./LAN-CODEX-TUTORIAL.md).

### Security note

- Share the service only on a LAN you trust.
- Treat the API token as a credential. Never commit or share it publicly.
- Do not expose the service port directly to the public internet without proper access control and encryption.

## Acknowledgement

This guide is built around [lidge-jun/opencodex](https://github.com/lidge-jun/opencodex). Thanks to the original project and its maintainers.

## License

This repository contains documentation only. Please follow the upstream project's license and terms when using OpenCodex.
