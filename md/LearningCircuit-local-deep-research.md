# Local Deep Research - 本地AI深度研究助手

> GitHub Trending Deep Analysis | 2026-05-07

## 📊 综合评分：8.5 / 10

本地 AI 研究工具的标杆之作。凭借 ~95% 的 SimpleQA 准确率、零遥测的隐私设计、以及对几乎所有主流 LLM 的原生支持，成为本地化 AI 研究工具领域的一颗新星。

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | **9.0** | 本地优先 AI 研究 + MCP 集成 + 知识库复利 + per-user 加密数据库 |
| 代码质量 | **8.0** | Docker 安全链（Cosign/SLSA/SBOM），但代码库复杂度较高 |
| 实用性 | **9.0** | 研究自动化 + 知识库构建 + 学术搜索 + 20+ 策略覆盖全场景 |
| 文档完善度 | **9.0** | 极其详尽的 README，含架构图、API 示例、安全策略、基准数据 |
| 社区活跃度 | **8.0** | 5.4K stars 快速增长，多语言社区覆盖，但项目较新 |

---

## 🎯 项目概览

**Local Deep Research（LDR）** 是一个完全本地运行的 AI 研究助手，由 LearningCircuit 团队开发。核心理念：**你拥有自己的数据，你看到它如何工作**。

用户用自然语言提出复杂问题，LDR 自动搜索网络、学术论文和个人文档库，综合生成带引用的研究报告。支持 20+ 研究策略，从快速摘要（30秒-3分钟）到深度分析报告（10-30分钟）。

- **Stars**: 5,420 (+197 today)
- **Language**: Python
- **License**: MIT
- **安装**: pip / Docker / Docker Compose
- **PyPI**: local-deep-research

### 🔑 核心数据

- **SimpleQA 准确率**: ~95%（GPT-4.1-mini + SearXNG）
- **搜索引擎**: 10+ 免费/付费引擎
- **LLM 支持**: Ollama、LM Studio、llama.cpp、OpenAI、Anthropic、Google、100+ via OpenRouter
- **加密**: AES-256 per-user SQLCipher
- **遥测**: 零追踪
- **MCP 工具**: 8 个（5 研究 + 3 发现）

---

## ✨ 核心特性

### 🔍 多模式研究
快速摘要（30秒-3分钟）、深度分析、正式报告生成、个人文档搜索，20+ 研究策略灵活选择。新增 LangGraph Agent 模式——LLM 自行决定搜索什么、使用哪个专业引擎，以及何时综合结论。

### 📚 知识库构建
每次研究的来源自动下载到加密库中，提取文本、建立索引、支持搜索。研究不再是一次性的，而是持续积累的个人知识资产。"研究 → 下载 → 索引 → 再研究"的闭环。

### 🔒 零遥测隐私
不收集、不传输、不存储任何用户数据。无分析 SDK、无回拨、无崩溃报告。网络请求仅由用户主动发起。

### 🔌 MCP 集成
通过 Model Context Protocol 与 Claude Desktop/Code 深度集成。8 个 MCP 工具：

| 工具 | 描述 | 耗时 | LLM 成本 |
|------|------|------|---------|
| `search` | 特定引擎原始搜索 | 5-30s | 无 |
| `quick_research` | 快速研究摘要 | 1-5 min | 是 |
| `detailed_research` | 全面分析 | 5-15 min | 是 |
| `generate_report` | 完整 Markdown 报告 | 10-30 min | 是 |
| `analyze_documents` | 搜索本地集合 | 30s-2 min | 是 |
| `list_search_engines` | 列出可用引擎 | 即时 | 无 |
| `list_strategies` | 列出研究策略 | 即时 | 无 |
| `get_configuration` | 获取当前配置 | 即时 | 无 |

### 📊 期刊质量系统
自动评估期刊声誉，覆盖 212K+ 索引来源，包含掠夺性期刊检测。基于 OpenAlex（CC0）、DOAJ（CC0）、Stop Predatory Journals（MIT）。

### 📰 研究订阅
订阅特定主题，定期接收 AI 驱动的研究摘要。支持日/周/自定义频率，智能过滤和总结。

### 🛡️ 供应链安全
Docker 镜像使用 Cosign 签名，包含 SLSA 来源证明和 SBOM。可验证的完整供应链安全链。

---

## 🛡️ 安全架构

### 数据层
- SQLCipher AES-256 per-user 加密数据库
- 无密码恢复 = 零知识架构
- 会话级凭证生命周期管理，核心转储排除

### 供应链层
- Docker 镜像 Cosign 签名
- SLSA 来源证明（provenance attestations）
- SBOM 物料清单

### 网络层
- 零遥测、零分析、零追踪
- 所有网络请求仅由用户主动发起
- 完全本地部署时可离线运行

### 透明度
- 扫描抑制有文档化理由
- 公开安全策略和审查流程

---

## 📈 性能基准

### SimpleQA 基准测试

