# ECC (Everything Claude Code) - 深度分析

> **Agent Harness 性能优化系统** — 为 Claude Code、Codex、Cursor、OpenCode 等 AI 编码代理提供完整的 Skills、Instincts、Memory、Security 和 Research-First 开发能力。

| 指标 | 数值 |
|------|------|
| Stars | 182K+ |
| Forks | 28K+ |
| Contributors | 170+ |
| Agents | 61 |
| Skills | 246 |
| Commands | 76 |
| 语言生态 | 12+ |
| License | MIT |

---

## 项目简介

ECC (Everything Claude Code) 是由 **Affaan Mustafa** 创建的开源 Agent Harness 性能优化系统，源自 Anthropic × Cerebral Valley 黑客松获奖作品。

它不仅仅是一个配置集合，而是一套完整的 Agent 运行时增强系统：

- **Skills（技能）**：246 个工作流定义和领域知识模块，覆盖前端、后端、安全、测试、DevOps、ML 等
- **Agents（代理）**：61 个专业化子代理，用于任务委派（planner、reviewer、TDD、security 等）
- **Hooks（钩子）**：基于事件的自动化触发器，支持 PreToolUse/PostToolUse/Stop 等事件
- **Rules（规则）**：跨语言的编码规范和最佳实践，涵盖 12+ 语言生态
- **Instincts（本能）**：基于置信度评分的持续学习系统
- **Memory（记忆）**：跨会话的上下文持久化和自动加载
- **AgentShield（安全审计）**：1282 个测试、102 条静态分析规则的配置安全扫描器

经过 10+ 个月的高强度日常使用和多个生产应用验证。

---

## 技术架构

### 核心技术栈

| 技术 | 用途 |
|------|------|
| Shell / Bash | 安装脚本和 Hook 脚本 |
| TypeScript / Node.js | 核心脚本、测试、包管理器 |
| Python | Dashboard GUI (Tkinter) |
| Go | 语言特定规则 |
| Java | Spring Boot / Quarkus 规则 |
| Perl | 模式和安全规则 |
| Rust | ECC 2.0 控制平面原型 |
| Markdown | Agent、Skill、Command 定义 |

### 架构特点

- **Plugin-first 设计**：支持 `/plugin install` 一键安装
- **DRY Adapter 模式**：Cursor 复用 Claude Code Hook 脚本
- **选择性安装**：Manifest 驱动的组件选择安装
- **跨平台**：Windows / macOS / Linux 全覆盖
- **Hook 运行时控制**：`ECC_HOOK_PROFILE` 环境变量控制严格度
- **包管理器自动检测**：npm/pnpm/yarn/bun 自动识别
- **SQLite 状态存储**：安装状态追踪和增量更新
- **ECC 2.0 Rust 控制平面**：dashboard/start/sessions/daemon

---

## 应用场景

1. **日常编码**：使用 Planner Agent 规划功能，TDD Agent 驱动测试先行，Code Reviewer 自动检查代码质量
2. **安全审计**：AgentShield 扫描配置漏洞，Security Reviewer 执行 OWASP Top 10 审计，支持红蓝对抗模式
3. **多语言项目**：12+ 语言规则覆盖（TypeScript/Python/Go/Java/PHP/Swift/Perl/Kotlin/C++/Rust），按需安装
4. **团队协作**：Instinct 导入/导出实现团队知识共享，Skill 从 Git 历史中提取最佳实践
5. **CI/CD 集成**：AgentShield 可集成到 CI 流水线，Quality Gate 验证覆盖率和安全检查
6. **ML/MLOps**：PyTorch Build Resolver、MLE Reviewer、MLE Workflow 覆盖从训练到部署全链路

---

## 为什么火（Trending 原因）

1. **AI Agent 生态爆发**：2025-2026 年 AI 编码代理全面普及，Claude Code 用户量激增，ECC 是该生态中最全面的开源配置系统
2. **182K+ Stars 的飞轮效应**：庞大的社区基础带来了持续贡献（170+ contributors），形成了正向循环
3. **跨工具通用性**：不绑定单一工具，支持 Claude Code / Cursor / Codex / OpenCode / Copilot 等 7+ 平台
4. **Anthropic 黑客松获奖背书**：官方认可增强了用户信任度
5. **高频迭代**：v1.2 到 v2.0-rc.1 的快速演进，每周发版
6. **解决真实痛点**：Token 优化、上下文管理、安全扫描等功能直击 AI 编码日常核心痛点
7. **AgentShield 安全工具**：内置的安全扫描器（1282 测试、102 规则）是同类项目中少有的专业级安全工具
8. **完善的商业模式**：OSS 免费核心 + Pro 付费增值，可持续的维护模式

