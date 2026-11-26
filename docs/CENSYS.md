# Censys 使用说明

Censys 是可选候选来源，只负责发现 IP，不负责判断最终地区。导入后的候选仍需完成本地 TCP、HTTPS、延迟和真实下载测速。

## 使用条件

- 需要可用的 Censys 账号和 Personal Access Token。
- 免费或 Starter 账号按 credits 计费，查询次数和结果数量受账号额度限制。
- 没有 Token 时不会影响 CM、GitHub、Cloudflare 官方段等其他来源。

## 配置步骤

1. 登录 Censys 并创建 Personal Access Token。
2. 打开软件「IP 来源 → Censys」。
3. 粘贴 Token 并保存。
4. 选择本次获取数量，建议先用较小数量确认账号权限和额度。
5. 点击获取，完成后到「总览」执行真实优选。

## 常见问题

| 提示 | 处理 |
| --- | --- |
| 401 / 403 | Token 无效、已过期或账号没有相应权限 |
| 402 | 账号 credits 不足 |
| 429 | 请求过于频繁，稍后重试 |
| 获取成功但结果为空 | 检查查询条件、端口和账号可用额度 |

Token 保存在 Windows 凭据管理器中。请勿把 Token 发到聊天、截图、Issue 或公开仓库。
