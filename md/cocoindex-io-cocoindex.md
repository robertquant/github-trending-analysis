# CocoIndex - 面向长周期Agent的增量数据引擎

> Incremental engine for long horizon agents · 开源增量数据框架 · Apache 2.0

| 指标 | 数据 |
|------|------|
| ⭐ Stars | 8,286 |
| 🔥 今日新增 | +434 |
| 💻 语言 | Python (API) + Rust (核心引擎) |
| 📄 许可证 | Apache 2.0 |
| 🏷️ 分类 | AI数据管道 / RAG / 增量索引 |

---

## 📋 项目简介

CocoIndex 是一个开源的增量数据框架，专为长周期 AI Agent 设计。它将代码库、会议记录、Slack 消息、PDF、视频等多种数据源转化为 **实时、持续刷新** 的上下文，供 AI Agent 和 LLM 应用高效推理——且只处理增量变化（Δ）。

核心理念：**"React for data engineering"** — 声明目标状态，引擎自动保持同步，只重新计算变化的部分。

---

## 🔧 核心功能

### 1. 增量同步引擎
- 只处理变化的 Δ（delta），无需全量重建
- 源数据变更时自动识别受影响记录，精确传播更新
- 代码变更时基于 hash(code) + hash(input) 的智能缓存失效

### 2. 声明式 Python API
- 用简洁的 Python 函数声明目标状态
- 引擎自动处理增量计算、缓存、并行、失败重试
- 代码像一次性脚本一样简单，引擎处理其余所有事情

### 3. 多源连接器（8类）
- 代码库、会议记录、Web/API、文件系统/对象存储
- 数据库、消息队列、图片/视频、语音/转录

### 4. 多目标存储（6类）
- 关系数据库、数据仓库、向量数据库（pgvector/LanceDB）
- 图数据库（Neo4j/Kuzu）、消息队列（Kafka）、特征存储

### 5. CocoIndex Code（旗舰 MCP 服务器）
- AST 感知的增量语义代码索引
- 支持调用图、符号搜索、向量搜索、代码块管理
- 70% token 使用减少，80-90% 缓存命中率
- 支持 Python、TypeScript、Rust、Go
- 兼容 Claude Code、Cursor 等 MCP 客户端

### 6. 端到端数据血缘
- 每个目标向量/行/图节点都可追溯至精确的源字节
- 可调试、可审计、合规友好

---

## 📐 技术架构

| 组件 | 技术选型 |
|------|---------|
| 核心引擎 | Rust（生产级） |
| API 层 | Python |
| 执行模型 | 持久状态驱动数据流 |
| 并行策略 | 默认并行，零拷贝转换 |
| 缓存机制 | hash(input) + hash(code) 双重 memoization |
| 容错 | 重试、指数退避、死信队列、零数据丢失 |
| 许可证 | Apache 2.0 |

---

## 📊 为什么增量？

| 优势 | 说明 |
|------|------|
| 亚秒级新鲜度 | 源变更传播到目标 < 1 秒 |
| 10x 成本节省 | 只处理 0.1% 变更数据，99.9% 命中缓存 |
| 默认可解释 | 端到端血缘追踪，每个字节可溯源 |
| 生产级可靠 | Rust 核心 + 重试 + DLQ + 零数据丢失 |

---

## 🎯 应用场景（20+ 内置示例）

- 🔍 **实时代码索引** — AST 分块、嵌入、pgvector/LanceDB、每次 commit 增量更新
- 📄 **PDF → RAG 索引** — 本地/S3/GDrive PDF 摄入，增量更新
- 📰 **HN 热门话题** — 爬取 HN + LLM 提取主题 + Postgres 存储
- 🕸️ **对话 → 知识图谱** — 会议转录 LLM 提取实体/决策 → Neo4j/Kuzu
- 📦 **多仓库摘要** — N 个 Git 仓库结构提取 + LLM 摘要
- 📋 **结构化提取** — BAML/DSPy 表单/发票/KYC → 数据库
- 🎙️ **播客 → 知识图谱** — Whisper 转录 + 说话人分离 + SurrealDB
- 📊 **CSV → Kafka 实时流** — 文件监听 + Kafka 发布

---

## 🔥 为什么火 (Trending 原因)

