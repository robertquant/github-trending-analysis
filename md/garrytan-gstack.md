# garrytan/gstack — GitHub Trending 深度分析

> **分析日期**: 2026-05-26 | **Stars**: 96K+ | **语言**: TypeScript / Shell | **许可证**: MIT

---

## 基本信息

| 项目 | 详情 |
|------|------|
| **名称** | garrytan/gstack |
| **描述** | Y Combinator CEO 的 AI 编程工作流 — 将 Claude Code 变成虚拟工程团队 |
| **Stars** | 96,190+ |
| **Forks** | 9,100+ |
| **语言** | TypeScript / Shell |
| **许可证** | MIT |
| **作者** | Garry Tan (Y Combinator President & CEO) |
| **开源日期** | 2026-03-12 |
| **版本** | v0.19+ |

**标签**: `AI Coding Agent` `Claude Code` `Workflow Framework` `Multi-Agent` `Browser Automation` `Open Source`

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | ⭐ 9.5/10 | 首个完整 AI 工程工作流框架，23 角色分工协作 |
| **代码质量** | ⭐ 8.5/10 | TypeScript 架构清晰，多平台支持，快速迭代中 |
| **实用性** | ⭐ 9.5/10 | 30秒安装，5步上手，覆盖从构思到部署全链路 |
| **文档完善度** | ⭐ 9.0/10 | 超5000字 README，每个技能有独立深度文档 |
| **社区活跃度** | ⭐ 9.8/10 | 96K+ Stars，35+ 贡献者，全平台热议 |

**总评：9.3 / 10** — AI 辅助开发工作流的标杆级项目

---

## 项目简介与核心功能

**gstack** 是 Y Combinator 总裁兼 CEO **Garry Tan** 的个人 AI 辅助开发工作流开源项目。它将 Anthropic 的 Claude Code CLI 工具转变为一个完整的虚拟工程团队，通过 **23 个精心设计的专家角色技能**（slash commands），覆盖从产品构思到部署上线的完整软件开发生命周期。

**核心理念：** 一个人 + AI 工具 = 一个完整的工程团队。Garry Tan 在 60 天内兼职交付了 3 个生产级服务、40+ 个功能，同时全职管理 Y Combinator。他声称 2026 年的有效代码产出率是 2013 年的 **810 倍**。

### Sprint 工作流模型

```
Think → Plan → Build → Review → Test → Ship → Reflect
```

1. **Think（思考）** — `/office-hours` 六个关键问题重构产品思路
2. **Plan（规划）** — `/plan-ceo-review` CEO 级战略审视 + `/plan-eng-review` 工程架构审查
3. **Build（构建）** — 基于设计文档和计划自动生成代码
4. **Review（审查）** — `/review` 高级工程师级代码审查
5. **Test（测试）** — `/qa` 用真实浏览器做端到端测试
6. **Ship（发布）** — `/ship` 自动化 PR 创建和测试运行
7. **Reflect（复盘）** — `/retro` 工程经理级迭代回顾

---

## 技术架构与特点

**技术栈：** TypeScript（核心逻辑）/ Shell（安装脚本）/ Bun v1.0+（运行时）/ Playwright（浏览器自动化）/ Chromium（无头浏览器）/ Supabase（遥测可选）

### 关键架构特点

1. **技能链式传递** — 每个技能的输出自动成为下游技能的输入。`/office-hours` 的设计文档被 `/plan-ceo-review` 读取，`/plan-eng-review` 的测试计划被 `/qa` 继承
2. **多 Agent 协调** — 通过 `/pair-agent` 实现跨 AI 代理（Claude、OpenClaw、Codex、Cursor）的浏览器共享和任务协调
3. **真实浏览器集成** — 基于 Playwright 的 `/browse` 技能提供真实 Chromium 浏览器操作，支持 Cookie 导入、反检测和截图
4. **GBrain 持久记忆** — 基于 PGLite/Supabase 的跨会话知识库，让 AI 代理在不同会话间保持对项目的理解
5. **安全防御层** — 内置 OWASP Top 10 安全审计（`/cso`）、22MB ML 分类器的 Prompt 注入防护、安全护栏（`/careful`/`/freeze`）
6. **跨平台支持** — 不仅支持 Claude Code，还支持 Codex CLI、Cursor、OpenCode、Kiro、Slate 等 10 种 AI 编程工具
7. **并行 Sprint** — 可同时运行 10-15 个并行开发会话，每个会话独立隔离
8. **GStack Browser** — 定制 Chromium 浏览器，带侧边栏 AI 助手、反机器人检测、智能模型路由

