# GitHub 上传说明

软件可以把优选结果直接上传到 GitHub，不需要在电脑上安装 Git。

## 1. 创建结果仓库

1. 在 GitHub 新建一个仓库，例如 `mikasa-results`。
2. 如果希望脚本直接读取 raw 链接，仓库需要设为 **Public**。
3. 私有仓库的 raw 链接需要登录或 Token，脚本无法匿名读取。

## 2. 创建 Token

1. 打开 GitHub「Settings → Developer settings → Personal access tokens → Fine-grained tokens」。
2. 新建 Token，并只选择目标结果仓库。
3. 为仓库内容授予 **Read and write** 权限。
4. 生成后立即复制 Token，页面关闭后不会再次显示。

请勿使用来源不明、已经泄露或过期的 Token。

## 3. 配置并上传

1. 打开软件「GitHub 上传」。
2. 填写仓库地址、分支、远程目录和 Token。
3. 点击「保存配置」，Token 会保存在 Windows 凭据管理器中。
4. 点击「检查仓库」，确认访问权限和目标分支正常。
5. 点击「开始上传」，选择上传范围、文件格式、速度和延迟条件、备注字段，以及覆盖或追加更新。
6. 上传完成后可复制 raw 直链或 jsDelivr 加速直链。

默认推荐目录结构：

```text
mikasa-results/
├─ all.txt
├─ HK/all.txt
├─ JP/all.txt
└─ US/all.txt
```

公开仓库直链示例：

```text
https://raw.githubusercontent.com/用户名/仓库名/main/mikasa-results/all.txt
https://cdn.jsdelivr.net/gh/用户名/仓库名@main/mikasa-results/all.txt
```

## 4. 常见错误

| 状态 | 处理 |
| --- | --- |
| 401 | 重新生成 Token |
| 403 | 检查 Token 是否具有目标仓库内容读写权限，或关闭分支保护 |
| 404 | 检查仓库地址、分支名和 Token 访问范围 |
| 409 | 仓库或分支正被同时修改，稍后重试 |
| 网络错误 | 检查代理、DNS 和 GitHub 连通性 |

上传失败不会影响本地导出。可以先生成到本地目录，再重新上传。

## 安全建议

- 只授权目标仓库，不授予无关权限。
- 定期更换 Token。
- 不要把 Token 发到聊天、截图、Issue 或公开仓库。
- 如怀疑泄露，立即在 GitHub 撤销旧 Token。
