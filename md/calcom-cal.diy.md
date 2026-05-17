# Cal.diy — GitHub Trending 深度分析报告

> **Scheduling infrastructure for absolutely everyone.**

| 指标 | 数据 |
|------|------|
| Stars | 43,065 |
| 今日新增 | +425 |
| 语言 | TypeScript (95.8%) |
| 许可证 | MIT |
| Forks | 13,400+ |
| 提交数 | 16,438 |
| Release | 611 |

---

## 📋 项目简介与核心功能

**Cal.diy** 是由 Cal.com 官方分拆出来的社区驱动、100% 开源的日程调度平台。在 Cal.com 宣布闭源后，Cal.diy 成为该项目唯一真正的开源分支。

**核心定位：** 为所有人提供完全自主托管的调度基础设施，无需许可证密钥，无企业版功能锁定，所有代码均以 MIT 许可证发布。

### 核心功能
- **事件调度** — 创建多种事件类型（一对一、团体、循环预约），灵活设置可用时间段
- **日历集成** — Google Calendar、Microsoft Outlook/365、Apple Calendar
- **视频会议** — Zoom、Daily.co、Webex
- **CRM 集成** — HubSpot、ZohoCRM、Pipedrive、Basecamp
- **App Store 框架** — 可扩展的应用商店体系
- **多语言支持** — 内置 i18n 国际化
- **API 支持** — REST API (v2) + tRPC 接口

---

## 🏗️ 技术架构

| 层级 | 技术 |
|------|------|
| 前端框架 | Next.js + React.js |
| API 层 | tRPC (端到端类型安全) |
| 样式 | Tailwind CSS |
| 数据库 | PostgreSQL (>= 13.x) |
| ORM | Prisma.io |
| 认证 | NextAuth.js |
| 构建工具 | Turborepo (Monorepo) |
| 视频 | Daily.co |
| 校验 | Zod |

### 架构特点
- **T3 Stack 变体** — Next.js + tRPC + Prisma + Tailwind，端到端类型安全
- **Turborepo Monorepo** — 多包管理，apps/ + packages/ 分层
- **App Store 框架** — 模块化集成体系，第三方服务独立 App，可热插拔
- **Docker 一键部署** — 官方维护 Docker 镜像 (calcom/cal.diy)，支持 ARM

---

## 🎯 应用场景

- **个人日程管理** — 自由职业者分享预约链接
- **咨询服务** — 律师、顾问、教练在线预约
- **远程面试** — HR 自动同步日历和视频会议
- **医疗预约** — 诊所/心理咨询自助预约
- **SaaS 产品集成** — 作为调度引擎嵌入其他产品

> ⚠️ 官方推荐用于个人、非生产环境。商业场景建议使用 Cal.com。

---

## 🔥 为什么火 (Trending 原因)

### 核心导火索：Cal.com 闭源事件

1. **Cal.com 宣布闭源** — 2025年，Cal.com 联合创始人发表"Open source is dead"言论，核心代码转为闭源
2. **社区反弹** — Reddit 上数百条讨论，用户纷纷寻找替代方案
3. **Cal.diy 应运而生** — 作为唯一官方开源分支，承接所有开源需求
4. **"Do It Yourself" 理念** — 精准击中自托管社区的痛点
5. **MIT 许可证** — 最宽松的开源许可，降低使用和二次开发门槛

---

## ⚔️ 同类项目对比

| 项目 | 开源 | 自托管 | 技术栈 | 许可证 | 特色 |
|------|------|--------|--------|--------|------|
| **Cal.diy** | 100% | 支持 | Next.js + tRPC | MIT | 功能最全面的开源方案 |
| Cal.com | 闭源 | 支持 | Next.js + tRPC | 商业 | 企业功能、商业支持 |
| Calendly | 闭源 | 不支持 | SaaS | 商业 | 最流行，不可自托管 |
| Easy!Appointments | 开源 | 支持 | PHP + jQuery | GPL-3.0 | 轻量，技术栈较旧 |
| Rallly | 开源 | 支持 | Next.js | AGPL-3.0 | 侧重群体投票/协调 |

---

## 👥 适合谁使用

- **自托管爱好者** — 在自有服务器运行调度系统
- **隐私敏感用户** — 不希望数据存于第三方 SaaS
- **自由职业者/小团队** — 免费替代 Calendly
- **开发者/创业者** — 在调度系统上构建自己的产品
- **开源贡献者** — 参与有实际用户基础的项目

> ⚠️ 需要 Docker/Node.js 部署、PostgreSQL 管理、SSL 配置等能力。

---

## 🚀 快速上手

### Docker Compose（推荐）

```bash
# 克隆仓库
git clone --recursive https://github.com/calcom/cal.diy.git
cd cal.diy

# 配置环境
cp .env.example .env
echo "NEXTAUTH_SECRET=$(openssl rand -base64 32)" >> .env
echo "CALENDSO_ENCRYPTION_KEY=$(openssl rand -base64 24)" >> .env

# 一键启动
docker compose up -d

# 访问 http://localhost:3000
```

### 本地开发

```bash
git clone https://github.com/calcom/cal.diy.git
cd cal.diy
yarn                           # 安装依赖
cp .env.example .env           # 配置环境变量
yarn dx                        # 一键启动（含 Docker + 本地 DB）
```

### 默认测试账号

| 邮箱 | 密码 | 角色 |
|------|------|------|
| pro@example.com | pro | Pro 用户 |
| admin@example.com | ADMINadmin2022! | 管理员 |

---

## 📊 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 7/10 | Cal.com 的开源分支，非全新发明，但策略和定位出色 |
| 代码质量 | 8.5/10 | 16k+ 提交，TypeScript 95.8%，成熟 Monorepo 架构 |
| 实用性 | 9/10 | 日程调度刚需，从个人到小团队的完整解决方案 |
| 文档完善度 | 8/10 | 详尽的 README，多种部署和集成指南 |
| 社区活跃度 | 9/10 | 43k Stars，13.4k Forks，活跃 Discussions |

### 总评：8.3 / 10

---

*Generated on 2026-05-18 | [GitHub Repository](https://github.com/calcom/cal.diy)*
