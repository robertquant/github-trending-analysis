# penpot/penpot 深度分析摘要

> 📅 分析日期：2026-06-18 ｜ 🏷️ 开源设计协作平台 ｜ 🔓 MPL-2.0 ｜ 🏠 可自托管 ｜ 🔥 今日 GitHub Trending

## 一句话定位
**"The open-source design platform for design and code collaboration"** —— 让设计与代码真正同源、数据完全自主的开放设计平台，被誉为设计界的开源 Figma 对标者。

## 项目概述
- **penpot/penpot**：~36,000+ ⭐ Stars，~2,300 🍴 Forks，MPL-2.0 协议
- 由西班牙公司 **Kaleidos** 主导维护，2015 年底立项，2021 年发布 1.0，已获 **DPG（数字公共产品）** 认证
- 面向团队规模化的设计与原型协作平台，核心卖点是**把设计资产完整所有权交还团队**：可用 SaaS，也支持**完全自托管**

## 技术架构
| 层级 | 技术选型 |
|------|---------|
| 前端 | **ClojureScript** + React（编译为静态 SPA） |
| 后端 | **Clojure**（与前端共享数据结构与协作 changeset 模型） |
| 数据库 | **PostgreSQL** |
| 渲染引擎 | **Rust 编译为 WASM**（约 22,000 行 Rust 代码） |
| 开放标准 | SVG · CSS · HTML · JSON |
| 部署 | Docker / Kubernetes / Elestio（部署无关） |

亮点：前后端统一 Lisp 方言实现**同构共享代码**；Rust/WASM 引擎把 ClojureScript 数据**解构为二进制结构体写入 WASM 线性内存**高速渲染，是性能关键优化。

## 核心创新点
1. **设计即代码**：原生 SVG 渲染 + CSS Grid/Flex 布局，设计稿与生产代码天然同构，Inspect 直出可用 SVG/CSS/HTML
2. **真正自托管 + 数据主权**：部署无关，设计资产永不离开自有基础设施，满足金融/医疗/政企/信创合规
3. **原生 Design Tokens**：设计与开发之间的"单一真相源"，构建可扩展设计系统
4. **MCP Server**：设计 ↔ 代码 ↔ AI 多向工作流，让设计可被 AI Agent 读取与消费
5. **开放可编程**：REST API（access tokens）+ Webhooks + 插件系统，工作区全链路可编程
6. **开放标准 + MPL 2.0**：文件永不锁定、商用友好、无厂商锁定

## 应用场景
数据合规团队（自托管） · 设计系统团队（Tokens） · 设计-开发一体化 · 信创/自主可控 · 教育与开源 · AI 设计工作流 · CI/CD 集成 · 成本敏感团队

## 竞品对比
- **Figma**：闭源云端霸主，速度/生态领先，但数据不可控 —— Penpot 以自托管 + 开放标准差异化
- **Sketch**：闭源、仅 Mac，协作与 Web 化弱
- **Adobe XD**：已进入维护模式，生态萎缩
- **Lunacy**：免费但闭源、仅桌面端
- **Akira / Open Pencil**：同为开源，但成熟度/协作/生态远不及 Penpot

## 综合评分：8.6 / 10
| 维度 | 分数 |
|------|------|
| 功能完整度 | 8.6 |
| 架构设计 | 9.3 |
| 开放性 / 数据主权 | 9.6 |
| 实用价值 | 8.4 |
| 文档与生态 | 8.0 |
| 性能体验 | 7.4 |

**总评**：开源设计协作赛道的标杆项目。以"开源 MPL 2.0 + 自托管数据主权 + 开放 Web 标准原生 + Clojure/Rust-WASM 架构"为底座，"设计即代码"是最锋利的差异化武器。短板在性能体验（超大文件仍逊于 Figma）与生态厚度，迁移存在损耗。

> 对追求数据主权、设计-开发一体化、信创自主可控，或希望把设计资产纳入 AI/CI 可编程工作流的团队，Penpot 是当前最完整、最成熟的开源选择——不是"便宜的 Figma 复制品"，而是一条以开放标准与数据所有权为核心理念的独立路线。

---
📎 数据来源：[GitHub](https://github.com/penpot/penpot) · [Penpot 官网](https://penpot.app/) · [架构文档](https://help.penpot.app/technical-guide/developer/architecture/) · [Why Clojure](https://opensource.com/article/22/7/why-we-chose-clojure-penpot)
