# Zhike (知客)

[English](README.en.md) | [简体中文](README.md)

Zhike is an automated front desk for your Douyin comment section (local software for macOS / Windows). It automatically patrols the comments under your videos, matches them against your business scripts, and replies automatically — standing watch during your configured active hours, with built-in guardrails, and all data kept on your own machine.

![Zhike v2.1.0 activation page — core business steps stay locked until activated](docs/assets/zhike-v2.1.0-activation.jpg)

## What it does

- **Automatic patrol**: scans all your videos on schedule and finds unreplied public comments; videos with comments come first, fresh uploads are covered too, old videos are not missed.
- **Automatic script matching**: a local business Q&A library (account scripts + per-video Q&A + FAQ) generates replies instantly; price, purchase, and partnership questions get your exact pre-written answers, no drifting.
- **Automatic execution**: with "hourly auto-patrol" on, Zhike runs a full round every hour during active hours and prepares the whole reply batch — you release it with one click; randomized intervals mimic a human rhythm.
- **Fully unattended mode (advanced)**: the package ships with a scheduled executor, `comment_cron.py`; hook it into your system scheduler and it runs with no clicks at all, with every guardrail still enforced.
- **Built-in guardrails**: hard daily cap, send-ledger dedup (the same comment is never replied to twice), Beijing-time active hours, three-state send results (confirmed / unknown / failed) — unknown results are never blindly retried.
- **Multi-account isolation**: login state, scripts, quotas, and send ledgers are kept separate per account.
- **Data stays local**: one-click export, restore, and wipe; your business data is never uploaded.

Direct-message handling is on the product roadmap for upcoming versions.

## Current stable release

Version: `v2.1.0`　Platforms: macOS Apple Silicon / Windows x64

The installer is a public download; core business features activate with an online license key.

### macOS Apple Silicon

- [Download v2.1.0 from the official site](https://zhike.crewup.cn/dl/macos/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-macos-arm64.zip)
- [View the GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.0)
- [View the SHA-256 checksum file](https://zhike.crewup.cn/dl/macos/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-macos-arm64.zip.sha256)

```text
47758843ea05e84f3a4e45fe6de4df8f5d64178b67238b691fef8161f7ab8399
```

### Windows x64

- [Download v2.1.0 from the official site](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip)
- [View the GitHub Release](https://github.com/JefferyMaa/kenton-zhike/releases/tag/v2.1.0)
- [View the SHA-256 checksum file](https://zhike.crewup.cn/dl/windows/2.1.0/%E7%9F%A5%E5%AE%A2-v2.1.0-windows-x64.zip.sha256)

```text
c723ad4bc70f59ffbcd273df3456dde51b9984bf3fc7923b0375feed8d3921a2
```

## Up and running in 5 minutes

1. Download the ZIP and verify its SHA-256.
2. Unzip and run the launcher: double-click `启动.command` on macOS (right-click → "Open" if blocked on first run); double-click `启动.bat` on Windows.
3. Wait for first-time setup (hash-locked dependencies and Chromium install automatically; later launches are instant).
4. Enter your license key on the local page to activate.
5. Scan the QR code to log in to Douyin and fill in your business scripts.
6. Hit "Preview" to check the first batch, release it — then switch on hourly auto-patrol and let it stand watch.

Full walkthrough: [Quickstart guide](docs/quickstart.md) (Chinese).

## License key and network boundary

Downloading the software does not grant a usage license. Before activation, only startup diagnostics, license activation/status, and local data export/wipe are available; every other business API is rejected by default. The license key, product ID, and device ID are sent to the Zhike license server during activation, at startup, and periodically at runtime for device binding, expiry, and revocation checks; the runtime refresh window is at most about 1 hour.

## Data and privacy

Platform login state, business scripts, comment-processing records, and the send ledger live on your own computer by default; they are not sent to the Zhike license server or to any external LLM. The software talks to exactly three places: Douyin (for the login and comment operations you initiate), the dependency/Chromium download sources (first-time setup), and the Zhike license service (key verification). Public comments may contain third-party personal information; use the tool in compliance with applicable laws.

## Boundaries

- Zhike is an independent third-party tool with no affiliation with Douyin (ByteDance); automation carries platform-rule and account risk — assess it yourself.
- Keyword matching can mis-hit; for high-stakes scripts, use preview mode to gate the first rounds.
- Douyin page or API changes may affect functionality; we track them with releases.
- The macOS build is not an Apple-notarized `.app`; the Windows build is unsigned (SmartScreen may warn). Both ship as plaintext Python under a soft license — no anti-reverse-engineering claims.

## Documentation

- [Quickstart guide](docs/quickstart.md) (Chinese)
- [Troubleshooting](docs/troubleshooting.md) (Chinese)
- [Security policy](SECURITY.md)
- [v2.1.0 release notes](docs/releases/v2.1.0.md) (Chinese)
- [Official site](https://zhike.crewup.cn/)

## Purchase and support

To buy a license key, use the contact channels on the [official site](https://zhike.crewup.cn/#buy). Open a GitHub Issue for usage problems, but never upload license keys, cookies, login-state directories, or full logs.

## License

This repository publishes release notes and user documentation; the software itself is not open-source licensed. Use is governed by [LICENSE](LICENSE) and the Software License & Service Terms inside the package; third-party components keep their own licenses.

<!-- name: Zhike | origin: Kenton | type: public-distribution | status: active -->
