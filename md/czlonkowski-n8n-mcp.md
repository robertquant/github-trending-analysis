# n8n-mcp — AI 驱动的 n8n 工作流自动化 MCP 服务器

> **仓库**: [github.com/czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp)
> **作者**: Romuald Czlonkowski
> **语言**: TypeScript | **协议**: MIT
> **Stars**: 19,734 | **今日增长**: +282

---

## 项目简介

n8n-mcp 是一个基于 Model Context Protocol (MCP) 的服务器，在 n8n 工作流自动化平台与 AI 模型之间架起桥梁。它让 Claude Desktop、Claude Code、Cursor、Windsurf 等 AI 助手深度理解 n8n 的完整节点生态系统，从"通用聊天助手"进化为"n8n 工作流专家"。

项目由 Romuald Czlonkowski 创建，最初是个人工具，现已发展为帮助数万名开发者高效构建工作流的开源项目。

---

## 核心功能

### 20 个 MCP 工具，覆盖工作流全生命周期

#### 核心工具（7 个）
- **tools_documentation** — 获取任何 MCP 工具的文档（推荐从这里开始）
- **search_nodes** — 全文搜索 1,650+ n8n 节点，支持社区节点过滤和配置示例
- **get_node** — 统一的节点信息工具，支持多种模式（最小/标准/完整信息、文档模式、属性搜索、版本对比）
- **validate_node** — 节点验证（快速必填项检查 / 完整验证）
- **validate_workflow** — 完整的工作流验证，包括 AI Agent 验证
- **search_templates** — 统一的模板搜索（关键词 / 节点类型 / 任务类型 / 元数据多维度筛选）
- **get_template** — 获取完整工作流 JSON

#### n8n 管理工具（13 个，需配置 API）
- **工作流管理**: 创建、获取、更新（全量/增量）、删除、列表、验证、自动修复、版本管理、模板部署
- **执行管理**: 测试/触发工作流执行、执行记录管理
- **凭证管理**: 凭证的增删改查
- **安全审计**: 实例安全审计 + 深度工作流扫描
- **系统工具**: API 连通性检查

---

## 数据覆盖

| 指标 | 数量 |
|------|------|
| n8n 节点 | 1,650+（820 核心 + 830 社区） |
| 节点属性覆盖 | 99% |
| 节点操作覆盖 | 63.6% |
| 文档覆盖 | 87% |
| AI 工具变体 | 265 个 |
| 真实配置示例 | 156 个（来自热门模板） |
| 工作流模板 | 2,352 个（99.96% AI 元数据覆盖） |
| 已验证社区节点 | 741 个 |

---

## 技术架构

### 技术栈
- **语言**: TypeScript
- **运行时**: Node.js
- **包管理**: npm (`n8n-mcp`)
- **协议**: MCP (Model Context Protocol)
- **传输**: stdio / SSE / HTTP
- **容器化**: Docker (ghcr.io/czlonkowski/n8n-mcp)
- **云服务**: dashboard.n8n-mcp.com（免费层 100 次调用/天）
- **CI/CD**: Railway 一键部署

### 架构流程
```
AI 助手 (Claude/Cursor/Windsurf) → n8n-mcp (MCP Server) → n8n 平台 → 外部服务
```

### 兼容的 AI 客户端
- Claude Desktop
- Claude Code
- Visual Studio Code (GitHub Copilot)
- Cursor
- Windsurf
- Codex
- Antigravity

---

## 应用场景

1. **聊天机器人工作流**: 用自然语言描述需求，AI 自动生成包含 Webhook 触发器、AI Agent、消息路由的完整工作流
2. **数据管道自动化**: 一句话描述数据源和目标，自动生成 ETL 管道（API 调用、数据清洗、格式转换、数据库写入）
3. **监控与告警**: 快速搭建定时监控工作流（服务状态检查、异常检测、Slack/Telegram 告警通知）
4. **AI Agent 工作流**: 利用 LangChain 节点构建 AI Agent 工作流，集成 OpenAI、向量数据库、工具调用链
5. **CI/CD 集成**: 自动化构建、测试、部署流水线
6. **安全合规审计**: 利用内置审计工具进行工作流安全扫描

