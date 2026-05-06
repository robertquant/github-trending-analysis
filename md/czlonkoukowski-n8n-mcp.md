# n8n-mcp — 用 AI 构建 n8n 工作流的 MCP 服务器

> **项目地址**: [github.com/czlonkowski/n8n-mcp](https://github.com/czlonkowski/n8n-mcp)
> **官网**: [n8n-mcp.com](https://www.n8n-mcp.com/)
> **许可证**: MIT
> **语言**: TypeScript
> **Stars**: 19,734 | **今日新增**: 282
> **版本**: v2.47.5+ | **npm**: n8n-mcp

---

## 项目简介

n8n-mcp 是一个基于 **Model Context Protocol (MCP)** 的服务器，充当 n8n 工作流自动化平台与 AI 模型之间的桥梁。它让 Claude Desktop、Claude Code、Cursor、Windsurf、VS Code、ChatGPT 等 20+ AI 工具能够深度理解 n8n 的 1,650 个工作流节点，自动构建、验证和部署 n8n 工作流。

简单来说：**让 AI 成为你的 n8n 工作流专家。**

---

## 核心功能

### 节点知识库
- **1,650 个 n8n 节点** — 820 核心节点 + 830 社区节点（741 已验证）
- **99% 属性覆盖率** — 详细的参数 Schema
- **87% 文档覆盖率** — 包含 AI 节点的官方文档
- **265 个 AI 工具变体** — 完整文档支持

### 工作流模板
- **2,352 个工作流模板** — 99.96% AI 元数据覆盖率
- **156 个真实配置示例** — 从热门模板中提取
- **多维度搜索** — 关键词、节点类型、任务类型、元数据

### 智能工具集（7 个核心 MCP 工具）
| 工具 | 功能 |
|------|------|
| `tools_documentation` | 获取任何 MCP 工具的文档 |
| `search_nodes` | 全文搜索所有节点 |
| `get_node` | 获取节点信息（支持多种模式） |
| `validate_node` | 节点配置验证（最小/完整模式） |
| `validate_workflow` | 完整工作流验证 |
| `search_templates` | 模板搜索（4 种模式） |
| `get_template` | 获取完整工作流 JSON |

### n8n 实例管理（13 个管理工具）
- 工作流 CRUD（创建/读取/更新/删除）
- Diff-based 部分更新（节省 Token）
- 执行管理与测试
- 凭证管理
- 安全审计
- 自动修复工作流错误

### Chat Agent（新增）
- 零配置在线版本
- 一句话描述即可生成工作流
- 从 72,000+ 模式库中匹配
- 自动验证和部署

---

## 技术架构

```
┌─────────────────────────────────────────────┐
│            AI 客户端 (20+ 工具)              │
│  Claude / Cursor / VS Code / ChatGPT / ...  │
└──────────────────┬──────────────────────────┘
                   │ MCP Protocol (stdio/SSE)
┌──────────────────▼──────────────────────────┐
│              n8n-mcp 服务器                  │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │  节点知识库  │  │  模板库 (2,352+)     │  │
│  │  (1,650+)   │  │  元数据搜索引擎      │  │
│  └─────────────┘  └──────────────────────┘  │
│  ┌─────────────┐  ┌──────────────────────┐  │
│  │  验证引擎   │  │  Diff 更新引擎       │  │
│  │  (多级验证) │  │  (Token 优化)        │  │
│  └─────────────┘  └──────────────────────┘  │
└──────────────────┬──────────────────────────┘
                   │ REST API
┌──────────────────▼──────────────────────────┐
│           n8n 实例 (自托管/Cloud)            │
│         工作流执行引擎                       │
└─────────────────────────────────────────────┘
```

### 技术栈
- **运行时**: Node.js / TypeScript
- **传输**: stdio（本地）/ SSE（远程）
- **部署**: npx / Docker / Railway / 自托管
- **数据库**: SQLite（轻量级本地存储）
- **包管理**: npm（`n8n-mcp`）
- **测试**: 5,418+ 测试用例通过
- **兼容 n8n 版本**: 2.18.4+

---

## 应用场景

1. **快速原型设计** — 用自然语言描述需求，AI 直接生成 n8n 工作流
2. **工作流调试** — AI 分析失败的工作流，自动定位和修复问题
3. **批量迁移** — 在不同 n8n 实例间迁移和更新工作流
4. **学习 n8n** — 通过 AI 交互式了解每个节点的用法和最佳实践
5. **CI/CD 集成** — 在开发流程中自动验证和部署 n8n 工作流
6. **团队协作** — 通过共享模板和模式库加速团队自动化开发

---

## 为什么火（Trending 原因）

1. **MCP 生态爆发** — 随着 Claude Desktop、Cursor 等 AI 工具原生支持 MCP，市场对高质量 MCP 服务器的需求暴增
2. **n8n 社区庞大** — n8n 本身拥有数百万用户，对 AI 辅助工作流构建的需求真实且迫切
3. **实用性极强** — 不是概念验证，而是真正能投入生产的工具，支持 1,650+ 节点和 2,352+ 模板
4. **持续更新** — 文档与 n8n 最新版本保持 48 小时内同步
5. **商业验证** — PayPal、Mercado Libre、Swiggy 等知名企业团队在使用
6. **零门槛体验** — Chat Agent 提供免费在线版本，无需安装即可尝试
7. **YouTube 传播** — Cole Medin、Nate Herk 等 AI 领域 KOL 制作教程推动传播

---

## 同类项目对比

| 特性 | n8n-mcp | n8n 官方 MCP | makafeli/n8n-workflow-builder |
|------|---------|-------------|------------------------------|
| 节点覆盖 | 1,650+ | ~400 | 有限 |
| 模板库 | 2,352+ | 无 | 无 |
| 社区节点 | 830+ | 无 | 无 |
| 验证引擎 | 多级验证 | 基础 | 基础 |
| Diff 更新 | 支持 | 不支持 | 不支持 |
| 在线服务 | Chat Agent | 无 | 无 |
| IDE 集成 | 20+ 工具 | Claude Desktop | Claude Desktop |
| AI 工具变体 | 265 个 | 无 | 无 |
| 自动修复 | 支持 | 不支持 | 不支持 |
| 开源协议 | MIT | MIT | MIT |

**核心优势**：n8n-mcp 在节点覆盖率、模板数量、验证能力和 IDE 兼容性方面均领先同类项目。

---

## 适合谁使用

- **n8n 用户** — 想用 AI 加速工作流构建的自动化工程师
- **AI 开发者** — 在 Claude Code/Cursor 中需要与 n8n 交互的开发者
- **DevOps 工程师** — 需要自动化管理大量 n8n 工作流的运维人员
- **技术团队** — 希望提升自动化开发效率的团队（尤其是不熟悉 n8n 的成员）
- **AI 爱好者** — 对 MCP 生态和 AI Agent 感兴趣的探索者

---

## 快速上手指南

### 方式一：Chat Agent（零配置）

访问 [dashboard.n8n-mcp.com](https://dashboard.n8n-mcp.com)，注册免费账户，直接在网页上用自然语言构建工作流。

### 方式二：Claude Desktop 集成

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

### 方式三：Claude Code CLI

```bash
claude mcp add n8n-mcp -- npx -y n8n-mcp@latest
```

### 方式四：Cursor / VS Code

```json
{
  "mcp": {
    "servers": {
      "n8n-mcp": {
        "command": "npx",
        "args": ["-y", "n8n-mcp@latest"]
      }
    }
  }
}
```

### 方式五：Docker

```bash
docker run -i --rm ghcr.io/czlonkowski/n8n-mcp
```

### 连接 n8n 实例（可选）

如需 AI 直接操作你的 n8n 实例，配置环境变量：

```json
{
  "mcpServers": {
    "n8n-mcp": {
      "command": "npx",
      "args": ["-y", "n8n-mcp@latest"],
      "env": {
        "N8N_API_URL": "http://localhost:5678",
        "N8N_API_KEY": "your-api-key"
      }
    }
  }
}
```

### 使用示例

在 Claude 中直接说：
> "帮我创建一个工作流：当收到 Webhook 请求时，解析 JSON 数据，发送到 Slack 频道，并记录到 Google Sheets"

AI 会自动搜索模板、查找节点、验证配置、生成工作流 JSON，甚至直接部署到你的 n8n 实例。

---

## 安全提示

> **永远不要让 AI 直接编辑生产环境工作流！** 始终在开发环境测试，并备份重要工作流。

---

## 相关资源

- [GitHub 仓库](https://github.com/czlonkowski/n8n-mcp)
- [官方网站](https://www.n8n-mcp.com/)
- [n8n-skills（Claude Code 技能集）](https://github.com/czlonkowski/n8n-skills)
- [YouTube 教程](https://www.youtube.com/watch?v=5CccjiLLyaY)
- [n8n 社区讨论](https://community.n8n.io/t/i-built-an-mcp-server-that-makes-claude-an-n8n-expert-heres-how-it-changed-everything/133902)
- [npm 包](https://www.npmjs.com/package/n8n-mcp)

---

*分析日期: 2026-05-05*
