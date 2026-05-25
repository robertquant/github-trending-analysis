# MiroFish 深度分析报告

> **简洁通用的群体智能引擎，预测万物**
> A Simple and Universal Swarm Intelligence Engine, Predicting Anything

| 属性 | 详情 |
|------|------|
| 项目 | 666ghj/MiroFish |
| Stars | ~61.4K (GitHub 全球排名 #290) |
| 语言 | Python + Vue 3 |
| 许可证 | AGPL-3.0 |
| 作者 | BaiFu (666ghj) |
| 背书 | 盛大集团战略投资孵化 |
| 日期 | 2026-05-25 |

---

## 项目简介与核心功能

MiroFish 是一个基于多智能体（Multi-Agent）技术的下一代 AI 预测引擎。它从现实世界中提取种子信息（如突发新闻、政策草案、金融信号或小说文本），自动构建一个高保真的平行数字世界。在这个世界中，数千个拥有独立个性、长期记忆和行为逻辑的智能体自由交互并进行社会演化。

**核心理念：** 在数字沙盒中预演未来，通过无数次模拟赢得决策。

**工作流程：**
1. **图谱构建：** 种子提取 & 个体/集体记忆注入 & GraphRAG 构建
2. **环境搭建：** 实体关系提取 & 人设生成 & Agent 配置注入
3. **模拟运行：** 双平台并行模拟 & 自动解析预测需求 & 动态时间记忆更新
4. **报告生成：** ReportAgent 配合丰富工具集深度交互
5. **深度交互：** 与模拟世界中任何 Agent 对话 & 与 ReportAgent 交互

---

## 技术架构与特点

- **多智能体社会模拟：** 创建数千个具有独立人格、长期记忆和行为逻辑的 AI Agent，模拟真实社会复杂交互
- **GraphRAG 图谱构建：** 基于图结构的检索增强生成，构建知识图谱支持复杂推理
- **种子信息提取：** 从新闻、政策、金融信号等真实数据中提取关键信息
- **双平台并行模拟：** 多维度并行预测，提高预测准确度
- **上帝视角变量注入：** 动态注入变量，精确推导未来轨迹
- **OASIS 引擎驱动：** 底层基于 CAMEL-AI 团队的 OASIS（Open Agent Social Interaction Simulations）框架

**技术栈：** Python 3.11+, Vue 3, Node.js 18+, LLM API (OpenAI格式), Zep Cloud, Docker

---

## 应用场景

- **宏观层面 — 决策者预演实验室：** 零风险测试政策、公关策略
- **微观层面 — 个人创意沙盒：** 推演小说结局、探索想象力场景
- **舆情预测：** 基于真实新闻事件模拟公众舆论走向
- **文学创作：** 推演经典文学遗失结局（如红楼梦后40回）
- **金融预测：** 基于市场信号模拟市场走势
- **政治新闻预测：** 模拟政策变化对社会影响

---

## 为什么火（Trending 原因）

1. **概念极具颠覆性：** "预测万物"的愿景打破了传统预测工具的局限性
2. **传奇故事加持：** 大四学生 BaiFu 仅用约 10 天 "vibe coded" 出此项目
3. **资本追捧：** 上线 24 小时内获陈天桥（盛大集团）3000 万人民币投资
4. **登顶 GitHub 全球 Trending #1：** 超越 OpenAI、Google、Microsoft 等巨头项目
5. **Demo 震撼：** 武汉大学舆情模拟、红楼梦遗失结局推演直观展示潜力
6. **时机精准：** Multi-Agent 是当前 AI 最热门方向之一

---

## 同类项目对比

| 项目 | 核心定位 | 技术路线 | 适用场景 | 独特优势 |
|------|---------|---------|---------|---------|
| **MiroFish** | 群体智能预测引擎 | Multi-Agent + GraphRAG | 舆情/金融/文学预测 | 通用预测，上帝视角交互 |
| Generative Agents (Stanford) | 社会行为模拟 | LLM + 记忆架构 | 学术研究 | 学术验证，论文支撑 |
| AgentSociety | 大规模社会模拟 | Multi-Agent | 社会科学研究 | 大规模社会网络模拟 |
| ChatDev | 虚拟软件公司 | Multi-Agent 协作 | 软件开发自动化 | 聚焦软件开发流程 |
| MetaGPT | 多智能体框架 | SOP 驱动 Multi-Agent | 通用任务协作 | 角色扮演 + SOP |

---

## 适合谁使用

- **AI 研究者：** 探索多智能体社会模拟和群体智能涌现
- **数据分析师/决策者：** 预测舆情走向、政策影响
- **金融从业者：** 多维度模拟市场走势
- **创作者/作家：** 用 AI 推演故事走向
- **开源爱好者：** 对 Multi-Agent 技术感兴趣的开发者

---

## 快速上手指南

**前置条件：** Node.js 18+, Python 3.11-3.12, uv 包管理器

```bash
# 1. 克隆项目
git clone https://github.com/666ghj/MiroFish.git
cd MiroFish

# 2. 配置环境变量
cp .env.example .env
# 编辑 .env 填入 LLM API Key 和 Zep API Key

# 3. 一键安装依赖
npm run setup:all

# 4. 启动服务
npm run dev

# 或使用 Docker 部署
docker compose up -d
```

前端访问 http://localhost:3000，后端 API http://localhost:5001
推荐使用阿里云通义千问 qwen-plus 模型，支持任何 OpenAI SDK 格式的 LLM API

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | **9.5/10** | "预测万物"理念在 AI 领域独树一帜，群体智能涌现概念前沿 |
| 代码质量 | **7.5/10** | 10天作品，架构清晰，但仍有优化空间 |
| 实用性 | **8.0/10** | 应用场景广泛，从决策支持到创意沙盒 |
| 文档完善度 | **8.5/10** | 双语文档，Quick Start 清晰，Demo 视频完整 |
| 社区活跃度 | **9.0/10** | 61K+ Stars，Discord/QQ 社区活跃，盛大集团背书 |

**总评：42.5 / 50** — MiroFish 在创新性上表现卓越。作为大四学生的 10 天作品，代码质量和文档水平令人印象深刻。盛大集团的投资背书和 61K+ Stars 证明了社区的高度认可。项目潜力巨大，值得持续关注。

---

## 相关链接

- GitHub: https://github.com/666ghj/MiroFish
- 配套项目: https://github.com/666ghj/BettaFish
- 深度技术解析: https://zhuanlan.zhihu.com/p/2016788410640135889
- 视频演示: https://www.bilibili.com/video/BV1VYBsBHEMY/
- TrendShift: https://trendshift.io/repositories/16144

---

*分析日期：2026-05-25 | 由 AI 深度分析生成*
