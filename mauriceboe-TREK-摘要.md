# mauriceboe/TREK 深度分析摘要

> **数据归你自己的 Wanderlog** —— 一行 Docker 拉起的自托管、实时协作、AI 原生旅行规划器

## 📌 基本信息
| 项目 | 详情 |
|------|------|
| **仓库** | [mauriceboe/TREK](https://github.com/mauriceboe/TREK) |
| **定位** | 自托管旅行 / 行程规划应用 |
| **热度** | 🔥 GitHub Trending / Trendshift 上榜，r/selfhosted 热议 |
| **技术栈** | React 18 + Vite + TypeScript + Tailwind / Node.js 22 + Express / SQLite |
| **实时同步** | WebSocket（ws）+ Zustand 状态 |
| **鉴权** | JWT + OAuth 2.1 + OIDC + TOTP 2FA |
| **地图** | Leaflet + Mapbox GL（3D 建筑 / 地形） |
| **部署** | Docker / Compose / Helm(K8s) / Railway / Zeabur / Hostinger |
| **License** | AGPL v3 |
| **语言** | 15 种（含中文、繁中、阿拉伯语 RTL） |

## 🧠 项目概述
TREK 是开发者 mauriceboe 打造的**自托管旅行规划器**，目标是做一个"数据完全归你自己的 Wanderlog / TripIt"——把行程规划、旅行管理、多人协作、预算与打包、游记足迹全部放在自己服务器上，PWA 离线可用，还能像原生 App 装到手机。在 v3.0.0 引入 Journey 游记插件与 Mapbox GL 一等渲染引擎后迎来跨越式更新，是 self-hosted 领域少有的"完成度接近商业产品"的旅行类应用。

## ⚙️ 技术架构
- **单镜像 + 单文件数据库**：前端 React SPA 与 Node 服务打包进同一 Docker，数据落 SQLite，**无需 Postgres / Redis / MQ**，部署与迁移成本极低。
- **前端**：React 18 + Vite + TypeScript + Tailwind + Zustand；PWA 经 Workbox 缓存瓦片/API/上传，离线可用。
- **后端**：Node 22 + Express，REST + WebSocket（`/ws`）实时广播，多人编辑秒级同步。
- **地图双引擎**：Leaflet 与 Mapbox GL 可切换，支持 3D 建筑、地形、照片标记、聚合、路线可视化。
- **安全默认**：只读容器、`cap_drop: ALL`、tmpfs `noexec`、`ENCRYPTION_KEY` 静态加密敏感凭据 + 密钥轮换脚本。
- **AI 原生**：内置 **OAuth 2.1 保护的 MCP Server**，150+ 工具、30 资源、27 个 scope。

## 💡 核心创新点
- **模块化插件体系**：Lists / Budget / Documents / Collab / Vacay / Atlas / Journey / Naver Import / MCP 九大插件，管理员按需开关，避免"全家桶"臃肿。
- **AI 原生 MCP**：把整套旅行数据通过受 OAuth 保护的标准化协议交给 AI 助手，让行程成为任意 MCP 客户端的一等数据源——Agent 时代前瞻性强。
- **3D 地图可视化**：Mapbox GL 渲染让"行程可视化"达到商业级，而非平面散点。
- **实时多人协作**：WebSocket 即时同步 + 角色权限 + 邀请链接（可设过期）+ 群聊/笔记/投票/签到。
- **旅行管理闭环**：预订、多币种预算分摊、打包清单（含行李称重）、文档管理、整行程 PDF 导出，打通"规划→执行→归档"。
- **企业级身份**：OIDC SSO（Google/Apple/Authentik/Keycloak）+ 2FA + SSO-only 模式 + 内网 SSRF 防护。

## 🎯 应用场景
家庭/朋友结伴出行（实时协作+预算分摊）、深度自由行/自驾（路线优化导出 Google Maps、16 天天气）、数字游民长期旅居（Vacay 假期日历、多币种预算）、数据隐私敏感用户（行程/护照/票据不出自有服务器）、小企业团建/旅行社（OIDC SSO+角色权限+PDF 交付）、AI Agent 爱好者（MCP 数据源）、旅行记录/回忆（Journey 游记+Atlas 足迹）。

## ⚔️ 竞品对比
相较 **Wanderlog / TripIt**（SaaS），TREK 赢在**数据主权 + 全功能免费 + AI MCP**；相较 **AdventureLog**（自托管），TREK 胜在**规划能力更完整 + 实时协作 + 企业级身份**。其真正对手是"自托管 + 商业级体验"这条线上的综合完成度，目前 TREK 处于领先。

## ⚖️ 优势与局限
**优势**：完成度极高（一条龙可用）、部署极简（1 行 Docker 无外部依赖）、AI 前瞻（内置 MCP）、安全默认到位、本地化优秀（15 语言 + PWA 近原生）。
**局限**：个人维护可持续性存疑、SQLite 不适合超大并发、Mapbox/Google Places 需自备 Key、AGPL v3 限制闭源 SaaS 化、第三方生态尚浅。

## 🏆 综合评分：**8.6 / 10**
| 维度 | 评分 |
|------|------|
| 功能完整度 | 9.0 |
| 技术架构 | 8.5 |
| 实用价值 | 9.0 |
| 部署与文档 | 8.5 |
| 社区热度 | 8.0 |

**结论**：2026 年自托管生态中完成度最高、最现代的旅行规划应用，用商业级产品力 + 极简部署 + 内置 MCP 三招拉开身位。对自托管玩家、隐私敏感旅行者、家庭/小团队结伴、AI Agent 爱好者几乎是最优解。**强烈推荐上手体验。**
