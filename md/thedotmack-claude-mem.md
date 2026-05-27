# thedotmack/claude-mem - AI Agent 跨会话持久记忆系统

> **GitHub Trending · 2026.05.27** | ⭐ 45,000+ Stars | 🏷️ v6.5.0 | 📜 Apache 2.0
> 作者：Alex Newman (@thedotmack)

---

## 项目简介

**claude-mem** 是一个为 Claude Code 及其他 AI 编程助手设计的**跨会话持久记忆插件**。它解决了 AI Agent 每次新会话都"失忆"的核心痛点 —— 自动记录编程上下文、决策逻辑和技术细节，让 AI 在后续会话中能够无缝衔接之前的工作。

### 核心功能

- **持久记忆** —— 上下文在会话之间自动保留，AI 不再从零开始
- **渐进式信息展示（Progressive Disclosure）** —— 分层记忆检索，附带 Token 消耗可视化，节省约 10x Token 用量
- **技能搜索（mem-search）** —— 用自然语言查询项目历史记忆
- **Web 可视化界面** —— 在 localhost:37777 实时查看记忆流
- **隐私控制** —— 使用 `<private>` 标签排除敏感内容
- **引文系统** —— 通过 ID 引用过去的观察记录
- **多平台支持** —— 兼容 Claude Code、Gemini CLI、OpenCode、OpenClaw、Copilot 等
- **自动运行** —— 无需手动干预，安装即生效

---

## 技术架构

### 6 大核心组件

| 组件 | 说明 |
|------|------|
| 5 个生命周期 Hook | SessionStart / UserPromptSubmit / PostToolUse / Stop / SessionEnd |
| 智能安装器 | 缓存依赖检查器（pre-hook 脚本） |
| Worker Service | 基于 Bun 运行时的 HTTP API（端口 37777），内置 Web UI |
| SQLite 数据库 | 持久化存储会话、观察记录、摘要 |
| Chroma 向量数据库 | 混合语义 + 关键词搜索，智能上下文检索 |
| mem-search 技能 | 自然语言查询，渐进式信息展示 |

### 3 层 MCP 搜索工作流

```
Step 1: search()           → 获取紧凑索引（~50-100 tokens/条）
Step 2: timeline()         → 获取时间线上下文
Step 3: get_observations() → 仅获取筛选后的完整详情（~500-1000 tokens/条）

结果：Token 消耗降低约 10 倍
```

### 技术栈

TypeScript · Node.js 18+ · Bun Runtime · SQLite 3 · ChromaDB · Claude Agent SDK · MCP Protocol · FTS5

### 多模式多语言

支持 `code`（英语默认）、`code--zh`（中文）、`code--ja`（日语）等工作模式，通过 `CLAUDE_MEM_MODE` 配置切换。

---

## 应用场景

- **长期项目开发** —— 每天启动 Claude Code 时，自动加载之前的开发上下文
- **多人协作交接** —— 团队成员快速了解项目历史决策和架构演进
- **复杂 Bug 追踪** —— 记录调查过程，后续会话从上次中断处继续
- **代码审查知识积累** —— 审查意见和改进建议被持久保存
- **学习与教学** —— AI 辅助学习过程中的知识点被记录
- **DevOps 运维** —— 记录基础设施变更历史和故障排查经验

---

## 为什么火（Trending 原因）

1. **解决核心痛点** —— AI Agent "失忆"是开发者最大的体验问题之一
2. **开箱即用** —— 一条命令安装，无需配置即可自动运行
3. **生态卡位精准** —— 2026 年被称为"AI Agent 持久上下文元年"
4. **社区驱动增长** —— Reddit r/ClaudeCode 起步，45,000+ Stars
5. **多 Agent 支持** —— 扩展到 Gemini CLI、OpenCode、OpenClaw 等
6. **Token 经济性** —— 渐进式信息展示节省约 10x Token 消耗
7. **高迭代速度** —— 从 v3 到 v6.5+ 持续快速演进
8. **文化现象** —— 社区代币 $CMEM 的出现体现了社区极高热情

