# free-llm-api-resources - 免费LLM API资源大全

> GitHub Trending Deep Analysis | 2026-05-07

## 基本信息

| 项目 | 详情 |
|------|------|
| 仓库 | [cheahjs/free-llm-api-resources](https://github.com/cheahjs/free-llm-api-resources) |
| Stars | 20,212 (+344 today) |
| 类型 | 社区维护的精选资源列表（Markdown 文档） |
| 分类 | 13 个永久免费平台 + 13 个试用额度平台 |
| 可用模型 | 200+ |
| 更新方式 | 社区 Issues/PRs 持续更新 |

## 综合评分: 8.3 / 10

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 7.0 | 精选列表而非技术创新，但概念和执行都极为到位 |
| 代码质量 | 7.5 | 纯 Markdown 项目，结构清晰，信息组织良好 |
| 实用性 | 9.5 | 极致实用——直接解决"去哪找免费 LLM API"的高频需求 |
| 文档完善度 | 9.0 | README 即全部内容，精确到 RPM/TPM 配额 |
| 社区活跃度 | 8.5 | 20K+ Stars，多个播客/视频/文章报道，社区持续贡献 |

## 项目概览

free-llm-api-resources 是一个由社区维护的精选列表，汇总了所有提供免费 API 访问或免费额度的 LLM 推理服务。不同于其他模糊的"免费资源合集"，这个项目精确列出了每个服务的请求速率限制（RPM）、每日/每月配额、Token 上限和可用模型清单。

### 核心原则

- **"请勿滥用"** — README 第一句话就是"Please don't abuse these services, else we might lose them"
- **合法合规** — 明确排除不合法服务（如逆向工程他人聊天机器人的平台）
- **精确信息** — 每个平台都列出具体配额数字，而非模糊描述

### 核心数据

- **13 个永久免费平台**: OpenRouter, Google AI Studio, NVIDIA NIM, Mistral (La Plateforme + Codestral), HuggingFace, Vercel AI Gateway, OpenCode Zen, Cerebras, Groq, Cohere, GitHub Models, Cloudflare Workers AI
- **13 个试用额度平台**: Fireworks ($1), Baseten ($30), Nebius ($1), Novita ($0.5/年), AI21 ($10/3月), Upstage ($10/3月), NLP Cloud ($15), Alibaba Cloud (1M tokens), Modal ($5/月), Inference.net ($1), Hyperbolic ($1), SambaNova ($5/3月), Scaleway (1M tokens)
- **200+ 可用模型**: GPT-OSS-120B, Gemini 3 Flash, Llama 4 Scout/Maverick, DeepSeek R1/V3, Qwen3 Coder, Kimi K2.5/K2.6, Nemotron 系列等

## 重点平台

| 平台 | 配额 | 亮点模型 |
|------|------|---------|
| **Google AI Studio** | 250K tokens/min, 14,400 req/day | Gemini 3 Flash, Gemma 3 系列 |
| **Mistral La Plateforme** | 1 req/sec, 500K tokens/min, 1B tokens/月 | 全部 Mistral 开源+专有模型 |
| **Cerebras** | 30 req/min, 60K tokens/min | GPT-OSS-120B, Llama 3.1 8B（极速推理） |
| **OpenRouter** | 20 req/min, 50 req/day | 数十个免费模型，多模型网关 |
| **Groq** | 14,400 req/day, 30K tokens/min | Llama 4 Scout, Qwen3-32B（LPU 极速） |
| **Cohere** | 20 req/min, 1,000 req/月 | Command A 全系列, Aya Expanse |
| **Cloudflare Workers AI** | 10,000 neurons/day | 60+ 模型，含 Kimi K2.5/K2.6 |
| **GitHub Models** | 依赖 Copilot 订阅 | GPT-5, o4-mini, Grok 3, Llama 4 |

## 热门原因

1. **LLM API 费用是开发者头号痛点** — 个人开发者和初创团队最大的成本之一就是 API 费用，这份列表直接解决了"去哪里找免费 API"的高频需求
2. **精确到每分钟的配额信息** — 每个平台都列出 RPM、每日配额、Token 上限和可用模型，开发者可以直接对比
3. **社区驱动 + 持续更新** — LLM 市场变化极快，通过 GitHub Issues/PRs 持续更新保证时效性
4. **"No Budget, No Problem" 时代宣言** — 2026 年完全可以基于免费 API 进行原型开发、测试甚至低流量生产
5. **明确排除不合法服务** — 为开发者提供法律安全感
6. **覆盖面广** — 26 个平台涵盖几乎所有主流免费 LLM 服务

## 竞品对比

| 项目 | 平台数 | 配额精度 | 更新频率 | 合法性筛选 |
|------|--------|---------|---------|-----------|
| **free-llm-api-resources** | 26 个 | 精确到 RPM/TPM | 持续社区更新 | 明确排除不合规 |
| awesome-free-ai-tools | 较广泛 | 概括性描述 | 不定期 | 未明确 |
| 博客文章 | 10-15 个 | 发布时快照 | 一次性 | 未明确 |
| Reddit/社区帖子 | 不固定 | 用户主观经验 | 不定期 | 无筛选 |

**关键差异**: 精确性和时效性是核心优势。精确到 RPM/TPM 的配额信息 + 持续社区更新 + 明确排除不合法服务的态度，使其成为开发者最值得信赖的免费 LLM API 参考。

## 应用场景

- **原型开发** — 用免费 API 快速验证 LLM 应用想法，零前期投入
- **学习与研究** — 学生和研究者零成本学习 LLM API 调用和 Prompt 工程
- **AI Side Project** — 个人项目、Hackathon、周末项目，免费 API 撑起 MVP
- **多模型对比** — 在多个平台间切换，对比不同模型表现
- **低流量生产** — 部分平台配额足够支撑低流量生产环境
- **CI/CD 测试** — 自动化测试管线中的 LLM 集成测试

## 快速开始

### 以 Google AI Studio 为例

```python
# 1. 访问 aistudio.google.com 获取免费 API Key
# 2. 安装 SDK
pip install google-genai

# 3. 调用 Gemini 3 Flash（免费，250K tokens/min）
from google import genai
client = genai.Client(api_key="your-free-api-key")
response = client.models.generate_content(
    model="gemini-3-flash",
    contents="Hello, world!"
)
```

### 以 OpenRouter 为例（多模型网关）

```python
# 兼容 OpenAI SDK
from openai import OpenAI

client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key="your-openrouter-key",
)

# 免费调用 Llama 3.3 70B
response = client.chat.completions.create(
    model="meta-llama/llama-3.3-70b-instruct:free",
    messages=[{"role": "user", "content": "Explain quantum computing"}]
)
```

---

🤖 由 AI 深度分析生成 | Powered by Claude Code