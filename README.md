# MIKASA OPTIMIZER · 三笠优选

Windows 10/11 x64 桌面端 Cloudflare 多地区 IP 优选工具。

真实 TCP、HTTPS、colo、延迟与下载测速，支持七地区独立筛选、结果导出、
GitHub 订阅上传、历史复测与浅色/夜间主题。

> 当前版本：`v1.0.9`
> 项目性质：source-available，非商业授权，禁止商用。

## 界面预览

<p align="center">
  <img src="docs/screenshots/01-overview.png" alt="总览首页" width="32%" />
  <img src="docs/screenshots/02-sources.png" alt="IP 来源管理" width="32%" />
  <img src="docs/screenshots/03-scan.png" alt="扫描任务" width="32%" />
</p>
<p align="center">
  <img src="docs/screenshots/04-rankings.png" alt="地区排名" width="32%" />
  <img src="docs/screenshots/05-export.png" alt="结果导出" width="32%" />
  <img src="docs/screenshots/06-github.png" alt="GitHub 上传" width="32%" />
</p>
<p align="center">
  <img src="docs/screenshots/07-history.png" alt="历史记录" width="32%" />
  <img src="docs/screenshots/08-settings.png" alt="设置" width="32%" />
  <img src="docs/screenshots/09-about.png" alt="关于软件" width="32%" />
</p>

## 已实现功能

- 九页桌面界面：总览、IP 来源、扫描任务、地区排名、结果导出、GitHub 上传、历史记录、设置、关于。
- 七地区优选：香港、台湾、日本、新加坡、韩国、法国、美国；全球其他地区达标节点同样识别并展示。
- 真实测速：TCP → HTTPS/colo → 多轮延迟 → 实际下载，全部使用真实测速数据。
- 多来源导入：TXT / CSV、粘贴、URL 订阅、FOFA、Cloudflare 官方段、CM、GitHub Raw、Censys 与社区源。
- 每地区测速数量可选前 20 / 30 / 50 / 100 / 全部，兼顾速度与精度。
- 结果导出：TXT / CSV、按地区 / 速度 / 延迟筛选、每地区前 5 / 前 10 / 全部，备注字段自由组合。
- GitHub 上传：支持覆盖全部内容或追加更新 IP，自动生成 raw / jsDelivr 直链，方便脚本直接读取。
- 地区排名：真实 colo、城市、延迟、下载速度、丢包率，支持综合 / 延迟 / 速度 / 丢包排序与复测。
- 本地历史、数据备份、夜间 / 浅色主题、2K / 4K 自适应缩放、自由之翼品牌图标。

## 下载与安装

前往 [Releases](../../releases/latest) 下载：

- `MIKASA_OPTIMIZER_1.0.9_x64_setup.exe`：NSIS 安装版，安装到当前用户目录，不需要管理员权限。
- `MIKASA_OPTIMIZER_1.0.9_x64_portable.zip`：便携版，解压后双击 `三笠优选.exe`。

系统要求：

- Windows 10 x64 1809 及以上，或 Windows 11 x64
- WebView2 Runtime（安装版会自动引导）
- 首次启动和测速需要网络连接

便携版数据库位置：

```text
%APPDATA%\com.mikasa.optimizer\mikasa-optimizer.sqlite
```

## 快速开始

1. 启动软件，等待顶部显示省份与运营商；识别失败可点「重新检测」。
2. 进入「IP 来源」，导入本地 TXT、CM IP 库、Cloudflare 官方段、GitHub Raw、FOFA 或社区公开源。
3. 回到「总览」，选择地区、每地区保留数量、端口、并发、延迟上限、下载时长和测速地址。
4. 点击「开始优选」，在「扫描任务」查看 TCP、HTTPS、colo、延迟、下载与错误日志。
5. 扫描结束后进入「地区排名」查看真实结果，再到「结果导出」筛选并导出。

## 结果导出

- 选择「全部地区」时合并为一个文件；选择单个地区时只导出该地区。
- 速度筛选示例：`5 MB/s 以上`；延迟筛选示例：`500 ms 以内`。
- TXT 备注字段可以只保留城市和下载速度，也可以追加延迟、colo、来源。
- 示例行：

```text
54.250.164.93:443#三笠优选 | 日本东京 | 下载 7.86MB/s
```

- 关闭全部备注字段时只输出 `IP:端口#三笠优选`，方便客户端直接导入。

## GitHub 订阅直链

在「GitHub 上传」点击「开始上传」后，可以先选择：

- 合并全部地区：生成一个 `all.txt`
- 按地区拆分：生成 `HK/all.txt`、`JP/all.txt`、`US/all.txt` 等，并额外生成 `all.txt`
- 最低下载速度、最高延迟
- TXT 备注字段
- TXT 或 CSV

上传完成后可直接复制 raw 直链，例如：

```text
https://raw.githubusercontent.com/xxx/xxx/main/mikasa-results/all.txt
https://raw.githubusercontent.com/xxx/xxx/main/mikasa-results/JP/all.txt
```

把 `xxx/xxx` 替换成你自己的 GitHub 用户名和仓库名。

如果希望脚本匿名读取：

1. 把目标仓库改成 **Public**。
2. 确认文件在 `main` 分支。
3. 直接使用 raw 直链，或使用 jsDelivr 加速：

```text
https://cdn.jsdelivr.net/gh/xxx/xxx@main/mikasa-results/all.txt
```

私有仓库的 raw 链接需要登录或 Token，脚本无法匿名访问。公开仓库不需要 Token，
路径也不需要放在根目录，放在 `mikasa-results/` 子目录即可。

## 速度与并发说明

- 软件显示十进制 `MB/s`，`1 MB/s = 8 Mbps`。
- v2rayN 等客户端通常显示 `Mbps`，同一个节点会看到约为软件数值的 8 倍。
- 多个 IP 同时下载会争抢本机出口带宽，速度会低于客户端单连接测速。
- 设置页「下载测速并发」改为 `1` 时最接近客户端单连接结果；默认 `4` 更适合批量筛选。

## 常见问题

**某个地区没有结果？**  
Cloudflare Anycast 受本地网络、时段和线路影响，软件只展示真实测速结果。

**为什么深度测试默认是 1024 个候选？**  
候选窗口按历史成绩、地区配额和新节点探索综合选取，默认取 1024 个进行深度测试。
首次导入且没有历史成绩的 IP，无法在测速前预知绝对最优；软件不会伪造测速结果。

**GitHub 上传 401/403？**  
检查 Token 是否过期、是否具有目标仓库 Contents 读写权限，以及分支是否受保护。

## 数据与隐私

- 顶部只显示省份和运营商，不显示公网 IP、街道、坐标或城市级位置。
- FOFA、GitHub、Censys 凭据保存在 Windows 凭据管理器。
- 历史记录只保存在本机，不上传服务器。
- GitHub 上传只上传你确认的测速结果文件。

## 版权说明

本项目采用 **CC BY-NC-ND 4.0** 协议，这意味着：

- ✅ 可以下载、使用、分享，但必须注明项目名称和来源。
- ❌ 禁止商业使用。
- ❌ 禁止二次开发或修改后发布。

完整条款见 [LICENSE](LICENSE)，品牌与署名说明见 [NOTICE.md](NOTICE.md)。

## 鸣谢

感谢使用 MIKASA OPTIMIZER。

