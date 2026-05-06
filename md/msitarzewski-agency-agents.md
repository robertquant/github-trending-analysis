# The Agency: AI Agent Orchestration Platform

> **GitHub**: [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents)
> **作者**: Michael Sitarzewski (30+ 年开发经验，Startup 创始人，Techstars 校友)
> **语言**: Shell (安装脚本) / Markdown (Agent 定义)
> **许可证**: MIT
> **Stars**: 91,960 ⭐ | 今日新增: +828 ⭐
> **分析日期**: 2026-05-05

---

## 📋 项目简介

**The Agency** 是一个精心策划的 AI Agent 人格集合库，包含 **144+ 个专业 AI Agent**，覆盖 **12 个专业部门**。每个 Agent 都具有独特的个性特征、专业领域知识、完整工作流程和明确的可交付成果。

项目源自 Reddit 的 r/ClaudeAI 社区讨论，经过数月迭代，已发展为 AI Agent 人格管理领域的重要开源项目。发布 12 小时内就收到 50+ 功能请求，目前拥有超过 10,000 行的 Agent 人格、工作流和代码示例定义。

核心区别：**不是 Prompt 模板合集，而是一整套经过实战验证的专业 AI 团队体系。**

---

## 🎯 核心功能

### 1. 专业化 Agent 系统
- 每个 Agent 具有深度领域专业知识，而非通用 Prompt
- 独特的个性、沟通风格和工作方式
- 明确的可交付成果和成功度量标准
- 经过实战验证的工作流和质量标准

### 2. 12 个专业部门

| 部门 | Agent 数量 | 主要角色 |
|------|-----------|---------|
| 💻 工程部 | 27 | 前端/后端/移动端/AI/DevOps/安全/嵌入式 等 |
| 🎨 设计部 | 8 | UI/UX/品牌/视觉叙事/包容性设计 |
| 💰 付费媒体部 | 7 | PPC/搜索分析/审计/追踪/创意策略 |
| 💼 销售部 | 9 | 外呼/探索/交易策略/销售工程/提案 |
| 📢 市场营销部 | 28 | 内容/社交/SEO/小红书/B站/抖音/微信 等 |
| 📊 产品部 | 5 | Sprint 优先级/趋势研究/反馈/行为科学 |
| 🎬 项目管理部 | 6 | 制片/协调/运营/实验/工作流 |
| 🧪 测试部 | 8 | 证据收集/质量门禁/性能/无障碍审计 |
| 🛟 支持部 | 6 | 客服/分析/财务/基础设施/合规 |
| 🥽 空间计算部 | 6 | XR/Vision Pro/WebXR/终端集成 |
| 🎮 游戏开发部 | 17 | Unity/Unreal/Godot/Roblox/Blender |
| 📚 学术部 | 5 | 人类学/地理/历史/叙事学/心理学 |

### 3. 多工具集成
支持 11+ 主流 AI 编码工具的一键部署：
- Claude Code, GitHub Copilot, Cursor, Windsurf
- Gemini CLI, Antigravity, OpenCode, OpenClaw
- Aider, Qwen Code, Kimi Code

### 4. 中国本地化
- 社区维护的简体中文翻译版（141 个翻译 Agent + 46 个中国本地化原创 Agent）
- 覆盖小红书、B站、抖音、微信、知乎、微博等平台的专业 Agent

---

## 🏗️ 技术架构

```
Agent 定义文件 (Markdown)
    │
    ├── 身份与个性 (Identity & Personality)
    ├── 核心使命 (Core Mission)
    ├── 关键规则 (Critical Rules)
    ├── 技术交付物 (Technical Deliverables)
    ├── 工作流过程 (Workflow Process)
    └── 成功指标 (Success Metrics)
    │
    ▼
convert.sh ─── 格式转换引擎
    │
    ├── .md → Claude Code / Copilot / OpenCode 原生格式
    ├── .md → .mdc (Cursor rules)
    ├── .md → SKILL.md (Antigravity / Gemini CLI)
    ├── .md → CONVENTIONS.md (Aider)
    ├── .md → .windsurfrules (Windsurf)
    ├── .md → SOUL.md + AGENTS.md (OpenClaw)
    ├── .md → YAML (Kimi Code)
    └── .md → SubAgent .md (Qwen Code)
    │
    ▼
install.sh ─── 交互式安装器
    │
    ├── 自动检测已安装工具
    ├── 交互式选择 UI
    ├── 支持 --parallel 并行安装
    └── 支持 --no-interactive CI 模式
    │
    ▼
目标工具目录
    ├── ~/.claude/agents/          (Claude Code)
    ├── ~/.github/agents/          (GitHub Copilot)
    ├── .cursor/rules/             (Cursor)
    └── ... 其他工具对应目录
```

### 技术栈
- **核心语言**: Shell (Bash 脚本)
- **Agent 定义**: Markdown
- **安装脚本**: Bash (支持并行处理)
- **格式转换**: Bash 脚本自动生成
- **许可证**: MIT

---

## 📖 应用场景

### 场景 1：创业 MVP 快速开发
- **团队**: Frontend Developer + Backend Architect + Growth Hacker + Rapid Prototyper + Reality Checker
- **成果**: 每个阶段都有专业 AI 支撑，显著加速交付