---

## 核心 Skills 一览

| 技能 | 角色 | 功能 |
|------|------|------|
| `/office-hours` | YC Office Hours | 6 个关键问题重构产品思路 |
| `/plan-ceo-review` | CEO / Founder | 战略级产品审视（4 种范围模式） |
| `/plan-eng-review` | Eng Manager | 架构锁定、数据流图、测试矩阵 |
| `/plan-design-review` | Senior Designer | 0-10 分设计评审 + AI Slop 检测 |
| `/plan-devex-review` | DX Lead | 开发者体验审查（20-45 个关键问题） |
| `/review` | Staff Engineer | 发现 CI 通过但生产会爆的 bug |
| `/qa` | QA Lead | 真实浏览器测试 + 自动修复 + 回归测试 |
| `/ship` | Release Engineer | 同步 main → 测试 → 覆盖率 → PR |
| `/cso` | CSO | OWASP Top 10 + STRIDE 威胁建模 |
| `/design-shotgun` | Design Explorer | 生成 4-6 原型变体 + 浏览器对比 |
| `/design-html` | Design Engineer | 设计稿 → 生产级 HTML（30KB 零依赖） |
| `/browse` | QA Engineer | 真实 Chromium 浏览器操作 |
| `/autoplan` | Review Pipeline | 一键 CEO → 设计 → 工程 → DX 审查 |
| `/codex` | Second Opinion | OpenAI Codex 独立代码审查 |
| `/retro` | Eng Manager | 团队周回顾 + 统计分析 |
| `/pair-agent` | Coordinator | 跨 AI 代理共享浏览器 |
| `/careful` | Safety Guard | 破坏性命令警告 |
| `/freeze` | Edit Lock | 限制文件编辑范围 |
| `/document-release` | Tech Writer | 自动更新所有项目文档 |
| `/investigate` | Debugger | 系统化根因调试 |
| `/benchmark` | Perf Engineer | 页面加载 + Core Web Vitals 基准测试 |
| `/canary` | SRE | 部署后监控循环 |
| `/learn` | Memory | 跨会话学习和记忆管理 |

---

## 应用场景

- **独立开发者 / Solo Founder** — 一个人像 20 人团队一样运作，从产品构思到部署上线全流程覆盖
- **YC 风格创业公司** — 2-3 人的早期团队用 AI 代理加速 MVP 迭代
- **技术型 CEO / 创始人** — 在管理公司之余仍能高效产出产品代码
- **Staff Engineer / Tech Lead** — 为每个 PR 提供系统化的代码审查、QA 测试和安全审计
- **开源项目维护者** — 自动化文档更新、测试生成和代码审查流程
- **设计工程师** — 从设计探索（/design-shotgun）到生产 HTML（/design-html）的完整工作流
- **多 AI 代理协调** — 通过 /pair-agent 实现不同 AI 工具之间的协作

---

## 为什么火 (Trending 原因)

### 11 天 39K Stars，6 周 85K+ Stars — 2026 年 GitHub 增长最快项目之一

1. **Garry Tan 的个人影响力** — 作为 Y Combinator CEO，他背书并亲自使用的工具自带极高信任度
2. **切中 AI 编程核心痛点** — 解决了"知道 AI 能写代码，但不知道怎么组织"的普遍困惑
3. **"一人=团队"的病毒叙事** — "810 倍生产力"和"兼职 60 天 3 个生产服务"极具传播力
4. **Andrej Karpathy 加持** — README 开头引用 Karpathy 言论，关联 AI 编程革命叙事
5. **MIT 完全免费开源** — 没有高级版、没有等待列表、没有 SaaS 订阅
6. **覆盖多种 AI 工具** — 支持 10 种 AI 编程工具，受众范围极广
7. **YC 生态系统推动** — 25% 的 YC 公司 95% 代码由 AI 编写，gstack 被定位为标准工具

---

## 同类项目对比

