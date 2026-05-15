# Genymobile/scrcpy - Android 设备投屏与控制终极利器

> Display and control your Android device

| 指标 | 数据 |
|------|------|
| 语言 | C |
| Stars | 141,011 |
| 今日新增 | +589 |
| 许可证 | Apache-2.0 |
| 当前版本 | v4.0 |

---

## 项目简介

**scrcpy**（发音 "screen copy"）是 Genymobile 开发的一款开源工具，通过 USB 或 TCP/IP 将 Android 设备的屏幕（包括视频和音频）实时镜像到电脑上，并允许使用电脑的键盘和鼠标直接控制手机。

它是 GitHub 上最受欢迎的 Android 投屏工具，拥有超过 14 万 Star，由 [@rom1v](https://github.com/rom1v) 主要开发和维护。

### 核心特性

- **极致轻量** — 原生实现，仅显示设备画面，无多余 UI，不在设备上安装任何应用
- **超高性能** — 30~120fps 自适应帧率，1920x1080 及以上分辨率，延迟仅 35~70ms，启动约 1 秒
- **音频转发** — Android 11+ 支持音频同步转发到电脑
- **屏幕录制** — 内置录屏功能，支持 H.264/H.265 编码，直接保存为 MP4
- **虚拟显示器** — 可在电脑上创建独立的 Android 虚拟屏幕
- **摄像头镜像** — Android 12+ 支持直接镜像设备摄像头
- **游戏手柄支持** — 通过 HID 模拟物理键盘/鼠标和游戏手柄
- **跨平台** — 完整支持 Linux、Windows、macOS

---

## 技术架构

| 维度 | 技术选型 |
|------|----------|
| 核心语言 | C（高性能原生实现） |
| 构建系统 | Meson |
| 视频编码 | H.264 / H.265（通过 Android MediaCodec） |
| 音频编码 | AAC / Opus / FLAC |
| 通信协议 | ADB (Android Debug Bridge) |
| 渲染引擎 | SDL2 |
| 连接方式 | USB / TCP/IP（WiFi） |

### 架构亮点

1. **零安装设计** — 无需在 Android 设备端安装任何 APK，完全通过 ADB 协议通信
2. **硬件编解码** — 利用设备端硬件编码器（MediaCodec），高效推送视频流
3. **USB 与无线双模** — USB 模式最低延迟，TCP/IP 模式无线便利
4. **OTG 模式** — 无需 USB 调试即可通过 HID 协议控制设备
5. **单二进制文件** — 无需安装，即开即用

---

## 应用场景

1. **应用开发与调试** — 在大屏上实时查看应用表现，截图录屏，快速调试 UI
2. **演示与教学** — 将手机操作实时投影到大屏/投影仪
3. **自动化测试** — 结合脚本实现自动化测试流程，录屏保存测试过程
4. **远程办公** — 通过无线连接远程操控手机，处理消息和通知
5. **游戏投屏** — 使用键盘/鼠标/手柄在大屏上玩 Android 游戏
6. **内容创作** — 录制高质量 App 使用教程、游戏实况等内容

---

## 为什么火（Trending 原因）

1. **持续迭代，功能不断增强** — 从简单屏幕镜像发展到音频转发、摄像头镜像、虚拟显示器、游戏手柄等高级功能
2. **极致性能，碾压竞品** — 35~70ms 延迟远低于任何商业投屏软件，完全免费无广告无水印
3. **生态繁荣** — guiscrcpy、QtScrcpy 等 GUI 封装降低了使用门槛，反过来促进核心项目传播
4. **Android 开发者刚需** — 随着 Android 15 发布，开发者对高效调试工具的需求持续增长
5. **14 万 Star 口碑效应** — GitHub 上 Star 数最高的 Android 工具之一，新用户不断被推荐而来

---

## 同类项目对比

| 特性 | scrcpy | Vysor | Samsung DeX | LetsView | Windows Phone Link |
|------|--------|-------|-------------|----------|-------------------|
| 价格 | 免费开源 | 免费+付费 | 免费(仅三星) | 免费 | 免费 |
| 延迟 | 35~70ms | 中等 | 中等 | 较高 | 较高 |
| 帧率 | 30~120fps | ~30fps | ~30fps | ~30fps | ~30fps |
| 广告/水印 | 无 | 有(免费版) | 无 | 有 | 无 |
| 跨平台 | Win/Mac/Linux | Win/Mac/Linux | Win only | Win/Mac | Win only |
| 无线连接 | USB + WiFi | USB + WiFi | USB + WiFi | WiFi | WiFi |
| 屏幕录制 | 内置 | 付费版 | 无 | 内置 | 有限 |

---

## 适合谁使用

- **Android 开发者** — 日常调试必备，比模拟器更流畅、更贴近真实设备
- **测试工程师** — 多设备投屏测试，录屏保存缺陷复现过程
- **技术博主/讲师** — 高清录屏制作教程，实时投屏演示
- **Linux 用户** — 对 Linux 支持最好，V4L2 虚拟摄像头等高级功能仅 Linux 可用

---

## 快速上手

### 安装

```bash
# Ubuntu/Debian
sudo apt install scrcpy

# macOS (Homebrew)
brew install scrcpy

# Windows (Scoop)
scoop install scrcpy

# Windows (winget)
winget install Genymobile.scrcpy

# Arch Linux
sudo pacman -S scrcpy
```

### 准备设备

在 Android 设备上开启「开发者选项」→「USB 调试」，用 USB 线连接电脑。

### 基本使用

```bash
# 基本投屏（USB 连接）
scrcpy

# 无线连接
scrcpy --tcpip=<设备IP>

# 高清模式
scrcpy --video-codec=h265 -m1920 --max-fps=60

# 录屏
scrcpy --record=demo.mp4

# 关闭手机屏幕（省电）
scrcpy --turn-screen-off

# 虚拟显示器
scrcpy --new-display=1920x1080

# 镜像摄像头
scrcpy --video-source=camera --camera-size=1920x1080
```

### 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| 右键点击 | 返回 (BACK) |
| 中键点击 | 主页 (HOME) |
| Alt + F | 全屏切换 |
| Alt + O | 关闭设备屏幕 |
| Ctrl + C/V | 复制粘贴（双向） |
| Ctrl + S | 截图 |

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 实用性 | 10/10 | Android 开发和日常使用必备工具，功能全面 |
| 代码质量 | 9.5/10 | 单人维护却保持极高水准，C 语言原生实现精炼高效 |
| 社区活跃度 | 10/10 | 14 万+ Star，社区活跃，GUI 封装生态丰富 |
| 文档完善度 | 9/10 | 按功能模块分类的详细文档，覆盖所有使用场景 |
| 创新性 | 8/10 | 投屏概念不新，但实现方式和性能做到了极致 |
| **综合评价** | **9.3/10** | 开源工具的标杆之作 |

> scrcpy 是开源工具中的标杆之作 — 代码精炼、功能完备、性能卓越。作者 @rom1v 常年一人维护，却保持着极高的代码质量和发布节奏。它证明了一个人也能做出改变行业的软件。

---

*分析日期: 2026-05-15 | 数据来源: GitHub, WebSearch | 由 AI 深度分析生成*
