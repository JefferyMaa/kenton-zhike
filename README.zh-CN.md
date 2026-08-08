# 知客

[English](README.md) | [简体中文](README.zh-CN.md)

知客是抖音评论区的自动接待员（当前新用户正式版为 macOS Apple Silicon）。它自动巡查你账号下的作品评论，按你配置的业务话术自动匹配、自动回复——在你设定的活跃时段内持续值守，护栏内建，数据全在本机。

![知客 v2.1.0 未激活页面，核心业务步骤保持锁定](docs/assets/zhike-v2.1.0-activation.jpg)

## 它能做什么

- **自动巡查**：按计划扫描你的全部作品，自动发现未回复的公开评论；有评论的作品优先，新发作品兜底，不漏老视频。
- **自动匹配话术**：本地业务问答库（账号话术 + 作品问答 + FAQ）即时生成回复；价格、购买方式、合作等关键问题按你写好的固定答案回，不跑偏。
- **全自动执行**：开启「每小时自动巡查」后，软件在活跃时段内每小时自动匹配并发送，无需逐批确认；也可点「立即自动跑一次」。
- **护栏内建**：每日上限硬封顶、发送账本去重（同一条评论绝不重复回）、北京时间活跃时段、发送结果三态（已确认 / 未知 / 失败），未知状态不盲目重试。
- **多账号隔离**：登录态、话术、配额、发送账本按账号各管各的。
- **数据留在本机**：支持一键导出、恢复、清除；不上传你的业务数据。

私信接待在产品路线图上，后续版本推进。

## 当前正式版

版本：`v2.1.2`　新用户平台：macOS Apple Silicon

安装包公开下载，核心业务功能使用在线卡密激活。

### macOS Apple Silicon

- [从知客官网下载 v2.1.2](https://zhike.crewup.cn/dl/macos/2.1.2/%E7%9F%A5%E5%AE%A2-v2.1.2-macos-arm64.zip)
- [查看 GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.2)
- [查看 SHA-256 校验文件](https://zhike.crewup.cn/dl/macos/2.1.2/%E7%9F%A5%E5%AE%A2-v2.1.2-macos-arm64.zip.sha256)

```text
8c77de94835bdcce37ac745481c01d5ecb8b8958d46e1ac9d34f183543b742c2
```

### Windows x64（仅已有用户恢复）

v2.1.2 暂未开放 Windows 新用户交付。下面的 v2.1.0 旧包只供已经激活的同一设备恢复使用，不接受新设备首次激活。

- [从知客官网下载 v2.1.0](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip)
- [查看 GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.0)
- [查看 SHA-256 校验文件](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip.sha256)

```text
c723ad4bc70f59ffbcd273df3456dde51b9984bf3fc7923b0375feed8d3921a2
```

## 5 分钟上手

1. 下载 ZIP，核对 SHA-256。
2. 解压运行启动器：macOS 双击 `启动.command`（首次被阻止时右键选「打开」）；Windows 双击 `启动.bat`。
3. 等首次环境准备完成（自动安装哈希锁定的依赖和 Chromium，之后启动秒开）。
4. 在本地页面输入卡密激活。
5. 扫码登录抖音，填好业务话术。
6. 点「立即自动跑一次」马上匹配并发送，或开启「每小时自动巡查」持续值守；无需逐批确认。

完整步骤见[首次使用指南](docs/quickstart.md)。

## 卡密与联网边界

下载软件不等于获得使用授权。未激活时只开放启动诊断、授权激活/状态和本机数据导出清除，其余业务 API 默认拒绝。授权码、产品标识和设备标识会在激活、启动及运行中定期发送到知客授权服务器，用于设备绑定、到期与吊销判断；运行中最长约 1 小时刷新一次状态。

## 数据与隐私

平台登录态、业务话术、评论处理记录和发送账本默认保存在你自己的电脑上，不发送给知客授权服务器，也不发给外部大模型。软件联网只访问三处：抖音（你发起的登录与评论操作）、依赖与 Chromium 下载源（首次安装）、知客授权服务（卡密验证）。公开评论可能涉及第三方个人信息，请按适用法律法规使用。

## 边界

- 知客是第三方独立工具，与抖音（字节跳动）官方无关联；自动化操作存在平台规则与账号风险，请自行评估。
- 关键词匹配可能误命中，请只配置准确、仍然有效的话术，并定期检查评论区和发送账本。
- 抖音页面或接口改版可能影响功能，我们随版本跟进。
- macOS 侧非 Apple 公证 `.app`，Windows 侧未做代码签名（SmartScreen 可能提示）；两端均为明文 Python 软授权，不承诺防逆向。

## 文档

- [首次使用指南](docs/quickstart.md)
- [故障排查](docs/troubleshooting.md)
- [安全政策](SECURITY.md)
- [v2.1.2 发布说明](docs/releases/v2.1.2.md)
- [知客官网](https://zhike.crewup.cn/)

## 获取卡密与支持

购买卡密走[知客官网](https://zhike.crewup.cn/#buy)公布的联系方式。使用问题可提 GitHub Issue，请勿上传卡密、Cookie、登录态目录或完整日志。

## 许可

本仓库公开发行说明与用户文档，软件本身不以开源许可证授权。软件、文档和发行包的使用受 [LICENSE](LICENSE) 及安装包内《软件授权与服务条款》约束；第三方组件适用各自许可证。

<!-- name: 知客 | origin: Kenton | type: public-distribution | status: active -->
