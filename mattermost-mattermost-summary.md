# 💬 mattermost/mattermost — 深度分析摘要

> **分析日期**：2026-06-13 | **Stars**：37,604（今日 +391）| **主语言**：TypeScript（服务端 Go）| **License**：Apache 2.0 + 商业版

## 项目简介
开源的**安全协作平台**，定位为 Slack / Microsoft Teams 的自托管替代方案，核心使命是让团队在**软件开发生命周期（SDLC）**中实现安全协作。采用 **Open-Core** 商业模式，核心功能以 Apache 2.0 开源，企业高级功能（合规、高级 SSO、高可用）以商业许可提供。

## 四大产品支柱
- **Channels**：类 Slack 的实时消息协作（频道、私信、群组、线程、文件共享）
- **Playbooks**：运维流程与事件响应预案自动化（On-call、发布检查清单）
- **Boards**：项目管理看板 / 表格 / 日历（源自 Focalboard）
- **Calls**：内置语音视频会议与屏幕共享

## 核心亮点
- 🔒 **自托管优先，数据主权可控**：数据完全留在企业自有基础设施，满足政府/国防/金融/医疗合规
- 🏗️ **Monorepo 架构**：Go 服务端 + React/TS 前端 + React Native 移动端 + Electron 桌面端
- 🧩 **双轨插件系统**：Go 服务端插件 + JS Web 插件，深度集成 GitLab/GitHub/Jira/ServiceNow/PagerDuty
- 🚀 **覆盖完整 SDLC**：从消息协作延伸到工程编排与运维响应，形成"作战中心"
- 🛡️ **企业级安全合规**：SAML/OIDC/LDAP SSO、合规导出、审计日志、eDiscovery、数据保留策略
- 🤖 **自托管 AI**：AI Copilot / AI Bot 可对接开源大模型，数据不出域

## 技术栈
| 层级 | 选型 |
|------|------|
| 后端 | Go（模块化单体，REST + WebSocket）|
| 前端 | React + TypeScript |
| 移动端 | React Native（iOS/Android）|
| 数据库 | PostgreSQL（MySQL 可选）|
| 搜索 | Elasticsearch / Bleve（可选）|
| 缓存/HA | Redis（可选）|
| 部署 | Docker / Kubernetes(Helm) / Omnibus / 裸机 |

## 竞品对比
| 维度 | Mattermost | Slack | MS Teams | Rocket.Chat | Element/Matrix |
|------|-----------|-------|----------|-------------|----------------|
| 开源自托管 | 🟢 是 | 🔴 闭源 | 🔴 闭源 | 🟢 是 | 🟢 是 |
| 数据主权 | 🟢 完全可控 | 🔴 云端 | 🔴 云端 | 🟢 可控 | 🟢 可控 |
| SDLC/DevOps 集成 | 🟢 原生深度 | 🟡 App 生态 | 🟡 办公协同 | 🟡 通用 | 🔴 弱 |
| 事件响应 Playbooks | 🟢 内置 | 🟡 第三方 | 🔴 无 | 🟡 弱 | 🔴 无 |
| 大团队成本 | 🟢 低边际 | 🔴 按人头 | 🟡 随 M365 | 🟢 低 | 🟢 低 |

## ⭐ 综合评分：8.3 / 10
- 创新性：7.0 | 代码质量：8.5 | 实用价值：9.0
- 文档完善度：9.0 | 社区活跃度：8.0 | 生态成熟度：8.5

## 结论
开源协作领域**最成熟、最企业化**的方案之一。不以炫酷新技术取胜，而以**数据主权、安全合规、DevOps 深度集成**构建护城河。是任何重视数据控制权的中大型研发组织替代 Slack/Teams 的高价值选项；追求技术新奇或仅需轻量聊天的个人用户则有更轻量的替代品。

📄 详细报告：[mattermost-mattermost-analysis.html](./mattermost-mattermost-analysis.html)