---

## 同类项目对比

| 项目 | 核心定位 | 优势 | 不足 |
|------|---------|------|------|
| **claude-mem** | Claude Code 专用记忆插件 | 深度集成、渐进式展示、10x Token 节省 | 主要面向 Claude 生态 |
| **Mem0** | 通用 AI 记忆框架 | 26% 更高准确率、跨平台通用 | 需要基础设施、延迟较高 |
| **Zep** | 企业级 AI 记忆 | 90% 延迟降低、企业级可靠 | 部署复杂度高 |
| **Memvid** | 轻量级记忆方案 | 极简部署、无依赖 | 检索精度有限 |
| **Claude Code 内置 Memory** | 原生文件记忆 | 无需安装、可审计 | 无向量搜索、检索精度有限 |

**claude-mem 差异化优势**：在 Claude Code 生态中做到最深度集成，Hook 机制实现全自动无感知运行，渐进式信息展示在 Token 成本上具有显著优势。

---

## 适合谁使用

- 重度 Claude Code 用户 —— 每天使用 Claude Code 的程序员
- 长期项目维护者 —— 需要保留完整项目上下文
- AI Agent 开发者 —— 构建基于 Claude 的自动化工作流
- 团队技术负责人 —— 保留团队协作中的 AI 上下文连续性
- DevOps / SRE 工程师 —— 记录和回溯运维决策
- 多 IDE 用户 —— 在不同 AI 编程助手之间切换

---

## 快速上手

### 1. 安装（一行命令）

```bash
# Claude Code
npx claude-mem install

# Gemini CLI
npx claude-mem install --ide gemini-cli

# OpenCode
npx claude-mem install --ide opencode

# 或通过插件市场
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
```

### 2. 重启 Claude Code

安装后重启即可生效，来自之前会话的上下文将自动出现在新会话中。

### 3. 使用搜索技能

```
/mem-search 我之前是怎么处理认证 bug 的？
```

### 4. 配置（可选）

```json
// ~/.claude-mem/settings.json
{
  "CLAUDE_MEM_MODE": "code--zh"
}
```

### 5. 隐私控制

使用 `<private>` 标签排除敏感内容，被标记的内容不会被记录到记忆系统中。

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|:----:|------|
| 创新性 | **9.0** | 渐进式信息展示、Hook 自动化、混合搜索均为行业创新 |
| 代码质量 | **8.5** | TypeScript 全栈、模块化架构、Bun 运行时优化 |
| 实用性 | **9.5** | 直击痛点、一行安装、零配置、10x Token 节省 |
| 文档完善度 | **9.0** | 完整文档站、25+ 语言、详细架构文档 |
| 社区活跃度 | **9.5** | 45K+ Stars、活跃 Discord、Reddit 驱动、快速迭代 |

### 综合评分：9.1 / 10

> 极具创新性和实用性的 AI Agent 记忆系统。如果你是 Claude Code 的重度用户，这是一个必备插件。

---

*📊 由 AI 深度分析生成 · 2026.05.27 · Powered by Claude Code*

Sources:
- [GitHub - thedotmack/claude-mem](https://github.com/thedotmack/claude-mem)
- [Reddit - 45K Stars Milestone](https://www.reddit.com/r/ClaudeCode/comments/1scz5kk/claudemem_hit_45000_stars_on_github_today_and_it/)
- [11 Best GitHub Repos for Claude Code (Medium)](https://medium.com/synthetic-futures/11-best-github-repos-for-claude-code-that-will-10x-your-next-project-in-2026-b300a120bd8b)
- [Mem0 vs Zep vs Claude-Mem Comparison](https://serenitiesai.com/articles/ai-agent-memory-why-2026-is-the-year-of-persistent-context)
- [State of AI Agent Memory 2026](https://mem0.ai/blog/state-of-ai-agent-memory-2026)
- [知乎 - Claude-Mem: Giving Claude Code Permanent Memory](https://zhuanlan.zhihu.com/p/2028261702915879837)
