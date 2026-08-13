# Zhike (知客)

[English](README.md) | [简体中文](README.zh-CN.md)

Zhike is an automated front desk for your Douyin comment section, available for macOS Apple Silicon and Windows x64. It patrols comments, matches them against your local business scripts, and replies automatically during your configured active hours, with built-in guardrails and local data storage.

![Zhike v2.1.0 activation page — core business steps stay locked until activated](docs/assets/zhike-v2.1.0-activation.jpg)

## What it does

- **Automatic patrol**: scans all your videos on schedule and finds unreplied public comments; videos with comments come first, fresh uploads are covered too, old videos are not missed.
- **Automatic script matching**: a local business Q&A library (account scripts + per-video Q&A + FAQ) generates replies instantly; price, purchase, and partnership questions get your exact pre-written answers, no drifting.
- **Fully automatic execution**: with hourly auto-patrol on, Zhike matches and sends every hour during active hours with no per-batch approval; you can also run one automatic round immediately.
- **Built-in guardrails**: hard daily cap, send-ledger dedup (the same comment is never replied to twice), Beijing-time active hours, three-state send results (confirmed / unknown / failed) — unknown results are never blindly retried.
- **Multi-account isolation**: login state, scripts, quotas, and send ledgers are kept separate per account.
- **Data stays local**: one-click export, restore, and wipe; your business data is never uploaded.

Direct-message handling is on the product roadmap for upcoming versions.

## Current stable release

Version: `v2.1.7`　Platforms: macOS Apple Silicon and Windows x64

The installer is a public download; core business features activate with an online license key. Core Python modules use PyArmor Basic obfuscation to raise reverse-engineering cost, but this is not an “unbreakable” guarantee.

### macOS Apple Silicon

- [Download v2.1.7 from the official site](https://zhike.crewup.cn/dl/macos/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-macos-arm64.zip)
- [View the GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.7)
- [View the SHA-256 checksum file](https://zhike.crewup.cn/dl/macos/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-macos-arm64.zip.sha256)

```text
b238b2608b2a8fd0065b3d1fdfae930b1d3616add2be8a438db0477bb5629d33
```

### Windows x64

- [Download v2.1.7 from the official site](https://zhike.crewup.cn/dl/windows/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-windows-x64.zip)
- [View the GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.7)
- [View the SHA-256 checksum file](https://zhike.crewup.cn/dl/windows/2.1.7/%E7%9F%A5%E5%AE%A2-v2.1.7-windows-x64.zip.sha256)

```text
e8c852d8f380dc81d21d62ddd91dfff9ea3b1efdc6f70997ad0f0fb731575557
```

## Up and running in 5 minutes

1. Download the ZIP and verify its SHA-256.
2. Unzip and run the launcher:
   - macOS: first right-click `启动.command` → “Open”; if still blocked, use System Settings → Privacy & Security → “Open Anyway”.
   - Windows: double-click `启动.bat`; for a normal SmartScreen prompt choose “More info” → “Run anyway”. If Smart App Control blocks it, this unsigned release is not compatible—do not disable system security for Zhike.
3. Wait for first-time setup (hash-locked dependencies and Chromium install automatically; later launches are instant).
4. Enter your license key on the local page to activate.
5. Scan the QR code to log in to Douyin and fill in your business scripts.
6. Run one automatic round immediately, or enable hourly auto-patrol. Matching and sending are fully automatic with no per-batch approval.

Full walkthrough: [Quickstart guide](docs/quickstart.md) (Chinese).

## License key and network boundary

Downloading the software does not grant a usage license. Before activation, only startup diagnostics, license activation/status, and local data export/wipe are available; every other business API is rejected by default.

The license key, product ID, and device ID are sent to the Zhike license server during activation, at startup, and periodically at runtime for device binding, expiry, and revocation checks. The runtime refresh window is at most about 1 hour.

## Data and privacy

Platform login state, business scripts, comment-processing records, and the send ledger live on your own computer by default. They are not sent to the Zhike license server or to any external LLM.

The software talks to exactly three places: Douyin (for the login and comment operations you initiate), the dependency/Chromium download sources (first-time setup), and the Zhike license service (key verification).

Public comments may contain third-party personal information; use the tool in compliance with applicable laws.

## Boundaries

- Zhike is an independent third-party tool with no affiliation with Douyin (ByteDance); automation carries platform-rule and account risk — assess it yourself.
- Keyword matching can mis-hit; keep scripts accurate and current, and regularly check the comment area and send ledger.
- Douyin page or API changes may affect functionality; we track them with releases.
- The macOS build is not Apple-notarized; the Windows build is unsigned (SmartScreen may warn, and Smart App Control may block it). Do not disable system security to run Zhike. Both packages use PyArmor Basic for core Python modules; it raises reverse-engineering cost but does not make the software unbreakable.

## Documentation

- [Quickstart guide](docs/quickstart.md) (Chinese)
- [Troubleshooting](docs/troubleshooting.md) (Chinese)
- [Security policy](SECURITY.md)
- [v2.1.7 release notes](docs/releases/v2.1.7.md) (Chinese)
- [Official site](https://zhike.crewup.cn/)

## Purchase and support

To buy a license key, use the contact channels on the [official site](https://zhike.crewup.cn/#buy). Open a GitHub Issue for usage problems, but never upload license keys, cookies, login-state directories, or full logs.

## License

This repository publishes release notes and user documentation; the software itself is not open-source licensed. Use is governed by [LICENSE](LICENSE) and the Software License & Service Terms inside the package; third-party components keep their own licenses.

<!-- name: Zhike | origin: Kenton | type: public-distribution | status: active -->

## 联系 Kenton

- 个人博客：[Kenton Blog](https://kenton.crewup.cn/)
- 公开邮箱：[dilipkhandale351@gmail.com](mailto:dilipkhandale351@gmail.com)
