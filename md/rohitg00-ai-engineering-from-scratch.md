# 深度分析: rohitg00/ai-engineering-from-scratch

> 分析日期: 2026-05-21 | Stars: 9.5k | Forks: 1.9k | License: MIT

## 项目简介

**AI Engineering from Scratch** 是由 Rohit Ghumare 发起的开源 AI 工程学习课程，口号是 "Learn it. Build it. Ship it for others."

核心理念：84% 的学生已在用 AI 工具，但只有 18% 觉得自己准备好了专业使用。这个课程要填补这个缺口。

- **435 节课程**、**20 个阶段**、约 **320 小时**学时
- 支持 **Python / TypeScript / Rust / Julia** 四种语言
- 每节课从原始数学推导开始，手写实现，再引入生产框架
- 每节课产出可复用工具：Prompt、Skill、Agent 或 MCP Server
- MIT 开源，完全免费

## 核心功能

1. **从零构建的方法论** — 先用纯数学推导算法，手写代码实现，最后才用 PyTorch/sklearn
2. **可交付的工具产出** — 每节课不只学习，还产出可安装到 Claude/Cursor 的 skill
3. **渐进式 20 阶段路径** — 数学基础 → ML → 深度学习 → Transformer → LLM → Agent → 多智能体
4. **AI 代理生态集成** — 内置 `/find-your-level` 水平测试和 `/check-understanding` 阶段测验
5. **SkillKit 工具链** — 一键安装 373 个 skills 和 99 个 prompts 到 AI 编码代理

## 技术架构

### 课程结构（六步法）

每节课遵循：Motto → Problem → Concept → **Build It** → **Use It** → **Ship It**

```
phases/<NN>-<phase-name>/<NN>-<lesson-name>/
├── code/      # 可运行实现 (Python, TypeScript, Rust, Julia)
├── docs/
│   └── en.md  # 课程讲义
└── outputs/   # 产出的 prompt / skill / agent / MCP server
```

### 20 个学习阶段

| Phase | 主题 | 课程数 |
|-------|------|--------|
| 0 | Setup & Tooling | 12 |
| 1 | Math Foundations | 22 |
| 2 | ML Fundamentals | 18 |
| 3 | Deep Learning Core | 13 |
| 4 | Computer Vision | 28 |
| 5 | NLP Foundations | 29 |
| 6 | Speech & Audio | 17 |
| 7 | Transformers Deep Dive | 14 |
| 8 | Generative AI | 14 |
| 9 | Reinforcement Learning | 12 |
| 10 | LLMs from Scratch | 22 |
| 11 | LLM Engineering | 15 |
| 12 | Multimodal AI | 25 |
| 13 | Tools & Protocols (MCP, A2A) | 23 |
| 14 | Agent Engineering | 42 |
| 15 | Autonomous Systems | 22 |
| 16 | Multi-Agent & Swarms | 25 |
| 17 | Infrastructure & Production | 28 |
| 18 | Ethics & Alignment | 30 |
| 19 | Capstone Projects | 17 |

### 技术栈

- Python 80.8% / JavaScript 10.5% / HTML 6.1% / CSS 0.8% / Julia 0.7% / TypeScript 0.7%
- 配套网站部署在 Vercel
- GitHub Actions CI 自动校验课程目录一致性

## 应用场景

| 场景 | 对应阶段 | 说明 |
|------|---------|------|
| AI 入门系统学习 | Phase 0-3 | 从环境搭建到神经网络核心 |
| 计算机视觉工程师 | Phase 4 | CNN → ViT → Diffusion → 3D Vision |
| NLP / LLM 工程师 | Phase 5, 7, 10, 11 | 词嵌入 → Transformer → RAG → MCP |
| Agent 开发者 | Phase 14, 16 | Agent Loop → LangGraph → Multi-Agent |
| AI 基础设施工程师 | Phase 17 | vLLM、SGLang、GPU 调度 |
| AI 安全研究员 | Phase 18 | RLHF、红队测试、越狱防御 |

## 为什么火（Trending 原因）

1. **精准定位市场缺口** — 84% 使用 AI vs 18% 准备好，直击痛点
2. **"从零构建"方法论** — 不同于 fast.ai 的自顶向下，自底向上真正理解原理
3. **每节课产出可复用工具** — 不只是学习，还产出可安装的 skill/prompt/MCP
4. **覆盖 2026 年前沿** — DeepSeek-V3、EAGLE-3、MCP、A2A 等最新技术
5. **社区驱动力** — ByteByteGo 推荐、LinkedIn/X 大量分享、55k+ 月访问量

## 同类项目对比

| 项目 | Stars | 课程量 | 方法 | 产出物 | 语言 |
|------|-------|--------|------|--------|------|
| **ai-engineering-from-scratch** | **9.5k** | **435** | 自底向上 | **Skills+Prompts+MCP** | **4种** |
| rasbt/LLMs-from-scratch | ~50k | ~30 chapters | 自底向上 | 代码笔记 | Python |
| microsoft/ai-agents-for-beginners | ~15k | ~10 lessons | 自顶向下 | 示例代码 | Python |
| fast.ai | ~26k | ~7 courses | 自顶向下 | 代码笔记 | Python |

**核心差异**: 工具化产出（每个 lesson 都有可安装的 skill/prompt）+ 覆盖广度（数学到 Agent Swarm 完整链路）+ AI 代理生态深度集成。

## 适合谁使用

| 背景 | 起始阶段 | 预计学时 |
|------|---------|---------|
| 编程 + AI 新手 | Phase 0 | ~306h |
| 会 Python 的 ML 新手 | Phase 1 | ~270h |
| 了解 ML 的 DL 新手 | Phase 3 | ~200h |
| 懂 DL 想学 LLM/Agent | Phase 10 | ~100h |
| 资深工程师专攻 Agent | Phase 14 | ~60h |

## 快速上手

**方式一：在线阅读**（零安装）
访问 [aiengineeringfromscratch.com](https://aiengineeringfromscratch.com)

**方式二：克隆运行**
```bash
git clone https://github.com/rohitg00/ai-engineering-from-scratch.git
cd ai-engineering-from-scratch
python phases/01-math-foundations/01-linear-algebra-intuition/code/vectors.py
```

**方式三：水平测试**
```bash
# 在 Claude / Cursor / Codex 中运行
/find-your-level              # 10题定位起始阶段
/check-understanding 3        # 测验 Phase 3 理解度
```

**安装 Skills 到 AI 代理**
```bash
python3 scripts/install_skills.py ~/.claude/skills     # 全部安装
python3 scripts/install_skills.py ./out --phase 14      # 只装 Agent 阶段
python3 scripts/install_skills.py ./out --tag rag       # 按标签过滤
```

## 综合评分

| 维度 | 评分 | 评价 |
|------|------|------|
| 创新性 | **9.0/10** | 工具化产出 + AI 代理生态集成是独特卖点 |
| 代码质量 | **8.8/10** | 标准化结构 + CI 校验 + catalog 自动化 |
| 实用性 | **9.5/10** | 每节课都有可交付工具，覆盖完整链路 |
| 文档完善度 | **9.2/10** | README 详尽，每课有讲义，配套网站齐全 |
| 社区活跃度 | **8.5/10** | 9.5k stars，活跃 PR/Issue，社区持续增长 |

### 综合评分: **9.0 / 10** — 强烈推荐

---

*数据来源: [GitHub](https://github.com/rohitg00/ai-engineering-from-scratch) | [官方网站](https://aiengineeringfromscratch.com)*
