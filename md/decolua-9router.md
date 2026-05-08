# 🔄 9Router 深度分析

> FREE AI Router & Token Saver — 40+ 提供商，100+ 模型，永远不断线

## 📊 基本信息

| 项目 | 详情 |
|------|------|
| 仓库 | decolua/9router |
| 语言 | JavaScript (Next.js 16 + React 19 + Tailwind CSS 4) |
| Stars | ⭐ 4,292 |
| 今日增长 | 🔥 +249 |
| 许可证 | MIT License |
| npm 包 | 9router |
| 运行环境 | Node.js 20+ |
| 默认端口 | localhost:20128 |

## 🏷️ 标签

`AI Router` `Token Saver` `RTK` `Multi-LLM` `Auto Fallback` `Next.js` `OpenAI Compatible` `Free AI` `Claude Code` `Codex` `Cursor` `40+ Providers`

---

## 1. 项目简介与核心功能

**9Router** 是一个开源的 AI 编码路由器和 Token 节省工具。它在本地运行代理服务，将 AI 编码工具（Claude Code、Codex、Cursor、Cline、Copilot、OpenClaw、Antigravity 等）的请求路由到 40+ AI 提供商，实现自动降级、Token 节省和零停机编码。

### 解决的核心痛点

- 订阅额度用不完就过期
- 编码中途被 Rate Limit 打断
- 工具输出（git diff、grep 等）快速消耗 Token
- 多个 AI 提供商之间手动切换麻烦
- API 费用昂贵（$20-50/月/提供商）

### 核心功能

- **RTK Token Saver**：自动压缩 tool_result 内容，每次请求节省 20-40% Token
- **Caveman Mode**：注入简洁提示，输出 Token 节省高达 65%
- **Smart 3-Tier Fallback**：订阅 → 廉价 → 免费，自动降级
- **Format Translation**：OpenAI ↔ Claude ↔ Gemini ↔ Cursor ↔ Kiro ↔ Vertex
- **Real-Time Quota Tracking**：Token 消耗追踪、重置倒计时、费用估算
- **Multi-Account Support**：每个提供商多账号，Round-Robin 或优先级路由
- **Auto Token Refresh**：OAuth Token 自动刷新
- **Custom Combos**：无限模型组合，混合订阅/廉价/免费层
- **Cloud Sync**：跨设备同步提供商、Combo、设置
- **Usage Analytics**：月度使用报告

---

## 2. 技术架构与特点

### 架构概览

```
CLI Tool (Claude Code / Codex / Cursor / Cline / Copilot)
    │
    ▼ http://localhost:20128/v1
9Router (Smart Router)
    ├── RTK Token Saver (cut tool_result)
    ├── Caveman Mode (terse output)
    ├── Format Translation (OpenAI↔Claude↔Gemini↔...)
    └── Quota Tracking + Auto Token Refresh
    │
    ├──→ [Tier 1: SUBSCRIPTION] Claude Code / Codex / Copilot / Cursor
    ├──→ [Tier 2: CHEAP] GLM ($0.6/1M) / MiniMax ($0.2/1M) / Kimi ($9/mo)
    └──→ [Tier 3: FREE] Kiro AI / OpenCode Free / Vertex AI ($300 credits)
```

### 技术栈

- **框架**：Next.js 16 + React 19 + Tailwind CSS 4
- **数据存储**：LowDB（本地 JSON）
- **认证**：OAuth 2.0 PKCE + JWT
- **通信**：SSE (Server-Sent Events)
- **部署**：localhost / VPS / Docker / Cloudflare Workers

### 三大降级层级

| 层级 | 提供商 | 费用 | 重置周期 |
|------|--------|------|----------|
| 🚀 订阅 | Claude Code Pro/Max, Codex Plus/Pro, GitHub Copilot | $20-200/月 | 5h + 每周 |
| 💰 廉价 | GLM-5.1, MiniMax M2.7, Kimi K2.5 | $0.2-0.6/1M | 5h/每日 |
| 🆓 免费 | Kiro AI, OpenCode Free, Vertex AI | $0 | 无限/90天 |

---

## 3. 应用场景

| 场景 | 说明 |
|------|------|
| 💻 日常 AI 编码 | 免费使用 Claude/GPT/Gemini 编写代码 |
| ⚡ 重度编码用户 | 3-Tier 降级保证 24/7 不间断 |
| 💰 成本优化 | RTK 省 20-40% Token + 免费层兜底 |
| 🏢 团队协作 | 多账号负载均衡 + 费用追踪 |
| 🎓 学习入门 | $0 门槛使用顶级 AI 模型 |
| 🔧 CI/CD 集成 | Docker/VPS 部署，API 模式接入 |

---

