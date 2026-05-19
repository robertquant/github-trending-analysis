# anthropics/claude-plugins-official

> Anthropic 官方管理的高质量 Claude Code 插件目录 —— 一站式插件市场，扩展你的 AI 编程工作流

| 指标 | 数据 |
|------|------|
| Stars | 20,000+ |
| Forks | 2,500+ |
| Commits | 394 |
| Issues | 667 |
| Watchers | 147 |
| 语言 | Python 31.6%, TypeScript 28.9%, HTML 19.5%, Shell 13.0%, JavaScript 7.0% |
| Trending 排名 | #4 (2026-05-20) |

---

## 项目简介

**claude-plugins-official** 是 Anthropic 官方维护的 Claude Code 插件市场目录。类似于 VS Code 扩展市场或 npm 生态，但专门为 Claude Code（Anthropic 的 AI 编程助手）打造。

它提供了集中化的插件发现、安装和管理能力，用户通过一条命令即可安装由 Anthropic 官方或社区开发的高质量插件，扩展 Claude Code 的能力边界。

### 核心功能

- **插件市场（Marketplace）** —— 集中化的插件浏览、发现和安装
- **双轨制来源** —— `/plugins`（Anthropic 内部开发）+ `/external_plugins`（社区/第三方）
- **一键安装** —— `/plugin install {name}@claude-plugins-official`
- **标准化结构** —— `plugin.json` 元数据 + MCP 配置 + 命令/代理/技能定义
- **质量审核** —— 外部插件需满足质量和安全标准
- **内置 Discover** —— Claude Code 中直接浏览 `/plugin > Discover`

---

## 技术架构

### 插件标准结构

```
plugin-name/
├── .claude-plugin/
│   └── plugin.json      # 插件元数据（必需）
├── .mcp.json            # MCP 服务器配置（可选）
├── commands/            # 斜杠命令（可选）
├── agents/              # Agent 定义（可选）
├── skills/              # Skill 定义（可选）
└── README.md            # 文档
```

### 架构亮点

- **MCP（Model Context Protocol）集成** —— 插件通过 MCP 协议与 Claude Code 通信，实现工具调用和上下文共享
- **Skills + Agents + Hooks 三层扩展模型** —— 覆盖从简单命令到复杂工作流的全场景
- **LSP 深度集成** —— 提供 typescript-lsp 等语言服务协议插件，增强代码智能
- **marketplace.json 注册机制** —— 标准化清单文件管理插件注册和发现

---

## 热门插件

| 插件名 | 功能 |
|--------|------|
| **typescript-lsp** | TypeScript/JavaScript 语言服务器，代码智能、类型检查 |
| **playwright** | 浏览器自动化与 E2E 测试 |
| **security-guidance** | 安全最佳实践指导 |
| **context7** | 上下文管理增强 |
| **claude-code-setup** | 扫描项目并自动推荐插件配置 |
| **github** | GitHub 官方 MCP 服务器，管理仓库/Issue/PR |

---

## 应用场景

- **日常开发提效** —— LSP 插件获得类型安全，Playwright 实现自动化测试
- **团队标准化** —— 统一插件配置确保 Claude Code 行为一致
- **安全编码** —— security-guidance 实时检测安全漏洞
- **项目定制化** —— 为特定项目安装专用 Skill 插件
- **MCP 工具集成** —— 连接数据库、API、CI/CD 等外部服务
- **插件开发参考** —— 学习插件开发的模板和最佳实践

---

## 为什么火（Trending 原因）

1. **官方背书 + 生态爆发** —— Anthropic 正式发布插件市场（Public Beta），Claude Code 从工具升级为平台，社区已涌现 6000+ 插件
2. **填补关键空白** —— 之前 Claude Code 缺乏标准化扩展机制，插件市场解决了"如何扩展"的核心痛点
3. **开发者刚需** —— LSP、安全检测、浏览器测试等高频需求一键解决
4. **社区传播效应** —— Reddit 帖子 "28 official plugins most people don't know about" 引爆讨论
5. **低门槛高回报** —— 一行命令安装，即时获得增强能力

---

## 同类项目对比

| 特性 | claude-plugins-official | VS Code Extensions | GitHub Copilot Extensions |
|------|------------------------|--------------------|---------------------------|
| 管理方 | Anthropic 官方 | Microsoft | GitHub |
| 协议标准 | MCP | LSP/自定义 | 自定义 API |
| 插件数量 | 36+ 官方/6000+ 社区 | 40,000+ | ~100 |
| 开源 | ✅ | 部分 | ❌ |
| 质量审核 | Anthropic 人工审核 | 自动+人工 | GitHub 审核 |
| 独特优势 | AI 原生、MCP 标准 | 生态最大 | GitHub 深度集成 |

---

## 适合谁使用

- **Claude Code 日常用户** —— 即装即用，提升 AI 编程效率
- **前端/全栈开发者** —— typescript-lsp、playwright 等插件直接可用
- **安全工程师** —— security-guidance 在编码阶段植入安全实践
- **DevOps 工程师** —— 通过 MCP 插件连接基础设施
- **插件/工具开发者** —— 为 Claude Code 生态贡献扩展
- **技术团队负责人** —— 标准化团队 AI 编程工作流

---

## 快速上手

### 1. 安装插件

```bash
# 在 Claude Code 中运行
/plugin install typescript-lsp@claude-plugins-official
/plugin install playwright@claude-plugins-official
/plugin install security-guidance@claude-plugins-official
```

### 2. 浏览市场

```
/plugin > Discover    # 浏览官方市场中的所有插件
```

### 3. 使用插件

安装后，插件的命令、Agent 和 MCP 工具自动可用。输入 `/` 查看新增的斜杠命令。

### 4. 提交插件（开发者）

按照标准结构开发插件，通过插件目录提交表单申请收录到 `/external_plugins`。

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | ⭐ 9.0/10 | MCP 协议 + AI 原生插件系统，开创 AI 编程工具平台化先河 |
| 代码质量 | ⭐ 8.5/10 | Anthropic 官方出品，结构规范，但部分插件代码风格不一致 |
| 实用性 | ⭐ 9.5/10 | 一键安装解决开发者高频痛点，即时获得感极强 |
| 文档完善度 | ⭐ 8.0/10 | 有官方文档和结构说明，但部分插件缺少详细使用指南 |
| 社区活跃度 | ⭐ 9.5/10 | 20K Stars，667 Issues，社区生态爆发式增长 |

**综合得分：8.9 / 10**

> Anthropic 官方出品，AI 编程工具生态化的关键基础设施。20K Stars 证明开发者对标准化插件系统的强烈需求。MCP 协议的开放性和双轨制的包容性为生态增长奠定了坚实基础。当前处于 Public Beta 阶段，生态正在快速成熟中。

---

*分析时间：2026-05-20 | GitHub Trending Deep Analyzer*
