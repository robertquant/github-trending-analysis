# Forge - Self-Hosted LLM Tool-Calling 的可靠性层

> **antoinezambelli/forge** | 1,470+ Stars | MIT License | Python 3.12+

## 核心亮点

**8B 参数本地模型，53% → 99% 准确率** — Forge 通过 Guardrails 机制（救援解析、重试引导、步骤强制）和上下文管理（VRAM 感知预算、分层压缩），将一个 8B 本地模型在多步 Agentic 工作流基准测试中的表现从 53% 提升到 99%，无需任何微调。

- **Agentic 任务准确率提升**: 53% → 99%
- **目标模型参数量**: 8B
- **最佳配置综合得分**: 86.5%（26 场景评测套件）
- **学术发表**: ACM CAIS 2026

## 项目简介

Forge 是一个 Python 框架（PyPI 包名 `forge-guardrails`），专门为**自托管本地 LLM** 的工具调用（Tool-Calling）和多步 Agentic 工作流提供可靠性保障。

在本地模型上构建 AI Agent 是当今热门趋势，但小模型（如 8B 参数量）在多步工具调用任务中经常出错——格式错误、跳过必要步骤、生成无效参数。Forge 通过一套可组合的 Guardrails 中间件解决这些问题，让小模型也能胜任生产级 Agent 任务。

项目由 **Antoine Zambelli**（德州仪器 AI 总监）创建，附带论文已发表于 **ACM CAIS 2026** 会议。

## 三种使用方式

| 方式 | 说明 | 适用场景 |
|------|------|----------|
| **WorkflowRunner** | 定义工具、选择后端、运行结构化 Agent 循环。Forge 管理完整生命周期 | 直接基于 Forge 构建 Agent 应用 |
| **Guardrails 中间件** | 在自有的编排循环中使用 Forge 的可靠性栈 | 已有编排框架，仅需 Guardrails 能力 |
| **Proxy Server** | OpenAI 兼容的代理服务器，透明应用 Guardrails | opencode、Continue、aider 等第三方客户端 |

## 技术架构与特点

### Guardrails 机制
- **响应验证器（ResponseValidator）**：验证模型输出的工具调用格式和参数有效性
- **救援解析（Rescue Parsing）**：自动修复格式错误的工具调用，而非直接丢弃
- **重试引导（Retry Nudges）**：逐步升级的提示，引导模型纠正错误行为
- **步骤强制（StepEnforcer）**：确保 Agent 执行完所有必要步骤

### 上下文管理
- **VRAM 感知预算**：根据硬件自动分配上下文窗口大小
- **分层压缩（TieredCompact）**：智能压缩历史消息，保留关键信息
- **滑动窗口（SlidingWindow）**：简单的滑动窗口策略

### 多后端支持

| 后端 | 优势 | 原生 Function Calling |
|------|------|----------------------|
| Ollama | 最易上手，内置模型管理 | 支持 |
| llama-server | 最佳性能，完全控制 | 支持（需 --jinja） |
| Llamafile | 单二进制，零依赖 | 不支持（Prompt注入） |
| Anthropic | 前沿基线，混合工作流 | 支持 |

### 其他特性
- **SlotWorker**：为多 Agent 架构提供优先级队列式的 GPU 槽位共享，支持自动抢占
- **合成 respond 工具**：Proxy 模式自动注入 `respond` 工具，让小模型始终在工具调用模式下工作

## 快速上手

### 安装

```bash
# 核心安装
pip install forge-guardrails

# 加 Anthropic 客户端
pip install "forge-guardrails[anthropic]"
```

### 最小工作流示例

```python
import asyncio
from pydantic import BaseModel, Field
from forge import (
    Workflow, ToolDef, ToolSpec,
    WorkflowRunner, OllamaClient,
    ContextManager, TieredCompact,
)

def get_weather(city: str) -> str:
    return f"72°F and sunny in {city}"

class GetWeatherParams(BaseModel):
    city: str = Field(description="City name")

workflow = Workflow(
    name="weather",
    description="Look up weather for a city.",
    tools={
        "get_weather": ToolDef(
            spec=ToolSpec(
                name="get_weather",
                description="Get current weather",
                parameters=GetWeatherParams,
            ),
            callable=get_weather,
        ),
    },
    required_steps=[],
    terminal_tool="get_weather",
    system_prompt_template="You are a helpful assistant.",
)

async def main():
    client = OllamaClient(model="ministral-3:8b-instruct-2512-q4_K_M")
    ctx = ContextManager(strategy=TieredCompact(keep_recent=2), budget_tokens=8192)
    runner = WorkflowRunner(client=client, context_manager=ctx)
    await runner.run(workflow, "What's the weather in Paris?")

asyncio.run(main())
```

