# revfactory/harness 深度分析摘要

**分析日期:** 2026-05-29 | **综合评分: 84/100**

## 项目定位

Claude Code 元技能（Meta-Skill）插件 —— 一句话自动生成专业 AI Agent 团队架构。位于 Claude Code 生态 L3 Meta-Factory / Team-Architecture Factory 子层。

## 核心亮点

- **六种架构模式:** Pipeline、Fan-out/Fan-in、Expert Pool、Producer-Reviewer、Supervisor、Hierarchical Delegation
- **零代码生成:** 输入自然语言描述，自动输出 `.claude/agents/` + `.claude/skills/` 配置
- **Progressive Disclosure:** 渐进式上下文管理，高效控制 token 消耗
- **A/B 验证:** +60% 质量提升(49.5→79.3)，15/15 胜率，-32% 输出方差

## 技术架构

六阶段工作流: 领域分析 → 团队架构设计 → Agent 定义生成 → 技能生成 → 集成编排 → 验证测试

## 生态

- **Harness-100:** 100 个预置配置（10 领域，EN/KO 双语）
- **Archon:** 同层不同子层（运行时配置工厂）
- **meta-harness:** Codex 移植版
- **ECC:** 上层标准化层

## 评分详情

| 维度 | 分数 |
|------|------|
| 创新性 | 92 |
| 实用性 | 85 |
| 技术深度 | 88 |
| 生态成熟度 | 70 |
| 社区活跃度 | 82 |
| 文档质量 | 90 |

## 推荐指数: 4/5

对 Claude Code 用户是必试项目；跨平台需求需等待生态扩展。

---
*详细 HTML 报告见: reports/revfactory-harness-2026-05-29.html*
