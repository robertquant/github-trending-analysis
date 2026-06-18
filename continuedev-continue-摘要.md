# continuedev/continue 深度分析摘要

> 开源 AI 编码 Agent ｜ Apache-2.0 ｜ CLI · VS Code · JetBrains 三端 ｜ 模型无关（BYO Model）｜ ⚠️ 已被 Cursor 收购

## 一句话定位
Continue 是最具影响力的**开源 AI 编码 Agent** 之一，以"让开发者掌控 AI、而非被 AI 自动化"为使命，把模型选择权还给开发者，并提供 CLI、VS Code 扩展、JetBrains 插件三种形态。

## 关键事实
| 维度 | 详情 |
|---|---|
| 仓库 | [github.com/continuedev/continue](https://github.com/continuedev/continue) |
| Stars | ~25,000 ⭐ |
| 协议 | Apache-2.0（商用友好） |
| 主语言 | TypeScript（核心）· Python（部分组件） |
| 模型支持 | OpenAI / Anthropic / Google / **Ollama(本地)** / **OpenRouter** —— 任意模型 |
| 重大事件 | **2025 年被 Cursor 收购**，项目处于过渡期 |

## 技术架构（核心亮点）
- **声明式 config.yaml**：统一声明模型、上下文、规则、提示词，可版本化、可团队共享（Git review）。
- **七大模型角色（roles）**——架构灵魂，把"模型"与"功能"解耦：
  - `chat`（对话）/ `autocomplete`（Tab 补全）/ `edit`（内联编辑）/ `apply`（应用差异）
  - `embed`（向量化，供 @codebase 语义检索）/ `rerank`（重排序）/ `summarize`（摘要）
  - → 可用顶级模型做推理、本地小模型做补全、专用模型做检索，**效果/成本/延迟精确权衡**。
- **上下文提供者 + MCP**：`@codebase`（代码库 RAG 索引）、`@docs`（文档检索）、原生支持 **Model Context Protocol** 接入数据库/API/知识库。

## 核心创新点
1. **模型无关 + 本地优先**：真正的"自带模型"，可用 Ollama 跑本地模型，数据不出本机——隐私/受监管团队刚需。
2. **角色化配置**：七角色解耦，组合式能力编排。
3. **三端覆盖，独有 JetBrains**：填补开源 AI 助手在 IntelliJ/PyCharm 等企业后端生态的空白。
4. **MCP 开放协议**：较早集成，连接庞大工具/数据源生态。
5. **Apache 2.0 + 零成本**：配 OpenRouter 免费额度或本地模型，无需订阅即可上手。

## 竞品对比
| 方案 | 开源 | 与 Continue 对比 |
|---|:---:|---|
| **Cursor** | ❌ | 闭源标杆、体验打磨，现已**收购 Continue** |
| **GitHub Copilot** | ❌ | 生态最广、企业集成强，但闭源、模型受限 |
| **Cline** | ✅ | 同为开源 VS Code 扩展，Agent 自主性/可视化审批更激进 |
| **Aider** | ✅ | 终端原生、**Git 自动提交**是杀手锏 |
| **OpenCode** | ✅ | Continue 被收购后，社区推荐的独立开源替代之一 |

## 综合评分：8.0 / 10
| 维度 | 分数 |
|---|---|
| 功能完整度 | 8.8 |
| 架构设计 | 9.2 |
| 开放性 / 隐私 | 9.0 |
| 实用价值 | 8.2 |
| 文档与生态 | 8.0 |
| **未来确定性** | **5.5** ⚠️（收购折价） |

## ⚠️ 关键风险
**2025 年被最大闭源竞品 Cursor 收购**。虽团队承诺延续开源路线，但：① 开源承诺能否长期兑现存疑；② 部分社区已视其为"不再独立的 Cursor 替代品"；③ 关注自主可控者应跟踪协议/治理变化，并评估 Cline / Aider / OpenCode 替代方案。

## 结论
Continue 是理解"开源 AI 编码"绕不开的参照系，**技术架构（9.2）与开放性（9.0）优秀，多端覆盖值得借鉴**；但被收购后**未来确定性显著折价**。若以长期自主可控为硬性要求，建议同时跟踪独立开源方案并谨慎评估其走向。

---
📅 分析日期：2026-06-18 ｜ 来源：[GitHub](https://github.com/continuedev/continue) · [官网](https://www.continue.dev/) · [config.yaml 文档](https://docs.continue.dev/reference)
