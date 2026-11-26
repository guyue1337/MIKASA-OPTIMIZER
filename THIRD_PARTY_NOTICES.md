# 第三方组件与参考资料

## 运行时依赖

| 组件 | 用途 | 许可证 |
|---|---|---|
| Tauri 2 | 桌面应用框架 | MIT / Apache-2.0 |
| Vue 3 | 前端框架 | MIT |
| Naive UI | UI 组件库 | MIT |
| ECharts | 图表 | Apache-2.0 |
| Lucide | 图标 | ISC |
| Tokio | 异步运行时 | MIT |
| Reqwest | HTTP 客户端 | MIT / Apache-2.0 |
| Rustls | TLS | MIT / Apache-2.0 / ISC |
| rusqlite | SQLite 绑定 | MIT |
| SQLite | 本地数据库 | Public Domain |
| chrono | 时间处理 | MIT / Apache-2.0 |
| keyring | Windows 凭据管理器绑定 | MIT / Apache-2.0 |

完整依赖版本和许可证文本以 `Cargo.lock`、`package-lock.json` 及各自仓库为准。发布安装包时建议保留本文件。

## 设计参考

测速流程与地区识别思路参考了以下公开项目的文档与实现思路：

- [XIU2/CloudflareSpeedTest](https://github.com/XIU2/CloudflareSpeedTest)：公开的 Cloudflare 测速工具，采用 GPL-3.0 许可证。本项目未包含、链接或复制其源代码，仅参考其公开文档中的测速阶段划分与 CF 特性说明。
- [PoemMisty/CFData-WEB](https://github.com/PoemMisty/CFData-WEB)：公开的 Cloudflare 数据项目，用于了解 colo 与地区映射的常见做法。

如果后续需要直接集成上述项目的代码或二进制，必须重新核对其许可证并在发行包中附带相应许可证与版权声明。

## 图标与角色素材

左侧角色装饰图由用户提供，仅用于本项目界面。相关角色形象权利归原权利人所有；再分发或商业使用前请自行确认授权。


