# FadCam - 开源无广告 Android 多媒体录制套件

> **GitHub**: [anonfaded/FadCam](https://github.com/anonfaded/FadCam) | **Stars**: 2,237 | **Today**: +116 | **语言**: Java

## 项目简介与核心功能

FadCam 是由 **FadSec Lab** 开发的开源、无广告 Android 多媒体录制套件。它集成了后台视频录制、行车记录仪、屏幕录制、局域网直播和远程摄像头控制等多种功能，主打**隐私优先**和**无广告体验**。

### 核心功能模块

- **FadRec 屏幕录制** — 全功能屏幕录制，支持标注工具（画笔、橡皮擦、文字、形状），多层编辑与版本控制
- **FadCam Remote** — 局域网实时直播摄像头画面，支持远程控制录制、调整设置、开关手电筒
- **行车记录仪 & 后台录制** — 支持息屏后台录制，fMP4 格式零损风险，大文件自动分割
- **视频 & 音频控制** — 多分辨率 + 60/90fps 支持，自定义水印和地理标记
- **文件管理** — 增强缩略图、排序过滤、回收站、内置 ExoPlayer 播放器
- **精美界面** — Material Design，7+ 主题，15+ 自定义图标

## 技术架构与特点

### 技术栈
- **Java** / Android SDK
- **ExoPlayer** — 内置视频播放
- **MediaCodec** — 硬件编码
- **Material Design** — 界面设计
- **Fragmented MP4** — 录制格式
- **Nominatim (OSM)** — 地理编码

### 架构亮点
1. **Fragmented MP4 (fMP4)** — 分段式封装，录制中断不损坏文件
2. **Foreground Service** — Android 后台持续录制，配合通知栏控制
3. **内置 HTTP 服务器** — 局域网直播 + Web 远程控制界面
4. **零数据收集** — 完全无追踪、无广告、无数据收集
5. **App Shortcuts** — 快捷操作可映射到硬件按键

## 应用场景

| 场景 | 说明 |
|------|------|
| 行车记录仪 | 替代专用设备，后台持续录制，fMP4 确保数据安全 |
| 家庭安防 | 将旧手机变 CCTV，通过局域网实时监控 |
| 屏幕录制教程 | FadRec 配合标注工具，制作 App 演示 |
| 个人安全记录 | 后台 discreet 录制，保护个人权益 |
| 内容创作 | 屏幕录制 + 标注的专业工具组合 |

## 为什么火（Trending 原因）

1. **隐私意识觉醒** — 被 PrivacyGuides、GrapheneOS 社区推荐，正中用户痛点
2. **多媒体 All-in-One** — 一个 App 集成五大功能，替代多个专用 App
3. **KOL 强力推荐** — HowToMen、Sam Beckman 等知名 YouTuber 多次推荐
4. **多平台分发** — GitHub、F-Droid、IzzyOnDroid、Amazon Appstore 全覆盖
5. **活跃迭代** — 当前 v3.1.0-beta，持续推出新功能
6. **FadSec Lab 生态** — 与 FadCrypt 等产品形成品牌矩阵

## 同类项目对比

| 特性 | FadCam | Open Camera | Background Video Recorder |
|------|--------|-------------|--------------------------|
| 开源 | 完全开源 | 完全开源 | 闭源 |
| 广告 | 无广告 | 无广告 | 有广告 |
| 后台录制 | 支持 | 不支持 | 支持 |
| 屏幕录制 | 支持（含标注） | 不支持 | 不支持 |
| 局域网直播 | 支持 | 不支持 | 不支持 |
| 远程控制 | 支持 | 不支持 | 不支持 |
| 行车记录模式 | 支持 | 不支持 | 不支持 |
| fMP4 防损 | 支持 | 不支持 | 不支持 |

## 适合谁使用

- **隐私敏感用户** — 厌倦广告和数据收集，想要完全掌控录制内容
- **车主/司机** — 需要可靠的行车记录仪替代方案
- **内容创作者** — 需要屏幕录制 + 标注工具
- **技术爱好者** — 喜欢将旧手机改造为远程监控设备

## 快速上手

### 方式一：直接下载 APK
```
# 从 GitHub Releases 下载最新版本
https://github.com/anonfaded/FadCam/releases
```

### 方式二：F-Droid / IzzyOnDroid
```
# 在 F-Droid 中搜索 "FadCam"
https://f-droid.org/packages/com.fadcam/
```

### 方式三：从源码编译
```bash
git clone https://github.com/anonfaded/FadCam.git
cd FadCam
./gradlew assembleDebug
adb install app/build/outputs/apk/debug/app-debug.apk
```

### 基本使用
- **后台录制**：打开 App → 点击录制 → 锁屏或切换 App → 录制继续
- **远程监控**：同一局域网 → 启用 Remote → 浏览器输入显示的地址
- **屏幕录制**：切换到 FadRec → 开始录制 → 使用浮动工具栏添加标注

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 8.0/10 | 多功能集成在开源领域独树一帜 |
| 代码质量 | 7.5/10 | 结构清晰，持续重构优化 |
| 实用性 | 9.0/10 | 解决真实需求，功能覆盖面广 |
| 文档完善度 | 8.5/10 | README 详尽，截图丰富，多语言支持 |
| 社区活跃度 | 8.0/10 | Discord 活跃，KOL 覆盖广 |

**综合评分：8.2 / 10**

FadCam 是 Android 多媒体录制领域非常突出的开源项目，将五大功能集于一体且保持无广告、无数据收集。特别推荐给注重隐私的 Android 用户、车主和技术爱好者。

---

*分析时间：2026-05-13 | 数据来源：GitHub API + Web Research*
