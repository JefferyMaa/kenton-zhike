---
name: 知客
origin: Kenton
type: public-distribution
status: active
---

# 知客

[English](README.en.md) | [简体中文](README.md)

知客是一款面向中国抖音创作者的 macOS / Windows 本地评论辅助工具。它读取未回复的公开评论，只从你配置的业务问答中匹配拟回复；你逐条预览并确认审核批次后，软件才发送这批内容。

![知客 v2.1.0 未激活页面，核心业务步骤保持锁定](docs/assets/zhike-v2.1.0-activation.jpg)

## 先判断是否适合你

知客适合需要按固定业务话术处理公开评论，并愿意在发送前人工审核的创作者或小团队。

当前版本需要：

- Mac Apple Silicon 或 Windows x64；
- 可正常访问软件安装源、知客授权服务和抖音的网络；
- 自己的抖音账号；
- 有效的知客在线卡密。

如果你需要无需人工审核的全自动直发、私信读取、云端大模型自由生成回复，或承诺零平台风险，当前版本不适合。

> 知客是第三方独立工具，与抖音（字节跳动）官方无关联，也未获得其授权或背书。任何自动化操作都可能触发平台规则或账号风险。

## 当前正式版

版本：`v2.1.0`

平台：macOS Apple Silicon / Windows x64

发行方式：公开下载安装包，核心业务功能必须使用在线卡密激活

源码状态：商业软件，本仓库不是开源源码仓库

### macOS Apple Silicon

- [从知客官网下载 v2.1.0](https://zhike.crewup.cn/dl/macos/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-macos-arm64.zip)
- [查看 GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.0)
- [查看 SHA-256 校验文件](https://zhike.crewup.cn/dl/macos/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-macos-arm64.zip.sha256)

```text
47758843ea05e84f3a4e45fe6de4df8f5d64178b67238b691fef8161f7ab8399
```

### Windows x64

- [从知客官网下载 v2.1.0](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip)
- [查看 GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.0)
- [查看 SHA-256 校验文件](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip.sha256)

```text
c723ad4bc70f59ffbcd273df3456dde51b9984bf3fc7923b0375feed8d3921a2
```

## 5 分钟首次使用

1. 下载 ZIP 并核对 SHA-256。
2. 解压后运行启动器：macOS 双击 `启动.command`（首次被阻止时在 Finder 中右键该文件并选择“打开”）；Windows 双击 `启动.bat`。
3. 等待首次环境准备完成。软件会安装哈希锁定的 Python 依赖并下载 Chromium，后续启动会复用本地环境。
4. 在本地页面输入购买时收到的卡密完成激活。
5. 扫码登录自己的抖音账号，填写业务问答，先生成逐条预览。
6. 检查作品、用户、原评论和拟回复，再确认发送审核批次。

完整步骤见[首次使用指南](docs/quickstart.md)。

## 主要能力

- 读取自己账号下尚未回复的公开评论；
- 只从本地业务问答库匹配拟回复，匹配不到时跳过；
- 价格问题只有命中已配置 FAQ 才会拟回复；
- 发送前展示逐条预览，并冻结一次性审核批次；
- 按账号隔离登录态、设置、配额和发送账本；
- 支持自定义随机间隔、每日上限和北京时间活跃时段；
- 区分已确认、未知和失败的发送结果，未知状态不会自动盲目重试；
- 支持导出和清除本机业务数据。

## 卡密与联网边界

下载软件不等于获得使用授权。未激活时，软件只开放启动诊断、授权激活/状态，以及本机业务数据的导出与清除；其他业务 API 默认拒绝。

授权码、产品标识和设备标识会在激活、启动及运行中定期发送到知客授权服务器，用于设备绑定、到期与吊销判断。运行中最长约有 1 小时的状态刷新窗口。

## 数据与隐私

平台登录态、业务问答、评论处理和发送账本默认保存在用户自己的电脑，不发送给知客授权服务器或外部大模型。软件会访问：

- 抖音，用于用户主动执行的登录和评论操作；
- Python 包及 Chromium 下载源，用于首次安装；
- 知客授权服务，用于卡密验证。

当前产品不读取或存储私信。公开评论可能涉及第三方个人信息，使用者须自行确保处理方式符合适用法律法规。

## 已知边界

- 当前交付 Mac Apple Silicon 与 Windows x64 两个版本。
- ZIP 通过 `启动.command` / `启动.bat` 运行：macOS 侧不是 Apple 公证的 `.app` 安装包；Windows 侧未做代码签名，SmartScreen 可能提示。
- 关键词匹配仍可能误命中，发送前必须人工审核。
- 抖音页面、接口或平台规则变化可能导致功能失效。
- 在线卡密属于软授权；macOS 与 Windows 版均为明文 Python，不能阻止有本机管理权限和逆向能力的人分析修改，因此不承诺“无法破解”。
- 使用软件不代表平台允许自动化，也不代表账号不会受到限制。

## 文档

- [首次使用指南](docs/quickstart.md)
- [故障排查](docs/troubleshooting.md)
- [安全政策](SECURITY.md)
- [v2.1.0 发布说明](docs/releases/v2.1.0.md)
- [知客官网](https://zhike.crewup.cn/)

## 获取卡密与支持

购买卡密请通过[知客官网](https://zhike.crewup.cn/#buy)公布的联系方式。一般使用问题可以提交 GitHub Issue，但请勿上传卡密、Cookie、登录态目录、完整日志或其他个人信息。

## 许可

本仓库公开的是发行说明与用户文档，不代表软件以开源许可证授权。软件、文档和发行包的使用受 [LICENSE](LICENSE) 及安装包内《软件授权与服务条款》约束；第三方组件适用各自许可证。
