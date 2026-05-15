# garrytan/gstack — GitHub Trending 深度分析

> **分析日期**: 2026-05-15 | **Trending 排名**: #14 | **今日 Star**: +1,083

---

## 基本信息

| 项目 | 详情 |
|------|------|
| **名称** | garrytan/gstack |
| **描述** | Garry Tan 的 Claude Code 虚拟工程团队 — 23 个专家角色，一个命令召唤 |
| **Stars** | 96,190 |
| **今日增长** | +1,083 |
| **语言** | TypeScript / Shell |
| **许可证** | MIT |
| **作者** | Garry Tan (Y Combinator CEO & President) |

**标签**: `AI Coding Agent` `Claude Code` `Workflow Framework` `Multi-Agent` `Browser Automation`

---

## 项目简介

**gstack** 是 Y Combinator 总裁兼 CEO **Garry Tan** 开源的个人 Claude Code 工作流配置。它将单一的 Claude Code 助手转变为一个完整的虚拟工程团队 — 包含 CEO、设计师、工程经理、发布工程师、文档工程师和 QA 等多个专家角色。

Garry Tan 在过去 60 天内，以兼职方式（同时全职运营 YC），交付了 3 个生产级服务和 40+ 功能。他的 2026 年代码产出率比 2013 年提高了约 **810 倍**（按逻辑代码变更计算）。

### 核心功能

- **/office-hours** — YC 风格的办公室时间，6 个追问帮你重新定义产品
- **/plan-ceo-review** — CEO 视角审视功能范围，4 种模式：扩展/选择性扩展/保持/缩减
- **/plan-eng-review** — 工程经理锁定架构、数据流、边界情况
- **/review** — 高级工程师 Code Review，自动修复明显问题
- **/ship** — 发布工程师：同步 main、运行测试、审计覆盖率、推送 PR
- **/qa** — QA 负责人：真实浏览器测试、发现 Bug、自动修复并生成回归测试
- **/design-shotgun** — 设计探索器：生成 4-6 个 AI 设计变体，可视化对比选择
- **/design-html** — 设计工程师：将设计稿转为可交付的生产级 HTML
- **/cso** — 首席安全官：OWASP Top 10 + STRIDE 威胁模型审计
- **/codex** — 跨模型第二意见，调用 OpenAI Codex CLI 独立审查
- **/browse** — 真实浏览器控制，赋予 AI "眼睛"
- **/learn** — 跨会话记忆管理，系统随使用越来越聪明

---

## Sprint 工作流

gstack 不是工具集合，而是一套完整流程：

```
Think → Plan → Build → Review → Test → Ship → Reflect
```

每个技能按 Sprint 顺序执行，前一步的输出自动成为后一步的输入：

```bash
/office-hours          # → 生成设计文档
/plan-ceo-review       # → CEO 审视范围
/plan-eng-review       # → 锁定架构
# ... Claude 自动编写代码 ...
/review                # → Code Review + 自动修复
/qa https://staging... # → 真实浏览器 QA
/ship                  # → 测试 + 覆盖率 + PR
```

---

## 技术架构与特点

### 技术栈
- TypeScript / Shell / Bun Runtime / Playwright / Chrome DevTools Protocol

### 架构亮点

1. **角色化 Agent 架构** — 每个 Slash Command 对应一个专家角色，有明确的方法论和输出格式
2. **链式工作流** — 技能间自动传递上下文，形成完整生产线
3. **真实浏览器集成** — 基于 Playwright 的 Chromium 控制，~100ms/命令，支持 cookie 导入和反检测
4. **跨 Agent 兼容** — 支持 Claude Code、OpenAI Codex CLI、Cursor、Factory Droid、Kiro、Hermes 等 10 个 AI 编码工具
5. **GBrain 持久知识库** — 支持 PGLite 本地 / Supabase 云端，跨会话记忆积累
6. **跨模型审查** — /codex 调用 OpenAI Codex 独立审查，与 Claude 的 /review 交叉验证
7. **Conductor 并行调度** — 支持 10-15 个并行 Sprint 同时运行
8. **多层安全防御** — 22MB ML 分类器 + Haiku 转录检查 + 随机 Canaries + DeBERTa 集成
9. **Continuous Checkpoint** — 自动 WIP 提交，崩溃恢复，ship 时自动清理

---

## 应用场景

