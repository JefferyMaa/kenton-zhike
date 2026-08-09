# 知客首次使用指南

本指南服务第一次成功运行：下载并验证安装包，阅读并确认使用须知，完成卡密激活和抖音登录，再启动全自动评论回复。

## 1. 准备条件

- Mac Apple Silicon（打开“关于本机”可查看芯片类型；终端执行 `uname -m` 应输出 `arm64`），或 Windows 10/11 x64。
- 稳定网络。首次启动需要下载固定版本 Python 依赖和 Chromium。
- 自己的抖音账号和手机 App，用于扫码登录。
- 有效知客卡密。购买入口见[知客官网](https://zhike.crewup.cn/#buy)。

## 2. 下载正式包

从以下任一入口下载：

- [知客官网 macOS v2.1.7 ZIP](https://zhike.crewup.cn/dl/macos/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-macos-arm64.zip)
- [知客官网 Windows v2.1.7 ZIP](https://zhike.crewup.cn/dl/windows/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-windows-x64.zip)
- [GitHub Release v2.1.7](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.7)

官网下载使用中文文件名：

```text
知客-v2.1.7-macos-arm64.zip
知客-v2.1.7-windows-x64.zip
```

GitHub Release 使用 ASCII 文件名：

```text
Zhike-v2.1.7-macos-arm64.zip
Zhike-v2.1.7-windows-x64.zip
```

同一平台的中文包与 ASCII 包字节完全相同，SHA-256 也必须相同。两端核心 Python 模块采用 PyArmor Basic 混淆以提高逆向成本，但不代表无法破解。

## 3. 核对 SHA-256

macOS 假设文件位于“下载”目录：

```bash
shasum -a 256 "$HOME/Downloads/知客-v2.1.7-macos-arm64.zip"
# 从 GitHub 下载时改用：
shasum -a 256 "$HOME/Downloads/Zhike-v2.1.7-macos-arm64.zip"
```

输出的第一列必须是：

```text
b238b2608b2a8fd0065b3d1fdfae930b1d3616add2be8a438db0477bb5629d33
```

Windows 在 PowerShell 中运行：

```powershell
$File = "$HOME\Downloads\知客-v2.1.7-windows-x64.zip"
# 从 GitHub 下载时改为：$File = "$HOME\Downloads\Zhike-v2.1.7-windows-x64.zip"
(Get-FileHash $File -Algorithm SHA256).Hash.ToLower()
```

输出必须是：

```text
e8c852d8f380dc81d21d62ddd91dfff9ea3b1efdc6f70997ad0f0fb731575557
```

不一致时不要继续运行，请重新下载并再次核对。

## 4. 首次启动

1. 先把 ZIP 完整解压，不要在压缩包预览窗口里直接运行。
2. macOS 首次在 Finder 中右键 `启动.command`，选择“打开”并确认；如果仍被阻止，到「系统设置 → 隐私与安全性」点「仍要打开」。不要关闭 Gatekeeper，也不要运行移除 quarantine 的命令。
3. Windows 双击 `启动.bat`；普通 SmartScreen 提示可选「更多信息 → 仍要运行」。如果 Smart App Control 直接阻止，当前未签名版无法运行，请勿为知客关闭系统安全功能，改为联系购买渠道处理。
4. 保持启动窗口开启。首次准备运行环境需要数分钟，具体时间取决于网络。
5. 看到浏览器打开 `http://127.0.0.1:8300` 且显示“知客 2.1.7”后，表示本机服务已启动。

知客只监听本机地址。关闭启动终端窗口会停止软件。

## 5. 激活卡密

先阅读页面中的四点摘要及《使用须知》《软件授权与服务条款》《隐私说明》，主动勾选确认，再粘贴完整卡密并点击“激活”。成功后页面才会进入扫码登录和业务配置步骤。

软件会在激活、启动和运行中定期联网复核卡密、设备、有效期与吊销状态。未激活时，业务功能保持锁定；本机数据导出和清除仍可使用。

## 6. 登录并配置问答

1. 进入“扫码登录”，用自己的抖音 App 扫码。
2. 在“业务问答”中填写账号话术、作品问答和 FAQ。
3. 对价格、购买方式、合作等容易产生误解的问题，写清关键词与固定答案。
4. 不确定或不希望自动处理的内容不要配置匹配答案，让软件跳过。

当前产品只处理公开评论，不读取或存储私信。

## 7. 启动全自动回复

首次运行时保留默认稳健设置：

1. 核对业务问答中的价格、购买方式和合作话术仍然准确。
2. 点“立即自动跑一次”会马上匹配并发送。
3. 开启“每小时自动巡查”后，软件会在活跃时段内每小时完成同一流程，无需逐批确认；关闭开关后不会开始新一轮。
4. 如果发送结果显示“未知”，不要再次发送；先人工回读平台状态。

当运行记录显示本轮已完成，并且抖音评论区能读回对应回复，就完成了首次成功路径。

## 8. 使用后备份

在数据管理中导出知客备份 ZIP，并保存到自己控制的位置。升级前建议先导出一次。备份可能包含业务问答与评论处理记录，不要公开上传。

遇到问题请查看[故障排查](troubleshooting.md)。
