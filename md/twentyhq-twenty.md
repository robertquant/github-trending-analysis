# Twenty — #1 开源 CRM，Salesforce 的开放替代方案

> **GitHub**: [twentyhq/twenty](https://github.com/twentyhq/twenty) | **Stars**: 45,000+ | **许可**: AGPL-3.0 | **官网**: [twenty.com](https://twenty.com)

---

## 📋 项目简介

**Twenty** 是 GitHub 上 Star 数最多的开源 CRM 项目，定位为 Salesforce 的开放替代方案。它为技术团队提供构建自定义 CRM 的全套模块——对象、视图、工作流和智能体，支持以代码方式定义和版本管理。

### 核心功能

- **对象定义即代码** — 通过 TypeScript SDK 定义数据模型、字段和视图
- **可自定义管道视图** — 销售管道、看板视图灵活配置
- **工作流自动化** — Webhook + 自动化工作流引擎
- **AI Agent 集成** — 原生 MCP (Model Context Protocol) 支持
- **自托管 / 云部署** — Docker Compose 一键部署或使用托管云
- **CLI 脚手架** — `npx create-twenty-app` 快速创建应用

---

## 🏗️ 技术架构

| 层级 | 技术 | 说明 |
|------|------|------|
| 前端 | React + TypeScript | 现代化 SPA，精美 UI |
| 后端 | NestJS + GraphQL | 模块化架构，强类型 API |
| 数据库 | PostgreSQL | 企业级关系型数据库 |
| 部署 | Docker Compose | 容器化部署，便于自托管 |
| AI | MCP 协议 | 原生 AI Agent 集成 |

### 架构亮点

- **"CRM as Code"** — 数据模型、视图、工作流全部代码化，可纳入 Git 管理
- **GraphQL API** — 灵活的数据查询接口，前后端解耦
- **AI-First** — 原生支持 MCP，可无缝集成 AI Agent
- **插件化设计** — 通过 CLI 和 SDK 构建自定义应用

```typescript
import { defineObject, FieldType } from 'twenty-sdk/define';

export default defineObject({
  nameSingular: 'deal',
  namePlural: 'deals',
  fields: [
    { name: 'name', label: 'Name', type: FieldType.TEXT },
    { name: 'amount', label: 'Amount', type: FieldType.CURRENCY },
    { name: 'closeDate', label: 'Close Date', type: FieldType.DATE_TIME },
  ],
});
```

---

## 🎯 应用场景

| 场景 | 描述 |
|------|------|
| 中小企业 CRM | 替代 Salesforce/HubSpot，零成本起步，完全掌控数据 |
| AI 驱动销售 | 利用 MCP 协议集成 AI Agent，智能客户分析和自动跟进 |
| 定制化 CRM | 技术团队用代码完全定制业务逻辑，不受 SaaS 限制 |
| SaaS 产品底座 | 基于 Twenty 构建垂直行业 CRM 产品 |
| 数据平台 | 作为客户数据的 Single Source of Truth |
| 隐私合规 | 自托管满足 GDPR 等数据隐私合规要求 |

---

## 🔥 为什么火 (Trending 原因)

1. **Salesforce 替代的巨大市场** — 企业 CRM 市场规模数百亿美元，用户苦于高价和复杂度久矣
2. **AI-First 设计理念** — 原生 MCP 支持让 Twenty 成为 AI 增强型 CRM 的先行者
3. **"CRM as Code" 范式** — 技术团队终于可以用开发软件的方式管理 CRM
4. **TechCrunch 等主流媒体报道** — 2024 年 11 月获 TechCrunch 专题报道
5. **社区爆发式增长** — 45,000+ Stars，两年内成为 GitHub 上最火的开源 CRM
6. **开发者友好体验** — CLI + SDK + 精美 UI，上手体验远超同类

---

## ⚖️ 同类项目对比

| 项目 | Stars | 许可 | 技术栈 | AI 集成 | 自托管 |
|------|-------|------|--------|---------|--------|
| **Twenty** | 45,000+ | AGPL-3.0 | React + NestJS + GraphQL | ✅ MCP 原生 | ✅ Docker |
| Odoo | 42,000+ | LGPL-3.0 | Python + PostgreSQL | ⚠️ 有限 | ✅ Docker |
| Monica CRM | 22,000+ | AGPL-3.0 | PHP + Laravel | ❌ | ✅ |
| Huly | 18,000+ | Elastic-2.0 | TypeScript + React | ⚠️ 有限 | ✅ Docker |
| Erxes | 3,500+ | GPLv3 | React + Node.js | ❌ | ✅ Docker |

---

## 👥 适合谁使用

- **初创团队** — 需要灵活、免费的 CRM，有能力自行部署维护
- **技术型 SMB** — 有开发团队，希望深度定制 CRM 匹配业务
- **AI 产品团队** — 需要 AI-Ready 的 CRM 底座构建智能销售工具
- **隐私合规企业** — 必须自托管客户数据，满足 GDPR/SOC2
- **SaaS 创业者** — 基于 Twenty 构建垂直行业 CRM 解决方案

---

## 🚀 快速上手

### 方式一：云部署（最快）

访问 [twenty.com](https://twenty.com) 注册，一分钟内创建工作区。

### 方式二：创建自定义应用

```bash
npx create-twenty-app my-app
```

使用 SDK 定义对象和字段，然后部署到工作区。

### 方式三：自托管部署

```bash
git clone https://github.com/twentyhq/twenty.git
cd twenty
docker compose up -d
```

### 参与社区

加入 [Discord](https://discord.gg/twenty) 获取帮助，在 GitHub Discussions 提问和贡献代码。

---

## 📊 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | ⭐ 9.0/10 | "CRM as Code" 理念独特，AI-First 设计领先 |
| 代码质量 | ⭐ 8.5/10 | TypeScript 全栈，架构清晰，测试完善 |
| 实用性 | ⭐ 9.0/10 | 直击企业 CRM 痛点，部署灵活 |
| 文档完善度 | ⭐ 8.0/10 | 官方文档齐全，SDK 示例丰富 |
| 社区活跃度 | ⭐ 9.5/10 | 45K+ Stars，Discord 活跃，贡献者众多 |

### 综合评分：8.8 / 10 — 强烈推荐关注

---

## 🔗 相关链接

- 📦 GitHub: [twentyhq/twenty](https://github.com/twentyhq/twenty)
- 🌐 官网: [twenty.com](https://twenty.com)
- 📖 文档: [docs.twenty.com](https://docs.twenty.com)
- 🗺️ 路线图: [GitHub Roadmap](https://github.com/twentyhq/twenty/projects)
- 💬 Discord: [Twenty Community](https://discord.gg/twenty)
- 🐦 Twitter/X: [@twentycrm](https://x.com/twentycrm)

---

*🤖 由 AI 自动分析生成 | 分析日期：2026-05-27 | Powered by Claude Code*