---

## 同类项目对比

| 项目 | 覆盖平台 | Skills | Agents | 安全扫描 | Stars |
|------|----------|--------|--------|----------|-------|
| **ECC (本项目)** | **7+ 平台** | **246** | **61** | **AgentShield** | **182K+** |
| anthropics/skills | Claude Code | ~20 | - | - | ~10K |
| addyosmani/agent-skills | Claude Code | ~30 | - | - | ~5K |
| obra/superpowers | Claude Code | ~15 | - | - | ~3K |
| mattpocock/skills | Claude Code | ~10 | - | - | ~2K |

ECC 在覆盖广度、深度和差异化功能上均显著领先。

---

## 适合谁使用

### 非常适合

- **Claude Code 日常用户** — 想要提升 Agent 编码效率和代码质量
- **多工具切换的开发者** — 在 Claude Code、Cursor、Codex 之间切换工作
- **团队技术负责人** — 希望统一团队编码规范和最佳实践
- **安全敏感项目** — 需要自动化安全审计和漏洞扫描
- **全栈开发者** — 需要多语言（TS/Python/Go/Java 等）的 Skill 支持

### 可能不太适合

- **纯 Vim/Emacs 用户** — 不使用 AI 编码代理的配置系统
- **极简主义者** — 246 个 Skills 可能显得过于庞大
- **非 Claude Code 生态** — 虽支持多平台但核心优化面向 Claude Code
- **网络受限环境** — 安装和 MCP 服务器配置需要稳定的网络

---

## 快速上手

### 1. 安装插件（推荐方式）

```bash
# 添加市场源
/plugin marketplace add https://github.com/affaan-m/ECC

# 安装插件
/plugin install ecc@ecc
```

### 2. 安装规则文件（手动）

```bash
git clone https://github.com/affaan-m/ECC.git
cd ECC
mkdir -p ~/.claude/rules/ecc
cp -R rules/common ~/.claude/rules/ecc/
cp -R rules/typescript ~/.claude/rules/ecc/  # 按需选择语言
```

### 3. 开始使用

```bash
# 规划功能
/ecc:plan "Add user authentication"

# TDD 工作流
# 使用 tdd-workflow skill

# 代码审查
/code-review

# 安全扫描
/security-scan

# Dashboard GUI
npm run dashboard
```

---

## 优缺点分析

### 优势
- 覆盖面极广：246 Skills + 61 Agents + 12+ 语言
- 跨平台支持：7+ AI 编码工具
- 安全扫描器 AgentShield 是独有亮点
- 持续学习系统（Instincts）自动化知识积累
- 社区活跃：170+ 贡献者，每周迭代
- Token 优化指南帮助降低成本
- MIT 开源，可自由使用和修改

### 不足
- 规模庞大，初学者可能感到 overwhelmed
- 安装路径多（Plugin/Manual/NPX），容易混淆
- 多次安装叠加会导致重复配置问题
- Pro 功能需要付费，部分高级功能受限
- Hook 系统在 v2.1+ 有 breaking change 风险
- ECC 2.0 Rust 控制平面尚在 alpha 阶段

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 9.0/10 | 首个跨 7+ AI 编码工具的统一配置系统，Instinct 持续学习、AgentShield 安全审计等独特功能 |
| 代码质量 | 8.5/10 | 997+ 内部测试通过，多语言支持，但规模大导致部分模块维护难度较高 |
| 实用性 | 9.5/10 | 直接解决 AI 编码日常核心痛点，Token 优化和安全扫描价值极高 |
| 文档完善度 | 9.0/10 | 详细的 README、多语言指南、安装向导、Longform Guide |
| 社区活跃度 | 10/10 | 182K+ Stars、170+ Contributors、每周发版、30+ 社区 PR |

### 综合评分：9.2 / 10 — 顶级开源项目

---

## 关键链接

- GitHub 仓库：https://github.com/affaan-m/ECC
- npm 包：https://www.npmjs.com/package/ecc-universal
- AgentShield：https://www.npmjs.com/package/ecc-agentshield
- 作者 Twitter：https://x.com/affaanmustafa
- ECC Tools (Pro)：https://github.com/marketplace/ecc-tools

---

*Generated on 2026-05-26 | GitHub Trending Deep Analysis*