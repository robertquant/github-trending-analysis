# jcode - 下一代 AI 编程代理框架

> **The next generation coding agent harness to raise the skill ceiling.**

| 指标 | 数据 |
|------|------|
| 项目地址 | [github.com/1jehuang/jcode](https://github.com/1jehuang/jcode) |
| 主要语言 | Rust |
| Star 数 | 3,672+ |
| 今日新增 | +591 |
| 开源协议 | 开源 |
| 支持平台 | Linux / macOS / Windows |

---

## 项目简介

jcode 是一个用 Rust 编写的**下一代编程代理框架（Coding Agent Harness）**，专为多会话工作流、极致性能和无限可定制性而设计。它不是又一个 AI 编程助手，而是一个"元框架"——负责管理 AI 编程代理与代码环境之间的全部交互，包括请求编排、工具提供、上下文保持和多代理协调。

简单理解：Claude Code、Codex CLI 等是"驾驶员"，而 jcode 是"赛车底盘"——换任何 AI 模型都能在上面跑。

---

## 核心功能

### 1. 极致性能
- **启动速度**：14ms 到第一帧（Claude Code 需要 3.4 秒，慢 245 倍）
- **内存占用**：单会话仅 28MB（Claude Code 387MB，是 jcode 的 14 倍）
- **多会话扩展**：每增加一个会话仅增约 10MB 内存
- **渲染性能**：超过 1000 FPS，无闪烁问题

### 2. 智能记忆系统
- 每一轮对话都被编码为语义向量
- 通过余弦相似度自动检索相关记忆
- 记忆提取、整合、去重全自动
- 支持显式记忆工具进行主动搜索和存储
- 类似人类的记忆机制——无需主动调用工具即可回忆

### 3. Swarm 多代理协作
- 同一仓库可启动多个代理，自动由服务器协调
- 代理间实时感知文件变更，自动解决冲突
- 支持 DM、广播、组播消息
- 代理可自主生成子代理团队，自动管理完成状态
- 支持 headed 和 headless 两种模式

### 4. 多 Provider 支持
- **原生支持**：Claude、OpenAI/ChatGPT、Gemini、GitHub Copilot、Azure OpenAI
- **聚合/兼容**：OpenRouter、OpenAI-compatible
- **其他**：DeepSeek、Fireworks、Groq、Ollama、LM Studio 等 30+ 提供商
- **OAuth 订阅登录**：直接用已有订阅，无需额外 API Key
- **多账户切换**：用完一个订阅的额度，一键切换到另一个

### 5. Self-Dev 自我开发模式
- 代理可以修改 jcode 自身源码
- 编辑、构建、测试、重载二进制文件全自动
- 专为自我迭代优化
- 推荐使用前沿模型（GPT 5.5 等）

### 6. 浏览器自动化
- 内置 Firefox Agent Bridge
- 支持 open、click、type、screenshot、eval 等 16+ 操作
- 一条命令设置：`jcode browser setup`

### 7. 高级 UI 功能
- 侧面板：文件查看、diff、Mermaid 图表渲染
- 信息小部件：利用屏幕负空间显示上下文信息
- 自定义 Mermaid 渲染器（1800 倍提速，无浏览器依赖）
- 左对齐/居中模式切换
- 自定义终端 Handterm 实现原生滚动

### 8. 会话恢复
- 可从 Claude Code、Codex CLI、OpenCode、pi 等其他框架恢复会话
- 跨框架兼容，不会因工具切换丢失工作进度

---

## 技术架构

```
┌─────────────────────────────────────────────┐
│                  jcode TUI                   │
│  ┌─────────┐  ┌──────────┐  ┌────────────┐  │
│  │  Chat    │  │ Side Panel│  │ Info Widget│  │
│  │  View    │  │ (Files/   │  │ (Context)  │  │
│  │          │  │  Diff/    │  │            │  │
│  │          │  │  Diagram) │  │            │  │
│  └────┬─────┘  └─────┬────┘  └─────┬──────┘  │
│       │              │              │          │
│  ┌────▼──────────────▼──────────────▼──────┐  │
│  │           Agent Orchestrator             │  │
│  │  ┌──────────┐ ┌──────┐ ┌─────────────┐  │  │
│  │  │  Memory   │ │ Tools│ │   Skills    │  │  │
│  │  │  System   │ │      │ │ (Semantic)  │  │  │
│  │  │(Embedding)│ │      │ │             │  │  │
│  │  └──────────┘ └──────┘ └─────────────┘  │  │
│  └─────────────────┬───────────────────────┘  │
│                    │                          │
│  ┌─────────────────▼───────────────────────┐  │
│  │           Provider Layer                 │  │
│  │  Claude │ OpenAI │ Gemini │ Copilot │..│  │
│  └─────────────────────────────────────────┘  │
│                                               │
│  ┌─────────────────────────────────────────┐  │
│  │           Server / Swarm                 │  │
│  │  Agent A ←→ Agent B ←→ Agent C           │  │
│  │  (File conflict detection & resolution)  │  │
│  └─────────────────────────────────────────┘  │
└─────────────────────────────────────────────┘
```

---

## 技术栈

| 层面 | 技术 |
|------|------|
| 核心语言 | Rust |
| 终端 UI | 自研 TUI（Handterm） |
| 向量嵌入 | 本地 embedding（可关闭） |
| 图表渲染 | 自研 mermaid-rs-renderer |
| 代理协调 | Server/Client 架构 |
| 包管理 | cargo |
| 平台 | Linux x86_64/aarch64, macOS Apple Silicon/Intel, Windows x86_64 |

---

## 应用场景

1. **日常编码辅助**：替代 Claude Code / Codex CLI 作为主力编码工具
2. **大型项目多代理协作**：多个 AI 代理同时工作在同一代码库，自动协调
3. **长期项目记忆管理**：跨会话保持项目上下文，无需重复解释
4. **订阅用户省钱**：用已有的 Claude/ChatGPT 订阅，无需额外 API 费用
5. **自部署模型**：通过 vLLM/Ollama 运行本地模型，完全离线使用
6. **自动化 CI/CD**：无头模式运行编码任务，集成到流水线

---

## 为什么火（Trending 原因）

1. **性能碾压竞品**：公开的基准测试显示，jcode 在启动速度（245 倍领先）和内存占用（14 倍领先）上全面超越 Claude Code、Cursor、Copilot CLI 等主流工具，这个对比极具冲击力

2. **AI Agent 生态爆发**：2026 年是 AI Agent 大年，市场对高性能、可定制的代理框架需求激增

3. **独创功能吸引眼球**：
   - Self-Dev 模式（AI 修改自身代码）极其新颖
   - Swarm 多代理协作解决了真实痛点
   - 智能记忆系统无需手动管理

4. **Rust 技术选型**：开发者社区对 Rust 的热情持续高涨，用 Rust 写的终端工具天然自带流量

5. **30+ Provider 兼容**：支持几乎所有主流 AI 模型，包括订阅制 OAuth 登录，降低了使用门槛

6. **社区传播**：YouTube 视频、Medium 文章、Reddit 讨论多平台传播

---

## 同类项目对比

| 特性 | jcode | Claude Code | Cursor | Codex CLI | OpenCode |
|------|-------|-------------|--------|-----------|----------|
| 语言 | Rust | Node.js | Electron | Node.js | Go |
| 启动速度 | 14ms | 3.4s | 1.9s | 880ms | 1.0s |
| 单会话内存 | 28MB | 387MB | 215MB | 140MB | 372MB |
| 多会话支持 | Swarm | 否 | 否 | 否 | 否 |
| 记忆系统 | 语义向量 | 基础 | 否 | 否 | 否 |
| 自我开发 | 是 | 否 | 否 | 否 | 否 |
| Provider 数量 | 30+ | 1 (Anthropic) | 3-5 | 1 (OpenAI) | 多个 |
| 开源 | 是 | 部分 | 否 | 是 | 是 |
| 浏览器自动化 | 内置 | 否 | 否 | 否 | 否 |

---

## 适合谁使用

- **高级开发者**：追求极致性能和多会话并行工作流
- **AI Agent 开发者**：需要一个高性能的代理底盘来构建自己的工作流
- **团队协作场景**：多人同时操作同一代码库，需要自动冲突解决
- **多模型用户**：同时使用 Claude、GPT、Gemini 等多个模型的开发者
- **终端重度用户**：偏好 TUI 界面而非 IDE 插件
- **自托管/隐私敏感用户**：支持 Ollama、LM Studio 等本地模型

---

## 快速上手指南

### 安装

```bash
# macOS & Linux（推荐）
curl -fsSL https://raw.githubusercontent.com/1jehuang/jcode/master/scripts/install.sh | bash

# macOS Homebrew
brew tap 1jehuang/jcode
brew install jcode

# Windows PowerShell
irm https://raw.githubusercontent.com/1jehuang/jcode/master/scripts/install.ps1 | iex

# 从源码编译
git clone https://github.com/1jehuang/jcode.git
cd jcode && cargo build --release
```

### 登录 Provider

```bash
# Claude
jcode login --provider claude

# OpenAI
jcode login --provider openai

# GitHub Copilot
jcode login --provider copilot

# Gemini
jcode login --provider gemini
```

### 使用

```bash
# 启动 TUI
jcode

# 非交互式运行
jcode run "say hello"

# 恢复之前的会话
jcode --resume fox

# 启动后台服务器，多个客户端连接
jcode serve
jcode connect

# 语音输入
jcode dictate
```

---

## 总结

jcode 是 2026 年 AI 编程工具领域的一个黑马项目。它不是简单的又一款 AI 编程助手，而是从底层架构出发重新定义了"编程代理框架"应该是什么样子。凭借 Rust 的极致性能、独创的 Swarm 协作机制、智能记忆系统和 Self-Dev 能力，它在 Claude Code、Cursor 等成熟竞品面前展现了独特的技术优势。对于追求高性能和深度定制的开发者来说，jcode 值得密切关注。

---

*分析日期：2026-05-05 | 数据来源：[GitHub](https://github.com/1jehuang/jcode)*
