# cmux — AI 编程时代的下一代终端

> **GitHub**: [manaflow-ai/cmux](https://github.com/manaflow-ai/cmux) | **官网**: [cmux.com](https://cmux.com) | **Stars**: 18.1k+ | **协议**: GPL-3.0

## 项目简介

**cmux** 是由 [Manaflow](https://manaflow.com)（Y Combinator 孵化的两人创业公司）开发的开源 macOS 终端模拟器。它基于 **Ghostty**（Mitchell Hashimoto 创建的高性能终端）构建，使用 Swift/AppKit 原生开发，专为同时管理多个 AI 编程 Agent 会话而设计。

两个月内突破万 Star，GitHub Trending 开发者工具榜第一名。

## 核心功能

### 通知环（Notification Rings）
- Agent 等待输入时，对应窗格显示蓝色光环
- 侧边栏标签高亮
- `Cmd+Shift+U` 跳转到最近未读

### 垂直 + 水平标签页
- 侧边栏显示 Git 分支、关联 PR 状态/编号、工作目录、监听端口、最新通知文本
- 支持水平和垂直分屏

### 内置浏览器
- 从 agent-browser 移植的可编程浏览器 API
- Agent 可获取可访问性树、点击元素、填写表单、执行 JS
- 可与终端并排显示

### SSH 集成
- `cmux ssh user@remote` 创建远程工作区
- 浏览器窗格通过远程网络路由，localhost 直接可用
- 拖拽图片上传（scp）

### Claude Code Teams
- `cmux claude-teams` 一键启动 Claude Code 的 teammate 模式
- 队友以原生分屏形式出现，无需 tmux

### 会话恢复
- 退出时自动保存，重新打开恢复布局、工作目录、滚动历史
- 支持 Claude Code、Codex、Gemini CLI 等 15+ 种 Agent 的自动恢复

## 技术架构

| 维度 | 详情 |
|---|---|
| 语言 | Swift |
| 框架 | AppKit (原生 macOS) |
| 渲染引擎 | libghostty (GPU 加速) |
| 自动更新 | Sparkle |
| API | CLI + Socket API |
| 兼容配置 | 读取 `~/.config/ghostty/config` |

**兼容的 AI 编程工具**: Claude Code, Codex, OpenCode, Gemini CLI, Kiro, Aider, Grok, Pi, Amp, Cursor CLI, Rovo Dev, Copilot, CodeBuddy, Factory, Qoder

## 应用场景

1. **多 Agent 并行开发** — 同时运行多个 Claude Code / Codex 会话，每个处理不同任务
2. **Code Review 工作流** — 分屏中同时运行代码审查和开发 Agent
3. **远程开发** — SSH 增强，浏览器路由无需端口转发
4. **团队协作** — Claude Code Teams 多 Agent 协作
5. **Web 自动化测试** — 内置浏览器与开发服务器交互
6. **CI/CD 监控** — 通知系统在需要人工介入时提醒

## 为什么火（Trending 原因）

1. **精准切入 AI 编程痛点** — 多 Agent 并行时通知管理是刚需，cmux 是目前唯一专注此场景的终端
2. **Ghostty 生态加持** — 基于热门终端 Ghostty 构建，天然获得关注
3. **原生性能** — Swift + AppKit，非 Electron，启动快、内存低
4. **爆发式增长** — 两个月破万 Star，社区口碑传播
5. **"原语而非方案"哲学** — 不规定使用方式，提供可组合基础设施
6. **AI Agent 生态爆发** — Claude Code、Codex 等工具增长带来终端管理需求
7. **YC 背景** — Manaflow 是 YC 孵化项目

## 同类项目对比

| 特性 | cmux | Ghostty | iTerm2 | Warp |
|---|---|---|---|---|
| AI Agent 通知 | ✅ 专属系统 | ❌ | ❌ | ⚠️ 有限 |
| 垂直标签页+元数据 | ✅ Git/PR/端口 | ❌ | ⚠️ 基本标签 | ⚠️ 基本标签 |
| 内置浏览器 | ✅ 可编程 API | ❌ | ❌ | ❌ |
| Agent 会话恢复 | ✅ 15+ Agent | ❌ | ⚠️ 基本恢复 | ❌ |
| SSH 增强 | ✅ 浏览器路由 | ❌ | ❌ | ❌ |
| 技术栈 | Swift/AppKit | Zig | Objective-C | Rust+Electron |
| 平台 | macOS | macOS/Linux | macOS | 跨平台 |

## 适合谁使用

- **重度 AI 编程用户** — 每天运行 3+ 个 Agent 会话
- **macOS 原生终端用户** — 已在使用 Ghostty 或追求原生性能
- **远程开发者** — 需要 SSH 增强功能
- **工具定制爱好者** — 喜欢通过 CLI/API 定制工作流

**不适合**: Linux/Windows 用户（仅 macOS）、轻度终端用户

## 快速上手

### 安装

```bash
# Homebrew（推荐）
brew tap manaflow-ai/cmux
brew install --cask cmux

# 或从 GitHub Releases 下载 DMG
```

### 设置 Agent Hooks

```bash
# 安装所有已检测到的 Agent hooks
cmux hooks setup

# 或指定特定 Agent
cmux hooks setup codex
cmux hooks setup --agent opencode
```

### 开始使用

```bash
# 打开 cmux，⌘N 创建新工作区
cmux

# 一键启动 Claude Code Teams
cmux claude-teams

# SSH 到远程服务器
cmux ssh user@remote
```

### 关键快捷键

| 快捷键 | 功能 |
|---|---|
| `⌘N` | 新建工作区 |
| `⌘⇧U` | 跳转到最近未读通知 |
| `⌘I` | 打开通知面板 |
| `⌘D` | 右侧分屏 |
| `⌘⇧D` | 下方分屏 |
| `⌘B` | 切换侧边栏 |
| `⌘⇧L` | 在分屏中打开浏览器 |

## 综合评分

| 维度 | 分数 | 说明 |
|---|---|---|
| 创新性 | ⭐ 9.0/10 | AI Agent 通知系统 + 内置浏览器的组合是终端领域的创新 |
| 代码质量 | ⭐ 8.5/10 | 原生 Swift 开发，架构清晰，但项目较新仍在快速迭代 |
| 实用性 | ⭐ 9.5/10 | 解决了真实痛点，兼容 15+ 种 Agent 工具 |
| 文档完善度 | ⭐ 8.0/10 | README 详尽，有独立文档站点，但部分 API 文档仍在完善 |
| 社区活跃度 | ⭐ 9.0/10 | 98 贡献者，Discord 活跃，创始人积极回应 Issue |

**综合评分: 8.8 / 10**

## 总结

cmux 是 AI 编程生态中定位最精准的终端工具。它聚焦"让多 Agent 并行开发不再痛苦"这一个核心问题，基于 Ghostty 引擎 + 原生 Swift + 通知系统 + 内置浏览器 + CLI/Socket API 构成一套可组合的原语。两个月破万 Star 的增长证明了市场需求。如果你是 macOS 上的重度 AI 编程用户，cmux 是目前的不二之选。

---

*分析日期: 2026-05-25 | 数据来源: [GitHub](https://github.com/manaflow-ai/cmux), [TrendShift](https://trendshift.io/repositories/27053), [DEV Community](https://dev.to/neuraldownload/cmux-the-terminal-built-for-ai-coding-agents-3l7h)*