| 维度 | gstack | anthropics/skills | addyosmani/agent-skills | mattpocock/skills |
|------|--------|-------------------|------------------------|-------------------|
| **定位** | **完整工程团队工作流** | Anthropic 官方技能示例 | 通用 AI 编程技巧集合 | TypeScript 工程实践 |
| **角色数量** | **23+ 专家角色** | ~5 个基础技能 | ~10 个实用技能 | ~8 个工程技能 |
| **工作流覆盖** | **思考→发布全链路** | 单一任务 | 部分覆盖 | 部分覆盖 |
| **浏览器自动化** | **完整（反检测+QA）** | 无 | 基础 | 无 |
| **跨 AI 工具** | **10 种** | 仅 Claude Code | 仅 Claude Code | 仅 Claude Code |
| **持久记忆** | **GBrain** | 无 | 无 | 无 |
| **安全审计** | **OWASP+STRIDE+ML** | 无 | 基础 | 无 |
| **并行工作** | **10-15 并行 Sprint** | 无 | 无 | 无 |
| **Stars** | **~96K** | ~15K | ~8K | ~5K |

**差异化：** gstack 的核心优势不在于单个技能深度，而在于将 23 个角色串联成完整的工程工作流，配合真实浏览器、持久记忆、跨 AI 工具支持，是目前最完整的 AI 辅助开发框架。

---

## 适合谁使用

| 适合度 | 用户类型 | 理由 |
|--------|----------|------|
| ⭐⭐⭐ 强烈推荐 | 创始人和 CEO | 技术型创始人仍想亲自交付产品 |
| ⭐⭐⭐ 强烈推荐 | 首次使用 Claude Code | 结构化角色代替空白提示词 |
| ⭐⭐⭐ 强烈推荐 | Tech Lead / Staff Eng | 系统化审查、QA 和安全审计 |
| ⭐⭐ 适合 | 独立开发者 / 开源维护者 | 自动化文档、测试、多项目并行 |
| ⭐⭐ 适合 | 设计工程师 | 设计探索到生产 HTML 完整流水线 |
| ⭐ 需评估 | 企业大团队 | 需评估与现有 CI/CD 集成兼容性 |

---

## 快速上手指南

### 前置条件

- Claude Code
- Git
- Bun v1.0+（Windows 还需要 Node.js）

### 30 秒安装

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack
cd ~/.claude/skills/gstack && ./setup
```

### 5 步体验完整工作流

```bash
/office-hours          # Step 1: 描述你要构建什么
/plan-ceo-review       # Step 2: CEO 级战略审视
/plan-eng-review       # Step 3: 工程架构审查
/review                # Step 4: 代码审查（有代码变更后）
/ship                  # Step 5: 发布
```

### 团队模式（推荐）

```bash
(cd ~/.claude/skills/gstack && ./setup --team) && \
~/.claude/skills/gstack/bin/gstack-team-init required && \
git add .claude/ CLAUDE.md && git commit -m "require gstack"
```

> **提示：** 首次使用建议从 `/office-hours` 开始。如果你只想快速体验，在一个有代码变更的分支上运行 `/review` 即可。

---

## 关键数据

- Garry Tan 2026 年 GitHub 贡献：1,237+（对比 2013 年的 772）
- 2026 年有效代码产出率：2013 年的 ~810 倍（基于逻辑代码变更而非原始 LOC）
- 2026 年截至 4 月 18 日产出：2013 年全年的 240 倍
- 25% 的当前 YC 批次公司：95% 的代码由 AI 编写
- 支持 10 种 AI 编程工具：Claude Code、Codex CLI、Cursor、OpenCode、Factory Droid、Slate、Kiro、Hermes、GBrain、OpenClaw

---

## 参考链接

- [GitHub 仓库](https://github.com/garrytan/gstack)
- [YC 官方介绍](https://www.ycombinator.com/library/OW-inside-garry-tan-s-ai-coding-setup)
- [Reddit 讨论](https://www.reddit.com/r/ClaudeAI/comments/1s7jdof/garry_tan_opensourced_gstack_his_personal_skill/)
- [Hacker News 讨论](https://news.ycombinator.com/item?id=47418576)
- [Towards AI 分析](https://pub.towardsai.net/gstack-garry-tans-claude-code-setup-that-turns-one-developer-into-a-full-engineering-team-2026-02854a569730)

---

*分析日期：2026-05-26 | 数据来源：GitHub、WebSearch、Reddit、Hacker News*
