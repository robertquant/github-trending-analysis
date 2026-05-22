# dotnet/skills — .NET AI 编程代理技能库

> **Microsoft .NET 官方团队**推出的 AI 编程代理技能库，让 AI 编码助手真正理解 .NET 和 C#。

| 属性 | 信息 |
|---|---|
| **仓库** | [github.com/dotnet/skills](https://github.com/dotnet/skills) |
| **Stars** | ~2,450 |
| **Forks** | ~193 |
| **语言** | C# |
| **许可证** | MIT |
| **上线** | 2026 年 3 月 9 日 |
| **维护方** | Microsoft .NET 团队 |

---

## 项目简介

`dotnet/skills` 是 Microsoft .NET 官方团队开源的项目，为 AI 编程代理（GitHub Copilot、Claude Code、Cursor、Codex CLI 等）提供 .NET 和 C# 领域的专业知识包。

每一个"技能"（Skill）是一个结构化的知识包（以 `SKILL.md` 文件组织），包含意图识别、任务特定上下文和支持文件，使 AI 代理在处理 .NET 任务时做出更精准的决策，减少试错和幻觉。

## 包含的 12 个官方插件

| 插件 | 功能描述 |
|---|---|
| `dotnet` | 核心 .NET 技能集合，处理常见 .NET 编码任务 |
| `dotnet-data` | 数据访问与 Entity Framework 相关技能 |
| `dotnet-diag` | 性能调查、调试和事件分析 |
| `dotnet-msbuild` | MSBuild 构建：故障诊断、性能优化、代码质量、现代化 |
| `dotnet-nuget` | NuGet 包管理：依赖管理和现代化 |
| `dotnet-upgrade` | .NET 项目迁移升级：框架版本、语言特性、兼容性 |
| `dotnet-maui` | .NET MAUI 开发：环境配置、诊断和故障排除 |
| `dotnet-ai` | AI/ML 技能：LLM 集成、Agentic 工作流、RAG、MCP、ML.NET |
| `dotnet-template-engine` | 模板发现、项目脚手架、模板创作 |
| `dotnet-test` | 测试运行、诊断、迁移：MSTest 工作流 |
| `dotnet-aspnet` | ASP.NET Core：中间件、端点、实时通信、API 模式 |
| `dotnet11` | .NET 11 新 API 和语言特性技能 |

## 技术架构与特点

### 基于 Agent Skills 开放标准
项目遵循 [agentskills.io](https://agentskills.io) 开放标准，技能以 `SKILL.md` 文件格式组织，包含结构化的知识描述、工作流指引和最佳实践。

### 插件化架构
采用 Marketplace 插件市场模式，每个插件聚焦一个 .NET 子领域，用户可按需安装。支持多平台：
- **Copilot CLI / Claude Code** — 通过 `/plugin` 命令安装
- **VS Code** — Preview 支持，Copilot Chat 中输入 `/plugins`
- **Cursor** — 内置 Marketplace 支持
- **Codex CLI** — 使用 `skill-installer` 工具安装

### 持续集成与质量保障
每夜构建（nightly build），Dashboard 展示各插件的准确性和效率评分趋势。

## 应用场景

| 场景 | 使用的插件 | 效果 |
|---|---|---|
| .NET Framework 迁移到 .NET 10 | `dotnet-upgrade` | 准确识别迁移路径和破坏性变更 |
| EF Core 数据访问层开发 | `dotnet-data` | 生成符合最佳实践的代码 |
| MSBuild 构建故障排查 | `dotnet-msbuild` | 快速定位构建错误根因 |
| ASP.NET Core API 开发 | `dotnet-aspnet` | 遵循官方推荐模式 |
| 在 .NET 中集成 AI/LLM | `dotnet-ai` | 正确选择技术栈，实现 RAG/Agentic 工作流 |
| .NET MAUI 跨平台开发 | `dotnet-maui` | 环境配置和常见问题诊断 |

## 为什么火 (Trending 原因)

1. **官方团队出品** — 由实际发布 .NET 的 Microsoft 团队维护，知识权威性无可替代
2. **AI 编码的刚需** — 解决 AI 代理在 .NET 领域产生幻觉和过时代码的核心痛点
3. **开放标准生态** — 遵循 agentskills.io，不绑定单一平台
4. **时机精准** — 2026 年 AI Agent 大爆发，.NET 官方入场引发巨大关注
5. **覆盖全面** — 12 个插件覆盖 .NET 生态几乎所有核心领域
6. **社区热情** — 开源后迅速获得 ~2,450 Stars，Uno Platform 等社区已开始贡献

## 同类项目对比

| 维度 | dotnet/skills | anthropics/skills | flutter/skills | addyosmani/agent-skills |
|---|---|---|---|---|
| **维护方** | Microsoft .NET 团队 | Anthropic 官方 | Flutter 团队 | 社区个人 |
| **领域** | .NET / C# 专用 | Claude 通用 | Flutter 专用 | 前端通用 |
| **插件数** | 12 个官方插件 | 数十个技能 | Flutter 专项 | 聚合收集 |
| **标准** | agentskills.io | Claude Skills | agentskills.io | 混合 |
| **平台支持** | Copilot/Claude/Cursor/Codex | 主要是 Claude Code | 多平台 | 主要是 Claude |
| **质量把控** | 官方团队审核 + 自动评分 | 官方维护 | 官方维护 | 社区策展 |
| **上线时间** | 2026 年 3 月 | 2025 年 10 月 | 2026 年 | 2025 年 |

**独特优势**：dotnet/skills 是唯一由 .NET 发布团队直接维护的技能库，知识权威性和时效性（支持 .NET 11 预览特性）是其他项目无法复制的。

## 适合谁使用

| 用户类型 | 推荐度 | 原因 |
|---|---|---|
| .NET / C# 后端开发者 | ★★★★★ | 直接受益者，让 AI 编码助手产出更高质量代码 |
| 企业 .NET 团队 | ★★★★★ | 统一团队 AI 编码标准，减少低级错误 |
| .NET Framework 迁移者 | ★★★★★ | upgrade 插件精准指导迁移路径 |
| AI 应用开发者 (.NET) | ★★★★☆ | dotnet-ai 插件覆盖 LLM 集成、RAG、MCP 等 |
| 全栈开发者 (部分使用 .NET) | ★★★★☆ | 按需安装特定插件即可 |
| 非 .NET 开发者 | ★☆☆☆☆ | 领域特定，非 .NET 项目无直接价值 |

## 快速上手指南

### Claude Code / Copilot CLI

```bash
# 1. 添加 Marketplace
/plugin marketplace add dotnet/skills

# 2. 安装所需插件
/plugin install dotnet@dotnet-agent-skills
/plugin install dotnet-aspnet@dotnet-agent-skills

# 3. 重启加载插件

# 4. 更新插件（可选）
/plugin update dotnet@dotnet-agent-skills
```

### Codex CLI

```bash
skill-installer install https://github.com/dotnet/skills/tree/main/plugins/dotnet/skills/<skill-name>
```

### 推荐起步插件组合

| 开发场景 | 推荐安装 |
|---|---|
| 通用 .NET 开发 | `dotnet` + `dotnet-test` |
| Web API 开发 | + `dotnet-aspnet` + `dotnet-data` |
| 项目迁移 | + `dotnet-upgrade` + `dotnet-nuget` |
| AI 集成 | + `dotnet-ai` |

## 综合评分

| 维度 | 评分 | 说明 |
|---|---|---|
| 创新性 | 8.5/10 | Agent Skills 概念不新，但官方团队+开放标准的组合是创新点 |
| 代码质量 | 9.0/10 | 官方团队出品，自动化评分体系保障质量 |
| 实用性 | 9.5/10 | 直击 AI 编码在 .NET 领域的核心痛点 |
| 文档完善度 | 8.0/10 | README 清晰，但部分插件文档可更详细 |
| 社区活跃度 | 9.0/10 | 增长迅速，社区贡献涌现 |

**综合评分: 8.8 / 10**

## 参考资源

- [GitHub 仓库: dotnet/skills](https://github.com/dotnet/skills)
- [官方博客: Extend your coding agent with .NET Skills](https://devblogs.microsoft.com/dotnet/extend-your-coding-agent-with-dotnet-skills/)
- [Agent Skills 开放标准](https://agentskills.io)
- [Dashboard: 准确性和效率评分](https://dotnet.github.io/skills/)
- [Uno Platform: .NET Agent Skills 解析](https://platform.uno/articles/dotnet-agent-skills-ai-coding-agets/)

---

*Generated on 2026-05-23 | GitHub Trending Daily Analysis*