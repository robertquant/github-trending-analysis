# AgentsView — AI 编码代理的本地会话智能分析平台

**仓库：** [kenn-io/agentsview](https://github.com/kenn-io/agentsview) | **作者：** Wes McKinney (pandas 创建者) | **协议：** MIT | **综合评分：9.0/10**

## 项目概述

AgentsView 是一款本地优先的 AI 编码代理会话智能分析工具，自动发现本机 20+ 编码代理（Claude Code、Codex、Gemini CLI、Cursor 等）的会话数据，同步到本地 SQLite 数据库，通过精美 Web UI 呈现完整分析视图。是 ccusage 的 100x 更快替代方案。

## 技术架构

- **后端：** Go 1.26+（CGO），SQLite + FTS5 全文搜索，SSE 实时推送
- **前端：** Svelte 5 + TypeScript (Vite)，Tauri 桌面端封装
- **部署：** 一行命令安装 / Homebrew / Docker / 桌面应用
- **团队模式：** PostgreSQL 同步后端

## 核心创新点

1. **20+ 代理统一支持** — 覆盖几乎所有主流 AI 编码代理的自动会话发现
2. **本地优先 + 零隐私风险** — 无遥测、无账户，服务器绑定 127.0.0.1
3. **100x 性能优势** — SQLite 索引查询 vs 重解析文件
4. **Prompt Cache 感知** — 精确区分缓存创建/读取 token 的成本计算
5. **丰富统计分析** — 会话分类、时长分布、工具/模型/代理混合比
6. **团队协作** — PostgreSQL 后端汇聚多成员数据

## 竞品对比

| 维度 | AgentsView | ccusage | Langfuse | Helicone |
|---|---|---|---|---|
| 代理覆盖 | 20+ | ~7 | 通用 LLM | 通用 LLM |
| 本地优先 | ✅ | ✅ | ❌ | ❌ |
| 可视化 UI | ✅ Web+桌面 | ❌ CLI | ✅ | ✅ |
| 查询速度 | 极快 | 慢 | 中等 | 中等 |

## 综合评价

由 pandas 创始人打造的开发者基础设施级工具，精准切中 AI 编码代理"不可见"的痛点。覆盖面广、性能卓越、隐私设计优秀。随着 AI 编码代理成为主流，该项目有望成为该细分领域的标准工具。**强烈推荐关注和使用。**

---
*分析日期：2026-06-12 | AI 深度分析引擎自动生成*
