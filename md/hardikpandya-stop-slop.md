# Stop Slop — GitHub Trending 深度分析

> **分析日期**: 2026-05-26 | **仓库**: [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | **作者**: Hardik Pandya | **许可证**: MIT

---

## 项目简介

**Stop Slop** 是一个精心设计的 `SKILL.md` 技能文件，专门用于教会 Claude（或任何 LLM）识别并消除 AI 写作中的典型模式。这些"AI 味"包括可预测的措辞、公式化的结构、机械的节奏感——让文本读起来就像机器写的。

项目名称中的 "Slop" 指的是 AI 生成内容中那些千篇一律、空洞无物的表达方式，即所谓的"AI 腔"。

### 核心功能

- **禁用词组检测** — 清除 100+ 个 AI 高频使用的空洞短语（"Here's the thing"、"Let that sink in"等）
- **结构化问题修复** — 打破二元对比、否定列举、戏剧化碎片等公式化结构
- **文体评分系统** — 5 维度量化评分（直接性、节奏、信任感、真实性、信息密度），低于 35/50 分自动要求修订
- **前后对比示例** — 提供丰富的 Before/After 改写案例，直观展示效果

---

## 技术架构

项目采用极简的纯 Markdown 架构，不依赖任何代码运行时。核心是结构化的提示工程（Prompt Engineering），通过分层参考文件实现精准控制。

```
stop-slop/
├── SKILL.md                 # 核心指令文件（8条写作规则 + 快速检查清单 + 评分体系）
├── references/
│   ├── phrases.md           # 禁用词组库（100+ 条目，分 7 大类）
│   ├── structures.md        # 结构化问题库（11 种模式，含修正建议）
│   └── examples.md          # 5 组 Before/After 对比示例
├── README.md
└── LICENSE                  # MIT
```

### 设计亮点

- **零依赖** — 纯文本 Skill 文件，无需安装任何包或工具
- **通用兼容** — 支持 Claude Code、Claude Projects、Cursor、API 调用等多种使用方式
- **分层架构** — 核心规则与参考库分离，按需加载
- **可量化** — 首创 5 维评分体系，让"去 AI 味"从主观感觉变成可衡量指标

---

## 8 条核心规则

| 规则 | 描述 |
|------|------|
| 1. 删废话词组 | 移除开场废话、强调词垫、所有副词 |
| 2. 破公式结构 | 避免二元对比、否定列举、戏剧碎片、修辞套路 |
| 3. 用主动语态 | 每句话需要一个人类主语在做某事 |
| 4. 要具体 | 不用模糊声明，命名具体事物 |
| 5. 让读者在场 | 不用旁白视角，"你"比"人们"好 |
| 6. 变化节奏 | 混合句子长度，不用破折号 |
| 7. 信任读者 | 直接陈述事实，不搞手把手 |
| 8. 砍金句 | 听起来像引用句的，重写它 |

---

## 评分体系

| 维度 | 问题 | 分数 (1-10) |
|------|------|-------------|
| 直接性 | 是陈述还是宣告？ | — |
| 节奏 | 多样还是机械？ | — |
| 信任感 | 尊重读者智力吗？ | — |
| 真实性 | 听起来像人写的吗？ | — |
| 信息密度 | 有可删内容吗？ | — |

**总分低于 35/50 则需要修订。**

---

## Before / After 示例

### 示例 1
**Before:**
> "Here's the thing: building products is hard. Not because the technology is complex. Because people are complex. Let that sink in."

**After:**
> "Building products is hard. Technology is manageable. People aren't."

### 示例 2
**Before:**
> "In today's fast-paced landscape, we need to lean into discomfort and navigate uncertainty with clarity. This matters because your competition isn't waiting."

**After:**
> "Move faster. Your competition is."

### 示例 3
**Before:**
> "What if I told you that the best teams don't optimize for productivity? Here's what I mean: they optimize for learning. Think about it."

**After:**
> "The best teams optimize for learning, not productivity."

---

## 应用场景

- **内容创作** — 博客、社论、Newsletter 等 AI 辅助写作的"去 AI 味"工序
- **商业文档** — 报告、提案、邮件等 AI 生成的商务文本润色
- **技术文档** — README、API 文档、技术博客的 AI 辅助撰写后优化
- **学术写作** — 论文润色（衍生项目 skill-deslop 专攻此领域）
- **营销文案** — 社交媒体帖子、广告文案的 AI 生成内容去套路化
- **代码审查辅助** — AI 生成的 commit message、PR 描述优化

---

## 为什么火 (Trending 原因)

Stop Slop 精准击中了 2026 年 AI 写作生态的最大痛点：**人人都在用 AI 写东西，但人人都讨厌读 AI 写的东西。**

1. **痛点刚需** — AI 写作的"套路感"已成为普遍认知，市场需求巨大
2. **即插即用** — 零门槛使用，复制 SKILL.md 到 Claude Project 即可生效
3. **Skill 生态红利** — 正值 Claude Code Skills 生态爆发期，首批高质量写作类 Skill
4. **KOL 传播** — Anand Chowdhary、Jesse Warden 等技术圈 KOL 推荐
5. **衍生生态** — 激发了 skill-deslop 等衍生项目，形成反 AI Slop 小生态
6. **话题性** — "AI 写作痕迹"本身是引发广泛讨论的社会话题
7. **简洁高效** — 结构清晰、规则明确、示例直观

---

## 同类项目对比

| 项目 | 定位 | 使用方式 | 覆盖范围 |
|------|------|----------|----------|
| **stop-slop** | 通用 AI 写作痕迹消除 | Claude Skill / Prompt | 词组+结构+节奏（最全面） |
| stephenturner/skill-deslop | 学术写作去 AI 味 | Claude Skill | 专注科学论文场景 |
| Kagi SlopStop | 搜索引擎 AI 内容检测 | Kagi 搜索集成 | 社区驱动标记 |
| AI Writing Detox | 营销团队去 AI 味指南 | 方法论文档 | 策略层面 |

**Stop Slop 的差异化优势**：覆盖最全面的通用 AI 写作痕迹消除工具，100+ 禁用词组、11 种结构化问题、5 维评分、Before/After 示例，极简架构兼容所有 LLM。

---

## 适合谁使用

| 用户类型 | 使用场景 | 推荐指数 |
|----------|----------|----------|
| 内容创作者 / 博主 | AI 辅助写作后润色去痕迹 | ★★★★★ |
| Claude Code 用户 | 作为 Skill 加载，自动优化输出 | ★★★★★ |
| 产品经理 / 市场营销 | AI 商业文案去套路化 | ★★★★ |
| 开发者 | 优化 README、文档、commit message | ★★★★ |
| 学术研究者 | 论文润色（推荐衍生版 skill-deslop） | ★★★ |

---

## 快速上手

### 1. 克隆仓库
```bash
git clone https://github.com/hardikpandya/stop-slop.git
```

### 2. Claude Code 集成
将 stop-slop 文件夹添加为 Claude Code 的 Skill 目录。每次生成文本时，Claude 会自动应用这些规则。

### 3. Claude Projects 集成
将 `SKILL.md` 和 `references/` 目录上传到项目知识库。写作或编辑文本时自动生效。

### 4. API 调用
将 `SKILL.md` 内容包含在 system prompt 中。参考文件可按需加载。

### 5. 自定义指令
从 `SKILL.md` 复制核心规则，粘贴到你的 CLAUDE.md 或 .cursorrules 文件中。

---

## 综合评分

| 维度 | 分数 | 评价 |
|------|------|------|
| 创新性 | **8/10** | 将"去 AI 味"系统化为可复用 Skill，5 维评分设计精巧 |
| 代码质量 | **8/10** | 结构清晰、分类严谨、示例精当 |
| 实用性 | **9.5/10** | 直击痛点，零门槛，即插即用 |
| 文档完善度 | **9/10** | README 清晰、参考文件分层合理、示例直观 |
| 社区活跃度 | **8.5/10** | Trending、KOL 推荐、衍生项目、Reddit 讨论 |

### 总分：43 / 50 — 强烈推荐

---

*分析由 GitHub Trending Analyzer 生成 | 2026-05-26*
