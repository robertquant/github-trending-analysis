# Medusa — The World's Most Flexible Commerce Platform

> **GitHub**: [medusajs/medusa](https://github.com/medusajs/medusa) | **Stars**: 33,296 (+200) | **语言**: TypeScript | **协议**: MIT

---

## 项目简介

Medusa 是一个开源的无头（Headless）电商平台，被誉为"开源版 Shopify"。它提供构建数字商务所需的全部基础模块，同时赋予开发者 100% 的代码和数据所有权。Medusa v2 引入了全新的模块化架构和 Workflows 引擎，代表了现代电商平台的设计方向。

---

## 核心功能

| 模块 | 说明 |
|------|------|
| 产品管理 | 多品类、多变体、多仓库产品目录 |
| 购物车与结账 | 灵活购物车引擎，自定义结账流程 |
| 订单管理 | 完整生命周期：退货、换货、索赔 |
| 支付集成 | Stripe、PayPal 等，可扩展自定义 |
| 配送物流 | 多仓库、多承运商、实时费率 |
| 促销引擎 | 百分比/固定/买赠等灵活规则 |
| 国际化 | 多货币、多语言原生支持 |
| B2B 功能 | 企业定价、批量订单、公司账户 |
| Workflows | 声明式业务编排引擎 |
| Admin | 全新现代化管理后台 |

---

## 技术架构

```
┌─────────────────────────────────┐
│        Storefront (Next.js)      │  ← 任何前端框架
├─────────────────────────────────┤
│     Medusa Admin Dashboard       │  ← 管理后台
├─────────────────────────────────┤
│   REST API + GraphQL + Medusa JS │  ← API 层
├─────────────────────────────────┤
│   Workflows & Modules Engine     │  ← 业务编排
├─────────────────────────────────┤
│  Product | Cart | Order | Payment │  ← 商务模块
│  Shipping | Pricing | Inventory  │
├─────────────────────────────────┤
│    Database (PostgreSQL) + Redis  │  ← 数据层
└─────────────────────────────────┘
```

**技术特点**:
- 全栈 TypeScript，类型安全
- 模块化设计，每个能力独立 npm 包
- Workflows 声明式编排复杂业务
- API-First：REST + GraphQL 双协议
- 丰富的插件生态
- Docker 一键部署

---

## 应用场景

- **DTC 品牌电商** — 高度定制的消费者购物体验
- **B2B 批发平台** — 企业采购、定制定价
- **多商户市场** — 多卖家平台（类 Amazon）
- **POS 系统** — 线上线下库存同步
- **国际电商** — 多区域、多币种运营
- **AI 驱动电商** — API-First 天然适配 AI Agent

---

## 为什么火（Trending 原因）

1. **反供应商锁定** — 企业越来越重视数据主权和平台独立性
2. **Medusa v2 重大升级** — 模块化 + Workflows + 全新 Admin
3. **Medusa Cloud 上线** — 官方托管降低部署门槛
4. **AI 时代的电商底座** — API-First 设计适配 AI Agent
5. **成本优势** — 相比 Shopify Plus 零授权费、零交易手续费
6. **社区爆发** — 33K+ Stars，14K+ Discord 成员
7. **开发者优先** — TypeScript 全栈对现代开发者极具吸引力

---

## 同类项目对比

| 维度 | Medusa | Shopify | Saleor | WooCommerce |
|------|--------|---------|--------|-------------|
| 开源 | MIT | 闭源 | 开源 | 开源 |
| 技术栈 | TypeScript/Node | Ruby/Liquid | Python/GraphQL | PHP/WordPress |
| Headless | 原生 | 需 Hydrogen | 原生 | 需插件 |
| 定制灵活性 | 极高 | 受限 | 高 | 中等 |
| 成本 | 免费（自建） | $39-$2000+/月 | 免费（自建） | 免费（需主机） |
| B2B | 原生 | Plus 版 | 原生 | 需插件 |
| Stars | 33K+ | N/A | 21K+ | 9K+ |
| 数据所有权 | 100% 自有 | 平台持有 | 100% 自有 | 100% 自有 |

**核心优势**: Medusa 在"灵活性 + 开发体验"之间取得最佳平衡。Saleor 基于 Python 对 JS 开发者不友好；WooCommerce 受限于 WordPress；Shopify 不开源。

---

## 适合谁使用

- 熟悉 TypeScript/React/Next.js 的全栈/前端开发者
- 预算有限、需要快速 MVP 的创业团队
- 受够了 Shopify 高交易费和受限定制的品牌
- 需要 B2B 复杂定价和批量订单的企业
- 为多客户构建定制方案的电商代理商
- 需要可编程电商 API 的 AI 产品团队

**不太适合**: 没有技术团队的传统商家、不懂代码的小白用户。

---

## 快速上手

```bash
# 1. 创建项目
npx create-medusa-app@latest

# 2. 启动开发服务
cd my-medusa-store
npm run dev
# 后端: http://localhost:9000
# Admin: http://localhost:7001
# 店面: http://localhost:8000
```

自定义 Workflow 示例:

```typescript
import { createWorkflow, WorkflowResponse } from "@medusajs/framework/workflows-sdk"
import { createProductStep } from "./steps/create-product"

export const customCreateProductWorkflow = createWorkflow(
  "custom-create-product",
  (input) => {
    const product = createProductStep(input)
    return new WorkflowResponse(product)
  }
)
```

部署方式:
- Medusa Cloud（官方托管）
- Docker Compose 自部署
- Vercel（店面）+ Railway/Render（后端）

---

## 综合评分

| 维度 | 评分 |
|------|------|
| 创新性 | 9.0/10 |
| 代码质量 | 9.0/10 |
| 实用性 | 9.5/10 |
| 文档完善度 | 8.5/10 |
| 社区活跃度 | 9.0/10 |
| **综合评价** | **9.0/10** |

> Medusa 是目前开源电商领域的最佳选择之一。v2 的模块化架构和 Workflows 引擎代表了现代电商平台的设计方向，TypeScript 全栈和 API-First 的设计理念使其成为 AI 时代的电商基础设施首选。

---

*GitHub Trending 深度分析 | 2026-05-18*