### 场景 2：多渠道营销活动
- **团队**: Content Creator + Twitter Engager + Instagram Curator + Reddit Community Builder + Analytics Reporter
- **成果**: 多平台协同作战，平台专属策略优化

### 场景 3：付费媒体账户接管
- **团队**: Paid Media Auditor + Tracking Specialist + PPC Strategist + Search Query Analyst + Creative Strategist
- **成果**: 30 天内完成系统化账户重构与优化

### 场景 4：跨部门产品探索
- **团队**: 8 个部门同时协作
- **成果**: 综合性、跨职能的产品蓝图，单次会话完成

---

## 🔥 为什么火 (Trending 原因)

1. **AI Agent 时代的基础设施**: 随着 AI 编码工具爆发式增长，开发者急需标准化的 Agent 定义和部署方案。The Agency 填补了这个空白，成为 AI Agent 人格管理的"事实标准"。

2. **极致的多工具兼容**: 支持 11+ 主流 AI 编码工具，用户不需要绑定单一工具链。convert.sh + install.sh 的一键转换安装体验极其流畅。

3. **社区驱动 + 中国本地化**: 源自 Reddit 社区讨论，天然具备社区基因。社区贡献了简体中文翻译版，覆盖小红书、B站、微信等平台，极大扩展了受众。

4. **不只是 Prompt — 是完整的"员工"**: 每个 Agent 有个性、工作流、交付物、成功指标。这不是 Prompt 工程，更像是"AI 代理人才市场"的蓝图。

5. **低门槛高回报**: 克隆仓库、运行一行命令即可使用。无需编程，复制 .md 文件就能获得专业 AI 辅助。

---

## 🔄 同类项目对比

| 特性 | The Agency | awesome-chatgpt-prompts | LangChain Agents | Claude Code 内置 |
|------|-----------|------------------------|-----------------|----------------|
| Agent 数量 | 144+ 个 | ~160 个 Prompt | 框架级 | 系统级 |
| 个性与人格 | ✅ 深度定制 | ⚡ 基础角色 | ❌ 无 | ❌ 无 |
| 工作流定义 | ✅ 完整流程 | ❌ 无 | ✅ Chain 模式 | ⚡ 有限 |
| 多工具支持 | ✅ 11+ 平台 | ❌ 仅 ChatGPT | ✅ Python 生态 | ❌ 仅 Claude |
| 可交付物定义 | ✅ 含代码示例 | ❌ 无 | ⚡ 工具输出 | ❌ 无 |
| 成功指标 | ✅ 每个 Agent | ❌ 无 | ❌ 无 | ❌ 无 |
| 中国本地化 | ✅ 社区翻译 | ⚡ 部分 | ❌ 无 | ❌ 无 |
| 使用门槛 | 极低（复制即用） | 极低 | 高（需编程） | 低 |

---

## 👥 适合谁使用

- **独立开发者 / Indie Hacker**: 一人企业也能拥有完整的"AI 团队"，从开发到营销全覆盖
- **初创团队**: 用 AI Agent 补充人力资源不足，快速迭代产品
- **AI 工具重度用户**: 使用 Claude Code / Cursor / Copilot 等工具，希望提升 AI 辅助质量
- **营销 / 销售从业者**: 利用专业化 Agent 提升工作效率，特别是在社交媒体运营方面
- **游戏开发者**: 17 个游戏开发 Agent 覆盖 Unity、Unreal、Godot、Roblox 全引擎
- **中国市场运营者**: 原生支持小红书、B站、抖音、微信、知乎等平台 Agent

---

## 🚀 快速上手

### 方式一：Claude Code（推荐）

```bash
# 克隆仓库
git clone https://github.com/msitarzewski/agency-agents.git
cd agency-agents

# 一键安装所有 Agent 到 Claude Code
./scripts/install.sh --tool claude-code

# 在 Claude Code 中激活 Agent
# "Hey Claude, activate Frontend Developer mode and help me build a React component"
```

### 方式二：多工具安装

```bash
# 生成所有工具的集成文件
./scripts/convert.sh

# 交互式安装（自动检测已安装工具）
./scripts/install.sh

# 或指定特定工具
./scripts/install.sh --tool cursor
./scripts/install.sh --tool copilot
./scripts/install.sh --tool aider

# 并行安装，更快
./scripts/install.sh --no-interactive --parallel
```

### 方式三：手动使用

```bash
# 只复制你需要的 Agent
cp engineering/*.md ~/.claude/agents/

# 或直接浏览 Agent 定义文件作为参考
# 每个文件包含：身份、使命、规则、交付物、工作流、成功指标
```

---

## 📊 项目数据

- **Stars**: 91,960
- **今日新增**: +828
- **Agent 总数**: 144+
- **部门数量**: 12
- **支持工具**: 11+
- **代码行数**: 10,000+ (Agent 定义)
- **许可证**: MIT

---

## 🔗 相关资源

- [GitHub 仓库](https://github.com/msitarzewski/agency-agents)
- [中文翻译版 (agency-agents-zh)](https://github.com/jnMetaCode/agency-agents-zh) — 141 翻译 + 46 中国本地化原创
- [中文翻译版 (agent-teams)](https://github.com/dsclca12/agent-teams) — B站/微信/小红书本地化
- [r/ClaudeAI 社区讨论](https://www.reddit.com/r/ClaudeAI/)