1. **精准定位 AI Agent 数据痛点** — Agent 需要新鲜上下文，批处理管道必然过时
2. **React 式心智模型** — "声明式" 大幅降低数据工程门槛
3. **MCP 生态爆发** — CocoIndex Code 直接兼容 Claude Code、Cursor 等主流 AI 编辑器
4. **Rust 核心保证性能** — Python 易用 + Rust 性能，两全其美
5. **Apache 2.0 完全开源** — 无 ELv2 等限制，社区友好
6. **20+ 即用示例** — 每周更新，降低上手门槛
7. **企业级特性** — PB 级扩展、10x LLM 成本节省

---

## 📊 同类项目对比

| 特性 | CocoIndex | LlamaIndex | LangChain ETL | Airbyte |
|------|-----------|------------|---------------|---------|
| 增量处理 | ✅ 原生 | ❌ | ❌ | ✅ |
| AI 原生 | ✅ | ✅ | ✅ | ❌ |
| 声明式 API | ✅ React 式 | ❌ | ❌ | ❌ |
| Rust 核心 | ✅ | ❌ | ❌ | ❌ Java |
| MCP 兼容 | ✅ | ❌ | ❌ | ❌ |
| 数据血缘 | ✅ 端到端 | ❌ | ❌ | ⚠️ |
| 知识图谱 | ✅ Neo4j/Kuzu | ✅ | ✅ | ❌ |
| 代码索引 | ✅ AST 感知 | ⚠️ 基础 | ❌ | ❌ |
| 开源 | ✅ Apache 2.0 | ✅ MIT | ✅ MIT | ✅ |

**结论**：CocoIndex 是目前唯一将"声明式增量"与"AI Agent 原生"结合的框架。

---

## 🚀 快速上手

### 安装
```bash
pip install cocoindex
```

### 最小示例（文档索引）
```python
import cocoindex as coco
from cocoindex.connectors import localfs, postgres
from cocoindex.ops.text import RecursiveSplitter

@coco.fn(memo=True)
async def index_file(file, table):
    for chunk in RecursiveSplitter().split(await file.read_text()):
        table.declare_row(text=chunk.text, embedding=embed(chunk.text))

@coco.fn
async def main(src):
    table = await postgres.mount_table_target(PG, table_name="docs")
    table.declare_vector_index(column="embedding")
    await coco.mount_each(index_file, localfs.walk_dir(src).items(), table)

coco.App(coco.AppConfig(name="docs"), main, src="./docs").update_blocking()
```

运行一次完成回填，再次运行只处理变更文件。

### CocoIndex Code (MCP)
```bash
# Claude Code
claude mcp add cocoindex-code -- cocoindex-code

# Cursor - 添加到 .cursor/mcp.json
```

---

## 👥 适合谁使用

- 🤖 **AI Agent 开发者** — 为 Agent 构建持续刷新的上下文管道
- 🔍 **RAG 工程师** — 构建增量向量索引，告别全量重建
- 🏢 **企业 AI 团队** — PB 级企业知识库实时索引
- 🛠️ **AI 编程工具用户** — CocoIndex Code 提升 Claude Code/Cursor 效果
- 📊 **数据工程师** — Python 声明式 ETL，无需 DAG 编排

---

## ⭐ 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 8/10 | React 式数据工程心智模型新颖，但增量处理本身非全新 |
| 代码质量 | 8/10 | Rust 核心 + Python API，生产级容错 |
| 实用性 | 9/10 | 精准解决 AI Agent 上下文新鲜度痛点 |
| 文档完善度 | 9/10 | 20+ 示例、博客、文档站、社区教程 |
| 社区活跃度 | 7/10 | Discord 活跃、Reddit 讨论，但尚处早期增长阶段 |
| **综合** | **8.2/10** | **⭐⭐⭐⭐** |

---

## 💡 总结

CocoIndex 是 2026 年 AI 数据基础设施领域的重要创新。它以 **"React for data engineering"** 的核心理念，通过声明式 Python API + Rust 增量引擎，解决了 AI Agent 长周期运行中上下文数据过时的核心难题。作为目前唯一将增量数据管道与 AI Agent 原生集成的开源框架，CocoIndex 在 RAG、代码索引、知识图谱等场景下展现出强大的实用价值，Apache 2.0 许可证更使其成为企业友好的选择。

---

📡 数据来源: GitHub · cocoindex.io · Reddit r/Rag · dev.to · Medium
🤖 分析由 AI 自动生成，仅供参考 | 2026-05-06