| 场景 | 说明 |
|------|------|
| **独立创始人** | 一个创始人完成从产品设计到发布上线的全流程，替代 20 人团队 |
| **初创 MVP 验证** | /office-hours → /autoplan → 编码 → /ship，数小时内完成 |
| **Code Review 自动化** | /review + /cso + /codex 三重审查，覆盖功能、安全、跨模型验证 |
| **设计协作** | /design-shotgun 可视化探索 → /design-html 转为生产代码 |
| **Claude Code 初学** | 结构化角色代替空白提示词，降低学习曲线 |
| **并行多项目** | Conductor 同时运行 10-15 个 Sprint |

---

## 为什么火 (Trending 原因)

1. **作者身份加持** — Garry Tan 作为 YC CEO，个人品牌影响力巨大
2. **Karpathy 背书** — README 引用"2025年12月以来我没写过一行代码"
3. **810× 生产力宣言** — 极具话题性和争议性
4. **时机完美** — 2026 年 AI Coding Agent 爆发元年，提供最佳实践
5. **实际可验证** — 3 个生产服务 + 40+ 功能的产出可查
6. **零门槛开源** — MIT 协议、纯 Markdown 技能、30 秒安装
7. **跨 Agent 生态** — 不绑定单一工具，覆盖面广
8. **社区讨论热烈** — HN、Reddit、Twitter 广泛讨论

---

## 同类项目对比

| 维度 | gstack | superpowers | mattpocock/skills | spec-kit |
|------|--------|-------------|-------------------|----------|
| **定位** | 全流程虚拟团队 | TDD 驱动方法论 | TS 最佳实践 | Spec 驱动开发 |
| **Stars** | 96K | 190K | 80K | 99K |
| **技能数** | 23 + 8 工具 | ~15 | ~10 | ~8 |
| **浏览器支持** | ✅ 完整 Chromium | ❌ | ❌ | ❌ |
| **跨 Agent** | ✅ 10 个工具 | ❌ 仅 Claude | ❌ 仅 Claude | ❌ 仅 Claude |
| **设计工作流** | ✅ 完整设计系统 | ❌ | ❌ | ❌ |
| **安全审计** | ✅ OWASP + STRIDE | 基础 | 基础 | 基础 |
| **并行 Sprint** | ✅ 10-15 并行 | 单会话 | 单会话 | 单会话 |

**gstack 差异化**: 完整 Sprint 流程 + 真实浏览器 QA + 跨 Agent 兼容 + 设计到部署全链路。

---

## 快速上手

### 前置要求
- Claude Code (Anthropic CLI)
- Git
- Bun v1.0+

### 30 秒安装

```bash
git clone --single-branch --depth 1 https://github.com/garrytan/gstack.git ~/.claude/skills/gstack && \
cd ~/.claude/skills/gstack && \
./setup
```

### 5 分钟体验

```
/office-hours           # 描述你要构建什么
/plan-ceo-review        # CEO 视角审视
/plan-eng-review        # 锁定架构
# ... Claude 自动写代码 ...
/review                 # Code Review
/qa https://your-app    # 浏览器 QA
/ship                   # 一键发布
```

### 团队模式

```bash
(cd ~/.claude/skills/gstack && ./setup --team) && \
~/.claude/skills/gstack/bin/gstack-team-init required && \
git add .claude/ CLAUDE.md && \
git commit -m "require gstack for AI-assisted work"
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | 9.0/10 | 角色化 Agent + Sprint 流程 + 并行调度，概念创新 |
| **代码质量** | 8.5/10 | 纯 Markdown 技能 + TypeScript 工具，结构清晰 |
| **实用性** | 9.5/10 | 解决真实问题，作者本人日用的工具 |
| **文档完善度** | 9.5/10 | README 极其详尽，含完整示例、对比、安装指南 |
| **社区活跃度** | 9.5/10 | 96K Stars，HN/Reddit 热议，多个第三方教程 |

### 综合评分：9.2 / 10

> gstack 代表了 AI 编码工具演进的下一个阶段 — 从单点辅助到完整工程流程自动化。它不是让你写代码更快，而是让你**不再需要写代码**，而是专注于产品决策和创意。

**风险提示**: 高度依赖 Claude Code 生态，浏览器安全分类器增加安装体积。810× 生产力数字存在争议但作者公开了完整方法论。

---

*分析由 AI 生成 · Powered by Claude Code*