| 配置 | 准确率 | 备注 |
|------|--------|------|
| gpt-4.1-mini + SearXNG + focused_iteration | 90-95% | Limited sample size |
| gpt-4.1-mini + Tavily + focused_iteration | 90-95% | Limited sample size |
| gemini-2.0-flash-001 + SearXNG | 82% | Single test run |

社区基准排行榜：
- **GitHub**: LearningCircuit/ldr-benchmarks — 提交结果
- **Hugging Face**: local-deep-research/ldr-benchmarks — 浏览排行榜

---

## 🔥 热门原因分析

1. **隐私优先的时代需求** — 零遥测、零追踪、本地加密架构精准击中痛点。记者、研究人员、企业敏感部门可在不泄露查询下进行深度研究。

2. **SimpleQA ~95% 准确率的硬实力** — 与 SOTA 系统相当，证明本地化不意味妥协。在 r/LocalLLaMA 引发广泛讨论。

3. **LLM 无绑定策略** — 支持所有主流 LLM，用户不被锁定在任何单一供应商。

4. **MCP 生态集成的前瞻性** — 首批提供完整 MCP Server 的研究工具，抓住 AI 工具链整合浪潮。

5. **知识复利效应** — 独特的知识库构建功能让研究自动归档来源、建立索引，形成可持续增长的个人知识资产。

6. **国际化的社区传播** — 覆盖中/日/韩/法等多语言社区。LangChain 官方 Twitter/LinkedIn 推广。Hacker News 190+ points。

---

## ⚖️ 竞品对比

| 维度 | Local Deep Research | GPT Researcher | OpenAI Deep Research | Perplexity Pro |
|------|-------------------|---------------|---------------------|---------------|
| 运行方式 | 本地 + 云端 | 云端为主 | 仅云端 | 仅云端 |
| 隐私保护 | 零遥测 · AES-256 | 基础 | 依赖 OpenAI | 依赖服务 |
| LLM 选择 | 全部主流 | 部分 | 仅 GPT | 仅自有 |
| 搜索引擎 | 10+ (含学术) | 多引擎 | Web search | 自有索引 |
| 知识库构建 | ✅ 自动积累 | ❌ | ❌ | Collections |
| MCP 支持 | ✅ 8 工具 | ❌ | ❌ | ❌ |
| 期刊质量评估 | ✅ 212K+ 来源 | ❌ | ❌ | ❌ |
| 开源 | MIT | MIT | ❌ 闭源 | ❌ 闭源 |
| 费用 | 免费（本地 LLM） | 需 API key | $200/月 | $20/月 |

---

## 💡 应用场景

- **学术研究** — 搜索 arXiv、PubMed、Semantic Scholar，自动评估期刊质量，生成带引用的学术综述
- **新闻调查** — 零追踪环境下进行敏感话题深度研究
- **企业知识管理** — 搜索公司内部文档 + 网络搜索进行竞品分析
- **AI Agent 增强研究** — 通过 MCP 让 Claude 自动执行深度研究
- **个人知识库** — 持续积累研究来源，构建可搜索的个人知识资产
- **趋势监测** — 订阅特定主题的研究摘要，定期获取最相关发展动态

---

## 🚀 快速开始

### Docker Compose（推荐）

```bash
# CPU 版本
curl -O https://raw.githubusercontent.com/LearningCircuit/local-deep-research/main/docker-compose.yml
docker compose up -d

# GPU 版本（Linux + NVIDIA）
curl -O https://raw.githubusercontent.com/LearningCircuit/local-deep-research/main/docker-compose.gpu.override.yml
docker compose -f docker-compose.yml -f docker-compose.gpu.override.yml up -d

# 访问 http://localhost:5000
```

### pip 安装

```bash
# 基础安装
pip install local-deep-research

# MCP 支持
pip install "local-deep-research[mcp]"
```

### Python API

```python
from local_deep_research.api import LDRClient, quick_query

# 一行研究
summary = quick_query("username", "password", "量子计算最新进展")
print(summary)

# 客户端模式
client = LDRClient()
client.login("username", "password")
result = client.quick_research("量子计算有哪些实际应用？")
print(result["summary"])
```

### Claude Desktop MCP 配置

```json
{
  "mcpServers": {
    "local-deep-research": {
      "command": "ldr-mcp",
      "env": {
        "LDR_LLM_PROVIDER": "openai",
        "LDR_LLM_OPENAI_API_KEY": "sk-..."
      }
    }
  }
}
```

---

## 🔗 链接

- [GitHub 仓库](https://github.com/LearningCircuit/local-deep-research)
- [PyPI](https://pypi.org/project/local-deep-research/)
- [Benchmarks](https://github.com/LearningCircuit/ldr-benchmarks)
- [HuggingFace Leaderboard](https://huggingface.co/local-deep-research/ldr-benchmarks)
- [Discord](https://discord.gg/local-deep-research)

---

📊 分析日期: 2026-05-07 | 🤖 由 AI 自动分析生成 | Powered by Claude Code