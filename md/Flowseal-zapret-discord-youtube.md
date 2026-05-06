# Flowseal/zapret-discord-youtube 深度分析

> GitHub Trending 2026-05-05 | Stars: 27,242 (+106 today) | Language: Batchfile | License: MIT

---

## 项目简介

**zapret-discord-youtube** 是一个基于 [bol-van/zapret](https://github.com/bol-van/zapret) 的 Windows 预配置构建版本，专门用于绕过 ISP 层面的深度包检测（DPI）封锁，恢复对 **Discord**、**YouTube** 等服务的访问。该项目主要面向俄罗斯用户，帮助他们突破因政府封锁而导致的服务不可用问题。

项目名称中的 "zapret"（запрет）在俄语中意为"禁止"或"封锁"，直接点明了该工具的核心用途——对抗网络封锁。

---

## 核心功能

### 1. DPI 流量绕过
- 通过操纵网络数据包，避免被 ISP 的 DPI 系统检测和拦截
- 支持多种绕过策略（Strategy）：General、ALT、FAKE 等
- 不同策略适用于不同 ISP 和网络环境

### 2. 多服务支持
- **YouTube** — 绕过视频平台封锁
- **Discord** — 恢复文字聊天和语音通话
- **Telegram (Web版)** — 通过 hosts 文件修复
- 可自定义添加更多服务的域名和 IP

### 3. 一键安装与自动化
- 提供 `service.bat` 脚本实现服务安装、自动启动、诊断等
- 支持开机自启动（通过 Windows 服务管理器 services.msc）
- 内置自动更新检查机制

### 4. 诊断与测试工具
- **Run Diagnostics** — 检测常见故障原因
- **Run Tests** — 测试不同策略的可用性
- **DPI Checkers** — 检测不同 CDN（Cloudflare、Amazon 等）的 DPI 行为
- **Game Filter** — 可切换游戏/UDP 应用的绕过模式

### 5. 灵活的域名和 IP 管理
- `list-general-user.txt` — 添加需要绕过的域名
- `list-exclude-user.txt` — 排除特定域名
- `ipset-all.txt` — 管理 IP 和子网列表
- `ipset-exclude-user.txt` — 排除特定 IP

---

## 技术架构

```
┌─────────────────────────────────────────────────┐
│                  用户界面层                        │
│   general.bat (手动策略)  │  service.bat (服务管理)  │
├─────────────────────────────────────────────────┤
│                  策略配置层                        │
│   多种绕过策略 (General/ALT/FAKE/...)             │
│   域名列表  │  IP集合  │  Hosts文件               │
├─────────────────────────────────────────────────┤
│                  核心引擎层                        │
│   winws.exe (zapret 核心)                        │
│   WinDivert (网络流量拦截与过滤)                   │
├─────────────────────────────────────────────────┤
│                  系统内核层                        │
│   WinDivert64.sys (内核级网络驱动)                │
│   Windows 网络协议栈                              │
└─────────────────────────────────────────────────┘
```

### 工作原理
1. **WinDivert** 在内核层拦截网络流量（相当于 Linux 的 iptables + NFQUEUE）
2. **winws.exe**（zapret 核心）根据策略规则处理数据包
3. 通过修改 TCP/IP 数据包的特征（如 TTL、窗口大小、分段等）来欺骗 DPI 系统
4. DPI 系统无法正确识别被修改的数据包，从而放行流量

---

## 技术栈

| 组件 | 技术 | 说明 |
|------|------|------|
| 脚本语言 | Batchfile (.bat) | Windows 批处理脚本，用户交互 |
| 核心引擎 | C (winws.exe) | zapret 的 Windows 版本 |
| 网络驱动 | WinDivert | 内核级网络数据包拦截库 |
| 包管理 | GitHub Releases | 通过 Release 分发预编译二进制 |
| CI/CD | GitHub Actions | 自动构建和发布 |
| 配置 | 文本文件列表 | 域名、IP、排除列表 |

---

## 应用场景

1. **俄罗斯用户访问被封锁服务** — YouTube、Discord 等因政府封锁而无法使用
2. **企业/学校网络受限** — 绕过机构网络的特定服务限制
3. **网络研究** — 了解 DPI 技术原理和对抗方法
4. **游戏网络优化** — Game Filter 模式可帮助游戏连接

---

## 为什么火（Trending 原因）

1. **强烈的地缘政治需求** — 俄罗斯持续封锁西方互联网服务，大量用户需要此类工具
2. **极低使用门槛** — 下载解压运行 .bat 文件即可，无需技术背景
3. **免费开源** — MIT 许可，完全免费，无广告
4. **持续维护** — 截至 2026 年 4 月仍有活跃的 CI 构建和 Issue 回复
5. **社区驱动** — 超过 12,000 个 Issue 和活跃的 Discussions，形成良性循环
6. **2026 年 2 月首次登上 Trending** — 引发新一轮关注，Star 数持续增长
7. **唯一的免费 GUI-free 方案** — 与 VPN 相比更轻量，不需要代理服务器

---

## 同类项目对比

| 项目 | 特点 | 优势 | 劣势 |
|------|------|------|------|
| **Flowseal/zapret-discord-youtube** | Windows 预配置版 | 开箱即用，一键运行 | 仅限 Windows |
| **[bol-van/zapret](https://github.com/bol-van/zapret)** | 原始项目，支持多平台 | 更灵活，支持 Linux/Mac | 配置复杂 |
| **[ankddev/zapret-discord-youtube](https://github.com/ankddev/zapret-discord-youtube)** | Fork 版本 | 额外支持 Viber 等服务 | 社区较小 |
| **GoodbyDPI** | 另一个 DPI 绕过工具 | 轻量 | 策略较少 |
| **VPN 服务** | 全局代理 | 通用性强 | 需付费，可能被封 |

---

## 适合谁使用

- **俄罗斯普通网民** — 需要访问 YouTube、Discord 但不想付费 VPN
- **在俄罗斯的留学生和外籍人士** — 需要与国外保持联络
- **网络安全学习者** — 想了解 DPI 技术和绕过原理
- **系统管理员** — 需要理解网络审查机制的技术人员

---

## 快速上手指南

### 前提条件
- Windows 7 及以上（64位）
- 管理员权限
- 开启 Secure DNS（推荐）

### 安装步骤

```bash
# 1. 开启浏览器的安全 DNS
#    Chrome: 设置 → 隐私和安全 → 安全 → 使用安全 DNS
#    Firefox: 设置 → 隐私与安全 → DNS over HTTPS → 最大保护

# 2. 从 GitHub Releases 下载最新版本
#    https://github.com/Flowseal/zapret-discord-youtube/releases

# 3. 解除 Windows 文件锁定
#    右键 → 属性 → 勾选"解除锁定" → 确定

# 4. 解压到不含中文/特殊字符的路径

# 5. 运行策略脚本（以管理员身份）
general.bat        # 手动运行策略
# 或
service.bat        # 安装为系统服务（推荐）
```

### 常用操作

```bash
# 安装为自动启动服务
service.bat → Install Service → 选择策略

# 检查服务状态
service.bat → Check Status

# 运行诊断
service.bat → Run Diagnostics

# 测试不同策略
# 依次尝试 general.bat 中的不同策略，找到可用的
```

### 注意事项
- 杀毒软件可能误报 WinDivert 为病毒 — 需添加排除项
- 策略可能随时间失效 — 定期更新或更换策略
- 路径不要包含西里尔字母或特殊字符
- 游戏模式下可能影响反作弊系统

---

## 项目数据

| 指标 | 数值 |
|------|------|
| Stars | 27,242 |
| 今日新增 | +106 |
| 主要语言 | Batchfile |
| 许可证 | MIT |
| 上游项目 | bol-van/zapret |
| 最近活动 | 2026-04-29（CI 构建） |

---

*分析日期：2026-05-05*
