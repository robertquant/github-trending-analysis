# TradingAgents: Multi-Agents LLM Financial Trading Framework

> **TauricResearch/TradingAgents** | ⭐ 66,248 Stars | 🔥 +3,313 Today | Python | [GitHub](https://github.com/TauricResearch/TradingAgents) | [arXiv:2412.20138](https://arxiv.org/abs/2412.20138)

---

## 项目简介

TradingAgents 是由 **Tauric Research** 团队（来自 UCLA）开发的开源多智能体 LLM 金融交易框架。其核心创新在于**模拟真实交易公司的运作模式**——通过部署多个专业化的 LLM 驱动智能体（基本面分析师、情绪分析师、技术分析师、研究员、交易员和风险管理团队），让它们协作评估市场状况并做出交易决策。

项目于 2024 年 12 月发表论文（arXiv:2412.20138，作者：Yijia Xiao, Edward Sun, Di Luo, Wei Wang），目前已更新至 v0.2.4，支持 GPT-5.x、Gemini 3.x、Claude 4.x、Grok 4.x、DeepSeek、Qwen、GLM 等几乎所有主流 LLM 提供商。

---

## 核心功能

### 1. 多角色智能体团队

框架将复杂交易任务分解为专业化的角色，模拟真实交易公司：

- **基本面分析师 (Fundamentals Analyst)**：评估公司财务和业绩指标，识别内在价值和潜在风险
- **情绪分析师 (Sentiment Analyst)**：分析社交媒体和公众情绪，使用情绪评分算法判断短期市场氛围
- **新闻分析师 (News Analyst)**：监控全球新闻和宏观经济指标，解读事件对市场的影响
- **技术分析师 (Technical Analyst)**：利用 MACD、RSI 等技术指标检测交易模式并预测价格走势

### 2. 多空辩论机制 (Bull/Bear Debate)

研究员团队包含**看多 (Bullish)** 和**看空 (Bearish)** 两个角色，通过结构化辩论批判性评估分析师团队的洞察。辩论机制强制系统从正反两面评估每笔交易，平衡潜在收益与固有风险，减少认知偏差。

### 3. 交易决策与风险管理

- **交易员 (Trader Agent)**：综合分析师和研究员的报告，做出交易决策，确定交易的时机和规模
- **风险管理团队**：持续评估投资组合风险（市场波动性、流动性等），调整交易策略
- **投资组合经理 (Portfolio Manager)**：最终审批或拒绝交易提案，执行订单到模拟交易所

### 4. 持久化与恢复

- **决策日志**：自动记录每次交易决策到 `~/.tradingagents/memory/trading_memory.md`，下次分析同标的时自动注入历史经验和反思
- **检查点恢复**：基于 LangGraph 的检查点机制（SQLite），中断后可从上次成功的步骤恢复，无需从头开始

### 5. 多 LLM 提供商支持（10+ 提供商）

| 类别 | 支持的提供商 |
|------|------------|
| **国际商业 LLM** | OpenAI (GPT-5.x), Google (Gemini 3.x), Anthropic (Claude 4.x), xAI (Grok 4.x) |
| **国产 LLM** | DeepSeek, Qwen (通义千问/阿里 DashScope), GLM (智谱) |
| **聚合/本地** | OpenRouter, Ollama (本地模型) |
| **企业级** | Azure OpenAI, AWS Bedrock |

---

## 技术架构

```
┌─────────────────────────────────────────────────────────────┐
│                  TradingAgents Graph (LangGraph)             │
├──────────────────┬──────────────────┬────────────────────────┤
│                  │                  │                         │
│   Analyst Team   │  Researcher Team │    Decision Layer       │
│                  │                  │                         │
│ ┌──────────────┐ │ ┌──────────────┐ │ ┌────────────────────┐ │
│ │ Fundamentals │ │ │    Bull      │ │ │   Trader Agent     │ │
│ │  Analyst     │ │ │  Researcher  │ │ │  (综合报告决策)      │ │
│ ├──────────────┤ │ ├──────────────┤ │ ├────────────────────┤ │
│ │  Sentiment   │ │ │    Bear      │ │ │  Risk Management   │ │
│ │  Analyst     │ │ │  Researcher  │ │ │  (风险评估)          │ │
│ ├──────────────┤ │ ├──────────────┤ │ ├────────────────────┤ │
│ │    News      │ │ │  Structured  │ │ │ Portfolio Manager  │ │
│ │  Analyst     │ │ │   Debate     │ │ │  (最终决策)          │ │
│ ├──────────────┤ │ └──────────────┘ │ └────────────────────┘ │
│ │  Technical   │ │                  │           │              │
│ │  Analyst     │ │                  │           ▼              │
│ └──────────────┘ │                  │  ┌────────────────┐    │
│                  │                  │  │ Simulated      │    │
│       │          │        │         │  │  Exchange      │    │
│       ▼          │        ▼         │  │ (订单执行)      │    │
│  ┌──────────┐    │ ┌──────────┐    │  └────────────────┘    │
│  │  Market  │    │ │Decision  │    │                         │
│  │ Data API │    │ │   Log    │    │                         │
│  │(Alpha    │    │ │(Markdown)│    │                         │
│  │ Vantage) │    │ └──────────┘    │                         │
│  └──────────┘    │                 │                         │
└──────────────────┴──────────────────┴────────────────────────┘
```

### 架构特点
- **LangGraph 编排**：使用 LangGraph 作为底层编排引擎，确保灵活性和模块化
- **结构化输出**：v0.2.4 引入结构化输出 Agent（Research Manager、Trader、Portfolio Manager），决策结果标准化
- **决策持久化**：SQLite 数据库存储检查点，Markdown 文件记录决策日志
- **Docker 支持**：提供完整 Docker Compose 配置，一键部署

---

## 技术栈

| 层级 | 技术 |
|------|------|
| **语言** | Python 3.13 |
| **AI 编排** | LangGraph (工作流 + 状态管理) |
| **LLM 提供商** | OpenAI, Google, Anthropic, xAI, DeepSeek, Qwen, GLM, OpenRouter, Ollama, Azure OpenAI |
| **市场数据** | Alpha Vantage API |
| **持久化** | SQLite (检查点), Markdown (决策日志) |
| **容器化** | Docker / Docker Compose |
| **CLI** | 交互式命令行界面 |
| **本地模型** | Ollama (可选 profile) |

---

## 应用场景

1. **量化研究**：模拟真实交易公司的决策流程，研究多智能体协作对交易绩效的影响
2. **金融 AI 教育**：作为多智能体系统在金融领域应用的教科书级案例
3. **策略回测**：利用 LLM 的多维度分析能力进行交易策略回测
4. **市场监控**：集成情绪分析、新闻监控，构建实时市场监控仪表盘
5. **学术研究**：论文已发表在 arXiv，适合引用和复现
6. **AI Agent 开发学习**：学习多智能体编排、LangGraph 工作流设计、结构化输出的最佳实践

---

## 为什么火 (Trending 原因)

1. **AI + 金融热度持续高涨**：LLM 在金融领域的应用是当前最热门的研究方向之一，"模拟交易公司"的叙事比单纯"AI 交易"更具说服力
2. **学术背景加持**：来自 UCLA 研究团队，有正式 arXiv 论文支撑，学术可信度远超一般开源项目
3. **极致的模型兼容性**：支持几乎所有主流 LLM（GPT-5、Gemini 3、Claude 4、Grok 4、DeepSeek、Qwen、GLM），用户无需绑定单一厂商
4. **活跃迭代**：2026 年频繁更新（v0.2.0 → v0.2.4），持续增加新功能
5. **开箱即用**：提供 CLI、Python API、Docker 三种使用方式，上手门槛低
6. **66K+ Stars 社区效应**：庞大的社区关注度形成了正反馈
7. **社区驱动发展**：Discord 活跃讨论、贡献者持续增加

---

## 同类项目对比

| 维度 | TradingAgents | FinRobot | FinGPT | FinRL |
|------|--------------|----------|--------|-------|
| **架构** | 多智能体辩论 | 多智能体平台 | 单一 LLM 模型 | 强化学习 |
| **核心方法** | LLM + 多角色协作 | LLM + Agent 平台 | 微调金融 LLM | RL 算法 |
| **交易决策** | ✅ 完整交易决策 | 部分支持 | ❌ 侧重 NLP | ✅ RL 策略 |
| **LLM 依赖** | 10+ 提供商 | 多提供商 | 单一微调模型 | 无（纯 RL） |
| **回测表现** | 强（论文验证） | 估值强 (75%) | 有限 | 强 |
| **上手难度** | 中等 | 中等 | 低 | 高 |
| **适用场景** | 研究 & 模拟 | 金融工作流 | 金融 NLP | RL 交易策略 |
| **Stars** | **66K+** | 3K+ | 15K+ | 10K+ |
| **论文** | arXiv:2412.20138 | arXiv:2405.14767 | 有 | 有 |

**TradingAgents 优势**：最完整的多智能体交易框架，学术验证充分，社区规模最大，模型兼容性最强。
**TradingAgents 劣势**：实际交易性能受 LLM 质量和 API 成本影响较大，依赖 Alpha Vantage 数据源，不适合直接用于实盘。

---

## 适合谁使用

- **量化研究员**：研究 LLM 在交易决策中的应用，复现论文实验
- **金融科技开发者**：构建 AI 驱动的交易系统原型，Python API 灵活集成
- **AI/ML 研究者**：多智能体系统的实际应用案例，学习 LangGraph 编排
- **金融专业学生**：理解交易决策的多维度分析流程
- **加密货币/股票爱好者**：利用 AI 辅助市场分析（仅供研究参考，非投资建议）

---

## 快速上手指南

### 安装

```bash
# 克隆仓库
git clone https://github.com/TauricResearch/TradingAgents.git
cd TradingAgents

# 创建虚拟环境
conda create -n tradingagents python=3.13
conda activate tradingagents

# 安装依赖
pip install -e .
```

### Docker 方式

```bash
cp .env.example ..env  # 填入你的 API Keys
docker compose run --rm tradingagents

# 使用本地 Ollama 模型
docker compose --profile ollama run --rm tradingagents-ollama
```

### 配置 API Keys

```bash
# 至少配置一个 LLM 提供商 + 市场数据
export OPENAI_API_KEY="sk-..."
export ALPHA_VANTAGE_API_KEY="..."

# 可选：其他提供商
export ANTHROPIC_API_KEY="..."       # Claude
export GOOGLE_API_KEY="..."          # Gemini
export DEEPSEEK_API_KEY="..."        # DeepSeek
export DASHSCOPE_API_KEY="..."       # 通义千问
export ZHIPU_API_KEY="..."           # 智谱 GLM
export XAI_API_KEY="..."             # Grok
export OPENROUTER_API_KEY="..."      # OpenRouter

# 企业级
cp .env.enterprise.example .env.enterprise  # Azure OpenAI / AWS Bedrock
```

### CLI 使用

```bash
# 启动交互式 CLI（选择股票、日期、LLM 提供商、研究深度等）
tradingagents

# 或从源码运行
python -m cli.main
```

### Python API

```python
from tradingagents.graph.trading_graph import TradingAgentsGraph
from tradingagents.default_config import DEFAULT_CONFIG

# 使用默认配置
ta = TradingAgentsGraph(debug=True, config=DEFAULT_CONFIG.copy())
_, decision = ta.propagate("NVDA", "2026-01-15")
print(decision)

# 自定义配置
config = DEFAULT_CONFIG.copy()
config["llm_provider"] = "anthropic"
config["deep_think_llm"] = "claude-sonnet-4-6"
config["quick_think_llm"] = "claude-haiku-4-5"
config["max_debate_rounds"] = 3

ta = TradingAgentsGraph(debug=True, config=config)
_, decision = ta.propagate("AAPL", "2026-05-01")
print(decision)
```

### 启用持久化与恢复

```bash
# CLI 方式
tradingagents analyze --checkpoint           # 启用检查点
tradingagents analyze --clear-checkpoints    # 清除所有检查点

# Python 方式
config = DEFAULT_CONFIG.copy()
config["checkpoint_enabled"] = True
ta = TradingAgentsGraph(config=config)
_, decision = ta.propagate("TSLA", "2026-03-01")
```

---

## 发展历程

| 时间 | 事件 |
|------|------|
| 2024-12 | arXiv 论文发表（2412.20138），提出多智能体交易框架概念 |
| 2025-01 | Trading-R1 技术报告发布，框架正式开源 |
| 2026-02 | v0.2.0 发布，支持 GPT-5.x / Gemini 3.x / Claude 4.x / Grok 4.x |
| 2026-03 | v0.2.2-0.2.3 连续发布：五级评分、多语言、GPT-5.4 模型支持 |
| 2026-04 | v0.2.4 发布：结构化输出、LangGraph Checkpoint、DeepSeek/Qwen/GLM 支持 |
| 2026-05 | Star 突破 66K，登顶 GitHub Trending |

---

## 综合评分

| 维度 | 评分 |
|------|:---:|
| 创新性 | 9.2 |
| 代码质量 | 8.8 |
| 实用性 | 8.2 |
| 文档完善度 | 8.5 |
| 社区活跃度 | 9.0 |
| **综合得分** | **8.7 / 10** |

---

## 注意事项

> **本框架仅用于研究目的。** 交易性能可能因多种因素而异，包括所选的骨干语言模型、模型温度、交易周期、数据质量等。**不构成任何金融、投资或交易建议。**

---

## 相关链接

- [GitHub 仓库](https://github.com/TauricResearch/TradingAgents)
- [arXiv 论文](https://arxiv.org/abs/2412.20138)
- [Tauric Research 官网](https://tauric.ai/research/tradingagents/)
- [项目官网](https://tradingagents-ai.github.io/)
- [OpenReview](https://openreview.net/forum?id=4QPrXwMQt1)
- [Discord 社区](https://discord.gg/TradingResearch)

---

*Generated on 2026-05-05 · GitHub Trending Daily Analysis*