## 4. 为什么火（Trending 原因）

- **直击痛点**：AI 编码用户最头疼的问题 — 额度耗尽、Rate Limit、Token 浪费
- **真正的免费**：Kiro + OpenCode Free = $0 永久免费使用 Claude/GPT/Gemini
- **RTK 创新**：智能压缩 tool_result，20-40% Token 节省，行业首创
- **一键接入**：`npm install -g 9router`，两分钟配置完所有 AI 编码工具
- **万能兼容**：Claude Code / Codex / Cursor / Cline / Copilot 全支持
- **40+ 提供商**：覆盖所有主流 AI 模型
- **开发者友好**：MIT 开源、完善文档、Dashboard UI

---

## 5. 同类项目对比

| 维度 | **9Router** | Claude Code Router | One API | LiteLLM |
|------|-------------|-------------------|---------|---------|
| 开源 | **✅ MIT** | ✅ | ✅ | ✅ |
| Token 节省 (RTK) | **✅ 20-40%** | ❌ | ❌ | ❌ |
| 3-Tier 降级 | **✅ 自动** | 手动 | ✅ | ✅ |
| 免费提供商 | **✅ 3+** | ❌ | ❌ | ❌ |
| Dashboard UI | **✅ Next.js** | ❌ | ✅ | ❌ |
| 格式转换 | **✅ 9种** | Claude only | 部分 | ✅ |
| Quota 追踪 | **✅ 实时** | ❌ | ❌ | ❌ |
| 多账号 | **✅** | ❌ | ✅ | 部分 |
| Cloud Sync | **✅** | ❌ | ❌ | ❌ |
| 专为编码优化 | **✅** | ✅ | ❌ | ❌ |

**总结**：9Router 在 AI 编码场景的针对性最强 — RTK Token 节省、免费提供商接入、实时 Quota 追踪都是独家特性。

---

## 6. 适合谁使用

| 用户类型 | 推荐度 | 原因 |
|---------|-------|------|
| 👨‍💻 独立开发者 | ⭐⭐⭐⭐⭐ | 免费 Combo + RTK = 零成本 AI 编码 |
| 🏢 开发团队 | ⭐⭐⭐⭐⭐ | 多账号负载均衡 + 费用追踪 |
| 🎓 学生 / 学习者 | ⭐⭐⭐⭐⭐ | $0 入门门槛，免费使用顶级模型 |
| ⚡ 重度 AI 编码用户 | ⭐⭐⭐⭐⭐ | 3-Tier 降级保证 24/7 不间断 |
| 🔧 DevOps / SRE | ⭐⭐⭐⭐ | VPS/Docker/Cloudflare 灵活部署 |
| 💰 成本敏感企业 | ⭐⭐⭐⭐⭐ | RTK 省 20-40% + 免费层兜底 |

---

## 7. 快速上手指南

### 安装

```bash
npm install -g 9router
9router
# 访问 http://localhost:20128
```

### 连接免费提供商

Dashboard → Providers → Connect Kiro AI (免费 Claude 无限) 或 OpenCode Free (无需认证)

### 配置 Claude Code

```json
// ~/.claude/config.json
{
  "anthropic_api_base": "http://localhost:20128/v1",
  "anthropic_api_key": "your-9router-api-key"
}
```

### 推荐免费 Combo

```
Combo: "free-forever"
1. kr/claude-sonnet-4.5    (Claude 4.5 免费无限)
2. kr/glm-5                (GLM-5 免费通过 Kiro)
3. oc/<auto>               (OpenCode Free, 无需认证)
月费: $0 + RTK 省 20-40% Token
```

---

## 8. 综合评分

| 维度 | 评分 |
|------|------|
| 🧪 创新性 | **8.8** / 10 |
| 🔧 代码质量 | **8.0** / 10 |
| 🎯 实用性 | **9.5** / 10 |
| 📖 文档完善度 | **9.0** / 10 |
| 🌐 社区活跃度 | **7.8** / 10 |
| **综合评分** | **8.6 / 10** |

### ⭐ 实用性极高，推荐关注

---

## 📌 总结

9Router 是 AI 编码工具生态中的一个关键基础设施项目。它通过 RTK Token 节省、3-Tier 智能降级和 40+ 提供商接入，解决了 AI 编码用户最关心的三大问题：成本、中断和复杂性。对于想要零成本使用顶级 AI 模型的开发者来说，Kiro + OpenCode Free + RTK 的组合提供了目前市场上最实用的免费 AI 编码方案。MIT 开源许可、完善的文档和活跃的社区使其成为降低 AI 编码成本的首选工具。

---

📊 由 AI 深度分析生成 | Powered by Claude Code
分析日期：2026-05-08 | 数据来源：GitHub, WebSearch