### Proxy 模式（零代码集成）

```bash
# 外部模式 — 你管理 llama-server，Forge 代理它
python -m forge.proxy --backend-url http://localhost:8080 --port 8081

# 托管模式 — Forge 启动 llama-server 和代理
python -m forge.proxy --backend llamaserver --gguf path/to/model.gguf --port 8081
```

## 为什么火（Trending 原因）

1. **突破性成果**：8B 模型 + Guardrails 达到 99% 准确率。"前沿模型无 Guardrails 输给带 Guardrails 的小模型，差距高达 50%"
2. **学术背书**：论文被 ACM CAIS 2026 接收并展示，提供了严谨的技术验证
3. **解决真实痛点**：本地模型做 Agent 时工具调用不稳定是开发者最大的痛点之一
4. **Hacker News 爆火**：667+ 点赞、240+ 评论，登上首页引发广泛讨论
5. **时机精准**：在 Local LLM 和 AI Agent 两大热点交汇处
6. **零微调方案**：不需要训练或微调模型，纯工程方法实现性能飞跃

## 同类项目对比

| 项目 | 定位 | 自托管 | Guardrails | 工具调用 |
|------|------|--------|------------|----------|
| **Forge** | 自托管 LLM 工具调用可靠性层 | 核心优势 | 深度内置 | 核心功能 |
| LangChain/LangGraph | 通用 Agent 编排框架 | 支持 | 基础 | 支持 |
| LlamaIndex | RAG + 数据索引 | 支持 | 有限 | 支持 |
| Guardrails AI | 通用 LLM 输入输出验证 | 支持 | 核心功能 | 不专注 |
| CrewAI | 多 Agent 协作 | 部分 | 基础 | 支持 |
| OpenAI Agents SDK | 云端 Agent 框架 | 不支持 | 内置 | 核心功能 |

**核心差异**：Forge 不是又一个 Agent 框架，而是专注于解决"小模型工具调用不可靠"这一具体问题的可靠性中间件。它可以与现有编排框架配合使用，也可以独立运行。

## 应用场景

- **本地化 AI Agent**：在无网络或数据隐私要求下，用 8B 模型运行可靠的多步 Agent 任务
- **边缘部署**：树莓派、Jetson 等设备上的 Agent 推理
- **成本优化**：用免费本地模型替代付费 API，Forge 弥补可靠性差距
- **IDE 集成**：通过 Proxy 模式让 Continue、aider 等工具使用本地模型时更可靠
- **多 Agent 架构**：用 SlotWorker 在单 GPU 上运行多个专业 Agent
- **语音助手 / CLI 聊天**：长对话会话中的可靠工具调用

## 适合谁使用

| 用户类型 | 适合度 | 原因 |
|----------|--------|------|
| 本地 LLM 开发者 | 强烈推荐 | 直接解决本地模型工具调用不稳定的痛点 |
| AI Agent 构建者 | 强烈推荐 | 作为可靠性中间件嵌入现有 Agent 系统 |
| 边缘/IoT 开发者 | 推荐 | VRAM 感知上下文管理适合资源受限环境 |
| IDE 工具用户 | 推荐 | Proxy 模式零代码集成，即插即用 |
| 云端 API 用户 | 一般 | 已有原生 Function Calling 的模型收益有限 |

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 9.2/10 | 用纯工程方法（非微调）实现小模型 Agent 可靠性飞跃，论文发表于 ACM |
| 代码质量 | 9.0/10 | 865 个单元测试，Codecov 覆盖，结构清晰，模块化设计 |
| 实用性 | 8.8/10 | 三种使用模式覆盖不同场景，但依赖本地 LLM 硬件 |
| 文档完善度 | 9.1/10 | 完整的 User Guide、Model Guide、Backend Setup、Eval Guide、Architecture |
| 社区活跃度 | 8.2/10 | HN 爆火，但项目较新，长期贡献者还需观察 |

**综合评分：9.1 / 10**

## 项目信息

| 项目 | 详情 |
|------|------|
| 仓库地址 | [github.com/antoinezambelli/forge](https://github.com/antoinezambelli/forge) |
| PyPI 包 | `forge-guardrails` (v0.4.2) |
| 许可证 | MIT |
| 作者 | Antoine Zambelli (德州仪器 AI 总监) |
| 语言 | Python 3.12+ |
| 论文 | ACM CAIS 2026 — DOI: 10.1145/3786335.3813193 |
| 推荐模型 | Ministral-3 8B Instruct Q8 (llama-server) |
| 测试覆盖 | 865 单元测试 + 26 场景评估套件 |

---

*分析日期：2026-05-22 | 由 AI 自动分析生成 | Powered by Claude Code*
