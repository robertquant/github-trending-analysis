# Alishahryar1/free-claude-code 深度分析

> 让 Claude Code 白嫖的终极代理 — 通过 NVIDIA NIM、Kimi、DeepSeek 等免费模型驱动 Claude Code

| 信息 | 详情 |
|------|------|
| 项目 | [Alishahryar1/free-claude-code](https://github.com/Alishahryar1/free-claude-code) |
| Stars | 13,200+ |
| 语言 | Python 3.14 |
| 框架 | FastAPI + Uvicorn |
| 协议 | MIT License |
| Trending | GitHub 日榜 #1, 周榜 #2 |

## 项目简介与核心功能

**Free Claude Code** 是一个轻量级本地代理服务器，拦截 Claude Code 发出的 Anthropic API 请求并路由到 **10+ 种替代 Provider**（包括免费的 NVIDIA NIM、Kimi、DeepSeek、OpenRouter，以及本地模型 Ollama、LM Studio、llama.cpp），从而实现免费或低成本使用 Claude Code。

### 核心功能

- **即插即用代理** — 通过环境变量接入，无需修改 Claude Code
- **10+ Provider 后端** — NVIDIA NIM、Kimi、Wafer、OpenRouter、DeepSeek、LM Studio、llama.cpp、Ollama、OpenCode Zen、Z.ai
- **分层模型路由** — Opus/Sonnet/Haiku 流量可分别路由到不同 Provider
- **原生 Model Picker** — 支持 Claude Code 的 `/model` 选择器
- **流式输出 & Tool Use** — 完整支持 streaming、工具调用、thinking blocks
- **Discord/Telegram Bot** — 远程使用 Claude Code，支持语音输入
- **VS Code / JetBrains 集成** — 原生支持主流 IDE
- **本地 Admin UI** — 可视化配置管理界面

## 技术架构与特点

### 架构流程

```
Claude Code CLI / VSCode / JetBrains
        ↓  (ANTHROPIC_BASE_URL=http://localhost:8082)
+-------------------+
|   Free CC Proxy   |  ← FastAPI + Uvicorn (Python 3.14)
|   /v1/messages    |
|   /v1/models      |
|  Model Router     |  → Opus  → Provider A
|  Protocol Trans.  |  → Sonnet → Provider B
|  Request Optim.   |  → Haiku  → Provider C
+-------------------+
        ↓
NVIDIA NIM / Kimi / DeepSeek / OpenRouter /
Ollama / LM Studio / llama.cpp / Z.ai ...
```

### 技术亮点

- **Python 3.14** — 采用最新 Python 版本和现代语法特性
- **FastAPI ASGI** — 高性能异步框架，原生 SSE 流式响应
- **协议转换** — Anthropic Messages API ↔ OpenAI Chat API 无缝翻译
- **请求优化** — 简单探针请求本地应答，节省配额和延迟
- **Thinking Block 规范化** — 正确处理各 Provider 的推理块格式差异
- **插件式架构** — `OpenAIChatTransport` / `AnthropicMessagesTransport` 基类扩展

### 项目结构

```
free-claude-code/
├── server.py          # ASGI 入口
├── api/               # FastAPI 路由、服务层、优化
├── core/              # Anthropic 协议辅助和 SSE 工具
├── providers/         # Provider 传输、注册、限流
├── messaging/         # Discord/Telegram 适配器、语音
├── cli/               # CLI 入口和 Claude 进程管理
├── config/            # 设置、Provider 目录、日志
└── tests/             # 单元和契约测试
```

## 支持的 Provider

| Provider | 费用 | 代表模型 | 协议 |
|----------|------|----------|------|
| NVIDIA NIM | **免费** | GLM-4.7, GLM-5, Kimi-K2.5 | OpenAI Chat |
| Kimi | 免费/付费 | Kimi-K2.5 | OpenAI Chat |
| Wafer | 付费 | DeepSeek-V4-Pro, GLM-5.1 | Anthropic Messages |
| OpenRouter | 免费/付费 | Step-3.5-Flash, DeepSeek | Anthropic Messages |
| DeepSeek | 免费/低价 | DeepSeek-Chat | Anthropic Messages |
| LM Studio | **免费(本地)** | 任意本地模型 | Anthropic Messages |
| llama.cpp | **免费(本地)** | 任意 GGUF 模型 | Anthropic Messages |
| Ollama | **免费(本地)** | Llama3.1 等 | Anthropic Messages |
| OpenCode Zen | 免费/付费 | GPT-5.3-Codex, Claude Sonnet 4 | OpenAI Chat |
| Z.ai | 付费 | GLM-5.1, GLM-5-Turbo | OpenAI Chat |

## 应用场景

1. **个人开发者体验 Claude Code** — 无需付费即可完整体验
2. **本地模型开发** — 通过 Ollama/LM Studio 使用本地模型进行 AI 编程
3. **多模型混搭** — 不同层级任务使用不同 Provider，优化成本
4. **远程协作编程** — 通过 Discord/Telegram 远程控制 Claude Code
5. **成本优化** — 企业场景替代 Anthropic 直连降低成本
6. **模型评估** — 在 Claude Code 环境中对比不同模型编程能力

## 为什么火 (Trending 原因)

1. **直击痛点** — Claude Code 付费门槛高，该项目完美解决"想用不想花钱"的需求
2. **时机绝佳** — NVIDIA NIM 提供免费 API（~40 req/min），配合 Claude Code 热度
3. **社交传播** — Instagram、YouTube、Reddit、LinkedIn、CSDN 全平台传播
4. **工程质量** — Python 3.14 + FastAPI，结构清晰，Admin UI 降低使用门槛
5. **生态丰富** — 10+ Provider、多端支持（CLI/VSCode/JetBrains/Discord/Telegram）
6. **爆发增长** — 一周涨星 7,800+，登顶 GitHub Trending

## 同类项目对比

| 项目 | 定位 | Provider 数 | Admin UI | 消息平台 | IDE 集成 |
|------|------|-------------|----------|----------|----------|
| **free-claude-code** | Claude Code 专用代理 | 10+ | ✔ | Discord/Telegram | CLI/VSCode/JetBrains |
| LiteLLM | 通用 LLM 代理 | 100+ | ✔ | ✘ | 无专用集成 |
| OpenRouter | 云端 LLM 网关 | 200+ | N/A(云端) | ✘ | 需第三方桥接 |
| free-llm-api-resources | 资源列表 | N/A | ✘ | ✘ | ✘ |

**free-claude-code 的差异化优势**：专为 Claude Code 优化，开箱即用，不需要了解底层协议。LiteLLM 更通用但配置复杂；OpenRouter 是商业服务。

## 适合谁使用

### ✔ 推荐
- 想体验 Claude Code 但不想付费的个人开发者
- 有本地 GPU 想用 Ollama 跑模型的人
- 需要多模型 A/B 测试的 AI 工程师
- 想通过 Discord 远程编程的极客
- 学习 API 代理和协议转换的开发者

### ⚠ 注意
- 代理经手所有请求，敏感项目需评估安全风险
- 替代模型的编程能力可能与 Anthropic 原生模型有差距
- NVIDIA NIM 免费额度有速率限制（~40 req/min）

## 快速上手

### 1. 安装 Claude Code
```bash
npm install -g @anthropic-ai/claude-code
```

### 2. 安装运行时
```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
uv self update
uv python install 3.14
```

### 3. 获取 NVIDIA NIM API Key（免费）
访问 `build.nvidia.com/settings/api-keys` 创建

### 4. 安装并启动代理
```bash
uv tool install --force git+https://github.com/Alishahryar1/free-claude-code.git
fcc-server
```

### 5. 配置 Admin UI
打开 `http://127.0.0.1:8082/admin`，粘贴 API Key → Validate → Apply

### 6. 启动 Claude Code
```bash
fcc-claude
```

默认使用 `nvidia_nim/z-ai/glm4.7` 模型，可在 Admin UI 中切换。

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 8.5/10 | 巧妙的协议转换 + 分层路由设计，Admin UI 和消息平台集成增加创新点 |
| 代码质量 | 8.0/10 | 现代 Python 实践，有完整的测试和类型检查，插件式架构清晰 |
| 实用性 | 9.5/10 | 直接解决开发者痛点，免费使用 Claude Code 的最简路径 |
| 文档完善度 | 9.0/10 | README 详尽，10 个 Provider 各有说明，架构图清晰 |
| 社区活跃度 | 8.5/10 | 13k+ Stars，社交媒体广泛传播，持续更新 |

**综合得分: 8.7 / 10**

---

*Generated on 2026-05-20 | GitHub Trending Daily Analysis*