---

## 为什么火（Trending 原因）

### 1. MCP 生态爆发
Model Context Protocol 正在成为 AI 与外部工具交互的标准协议。随着 Claude、Cursor 等 AI 工具普及，MCP 服务器需求激增。n8n-mcp 是最成熟的工作流自动化 MCP 实现之一。

### 2. n8n 社区高速增长
n8n 是最流行的开源工作流自动化平台之一，拥有庞大的用户群体。用户对 AI 辅助构建工作流的需求非常强烈。

### 3. 解决真实痛点
直接解决了 AI 生成 n8n 工作流时的核心问题：
- AI 对 n8n 节点不了解（易产生幻觉）
- 节点属性众多，手动配置易出错
- 工作流 JSON 结构复杂，手动编写效率低

### 4. 社区活跃
- n8n 官方论坛推荐
- YouTube 多个教程视频
- Reddit/Medium 大量讨论
- 配套 n8n-skills 项目提供 7 个 Claude Code Skills

---

## 同类项目对比

| 特性 | n8n-mcp | 手动粘贴 JSON | 纯 AI 对话 |
|------|---------|-------------|-----------|
| 节点知识覆盖 | 1,650+ 节点 | 依赖个人经验 | 易产生幻觉 |
| 直接部署到 n8n | ✅ | ❌ | ❌ |
| 多级验证 | 4 层验证 | 手动测试 | 无验证 |
| 工作流模板 | 2,352 个 | 需手动查找 | 有限 |
| 实时更新 | 跟随 n8n 版本 | N/A | 训练数据截止 |
| IDE 集成 | 5+ IDE | N/A | 部分 |

---

## 适合谁使用

- **自动化工程师**: 用 AI 加速工作流开发，减少查阅文档的时间
- **创业团队**: 快速搭建 MVP 自动化流程，对话式构建生产级工作流
- **n8n 新手**: 零经验也能通过 AI 引导创建复杂工作流，内置模板即学即用
- **DevOps / SRE**: 自动化运维工作流，CI/CD 管道集成，安全审计
- **AI 应用开发者**: 构建 AI Agent 工作流，集成 LangChain 和各种 LLM

---

## 快速上手

### 方式一：npx 一键启动（推荐）
```bash
npx -y n8n-mcp@latest
```

### 方式二：配置 Claude Desktop
在 `claude_desktop_config.json` 中添加：
```json
{
  "mcpServers": {
    "n8n-mcp": {
      "command": "npx",
      "args": ["-y", "n8n-mcp@latest"]
    }
  }
}
```

### 方式三：Docker
```bash
docker run -i --rm ghcr.io/czlonkowski/n8n-mcp
```

### 方式四：云服务
访问 [dashboard.n8n-mcp.com](https://dashboard.n8n-mcp.com)，免费层每天 100 次工具调用。

### 连接 n8n 实例（可选）
配置环境变量以启用完整的管理工具：
```bash
N8N_API_URL=https://your-n8n-instance.com
N8N_API_KEY=your-api-key
```

---

## 安全提示

> **重要**: 永远不要直接用 AI 编辑生产环境的工作流！
> - 在使用 AI 工具前先备份工作流
> - 先在开发环境测试
> - 导出重要工作流的备份
> - 部署到生产环境前验证所有更改

---

## 相关资源

- [GitHub 仓库](https://github.com/czlonkowski/n8n-mcp)
- [n8n-skills 配套项目](https://github.com/czlonkowski/n8n-skills)
- [n8n 官方论坛讨论](https://community.n8n.io/t/i-built-an-mcp-server-that-makes-claude-an-n8n-expert-heres-how-it-changed-everything/133902)
- [自托管指南](https://github.com/czlonkowski/n8n-mcp#self-hosting-guide)
- [安全加固文档](https://github.com/czlonkowski/n8n-mcp#security--hardening)
