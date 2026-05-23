# byJoey/cfnew 深度分析

> 基于 Cloudflare Workers 的多功能代理部署工具
> 分析日期: 2026-05-23 | Stars: ~13.3k | Forks: ~6.5k | 版本: v2.9.6

---

## 项目简介

**CFnew** 是一个基于 Cloudflare Workers/Pages 平台的多功能代理部署工具，由开发者 byJoey 创建。该项目从经典的 `zizifn/edgetunnel` 改进而来，在继承原有能力的基础上，大幅扩展了协议支持、管理功能和用户体验。

核心理念：**零成本部署、图形化管理、多协议共存**。

### 核心功能

| 功能 | 说明 |
|------|------|
| 多协议支持 | VLESS、Trojan、XHTTP 可同时启用 |
| 图形化管理面板 | 基于 KV 存储的可视化配置，修改后立即生效 |
| 内置延迟测试 | 集成 IP 延迟测试，自动获取机场码，支持地区筛选 |
| 自定义路径 | 告别 UUID 路径，支持自定义多级路径 |
| 多客户端兼容 | CLASH、SURGE、SING-BOX、Shadowrocket 等 10+ 客户端 |
| API 动态管理 | RESTful API 管理优选 IP，支持批量操作 |
| ECH 加密握手 | 支持 Encrypted Client Hello，增强隐私保护 |
| 多语言支持 | 中文 + 波斯语，根据浏览器自动切换 |

---

## 技术架构

### 架构组件

| 组件 | 技术 | 作用 |
|------|------|------|
| Worker 主程序 | JavaScript / Workers Runtime | 协议解析和流量转发 |
| KV 存储 | Cloudflare KV Namespace | 持久化配置数据 |
| 配置面板 | HTML/CSS/JS（内嵌） | Web 端可视化管理 |
| 优选引擎 | Workers Cron Trigger | 每 15 分钟自动优选 IP |
| API 层 | RESTful API | 外部程序动态管理 |
| 订阅生成 | 动态模板引擎 | 根据客户端自动生成配置 |

### 技术亮点

- **零服务器成本** — 完全运行在 Cloudflare 免费套餐
- **KV 配置热更新** — 5 小时内存缓存，减少 99%+ KV 读取量
- **无效请求拦截** — 非法路径直接 404，不触发 KV 读取
- **Path 参数覆盖** — 在分享链接 path 中直接写参数，无需额外部署
- **智能地区匹配** — 自动检测 Worker 地区，优选同地区 ProxyIP
- **兼容 Xray-core v26.3.27**

---

## 应用场景

| 场景 | 描述 |
|------|------|
| 个人网络加速 | 利用 Cloudflare 全球 CDN 节点加速网络访问 |
| 访问 AI 服务 | 访问 ChatGPT、Claude 等 AI 服务 |
| 开发者工具 | 访问 GitHub、Google、Stack Overflow 等资源 |
| 学习 Workers | 作为学习边缘计算和 Workers 开发的实战项目 |
| 协议研究 | 了解 VLESS、Trojan、XHTTP 等现代代理协议 |

> ⚠️ **重要提醒：** Cloudflare 已更新服务条款限制代理相关服务，部署前请阅读最新 ToS。

---

## 为什么火（Trending 原因）

1. **零成本解决方案** — Cloudflare 免费套餐即可部署，无需购买 VPS
2. **持续快速迭代** — v2.7 到 v2.9.6 短期内多次实质性更新
3. **极致用户体验** — 图形化管理面板是同类项目中的显著差异化优势
4. **中文社区驱动** — 完善中文文档、Telegram 群、YouTube 教程形成活跃生态
5. **多协议共存** — VLESS + Trojan + XHTTP 同时启用
6. **ECH 前沿技术** — 较早支持 Encrypted Client Hello
7. **API 生态完整** — RESTful API + 优选工具形成完整工具链

---

## 同类项目对比

| 特性 | byJoey/cfnew | cmliu/edgetunnel | zizifn/edgetunnel | eooce/Cloudflare-proxy |
|------|-------------|-----------------|-------------------|----------------------|
| Stars | ~13.3k | ~8k+ | ~6k+ | ~3k+ |
| 图形化管理 | ✅ 完整面板 | ✅ WebUI | ❌ | ❌ |
| 协议支持 | VLESS+Trojan+XHTTP | VLESS+Trojan+SS | VLESS | VLESS+Trojan |
| 延迟测试 | ✅ 内置 | ❌ | ❌ | ❌ |
| API 管理 | ✅ RESTful | ❌ | ❌ | ❌ |
| ECH 支持 | ✅ | ❌ | ❌ | ❌ |
| 多语言 | 中文+波斯语 | 中文 | 英文 | 英文 |
| 更新频率 | 非常活跃 | 活跃 | 低 | 一般 |

---

## 适合谁使用

- **技术学习者** — 对边缘计算、Workers、网络协议感兴趣
- **开发者** — 需要访问 GitHub、Google 等开发资源
- **AI 研究者** — 需要访问 ChatGPT、Claude 等 AI 服务
- **网络安全研究者** — 研究现代代理协议、ECH、TLS 等技术

前提：Cloudflare 免费账号 + 基本网络知识 + 兼容客户端

---

## 快速上手

### 部署步骤

1. 注册 Cloudflare 免费账号
2. 进入 Workers 和 Pages → 创建 Worker → 上传 worker.js
3. 设置环境变量 `u`（你的 UUID）
4. 兼容日期设置为 `2026-01-20`
5. 创建 KV 命名空间并绑定变量 `C`（推荐）
6. 访问 `https://你的worker.workers.dev/{UUID}` 进行图形化配置

### 基础环境变量

```bash
# 必需
u = 你的UUID

# 可选
d = /mypath          # 自定义路径
p = 1.1.1.1:443      # ProxyIP
wk = SG              # 地区代码
ev = yes             # 启用 VLESS（默认）
et = yes             # 启用 Trojan
ex = yes             # 启用 XHTTP
ech = yes            # 启用 ECH
```

### 客户端订阅

```
https://你的worker.workers.dev/{UUID或自定义路径}
```

客户端根据 User-Agent 自动返回对应格式配置。

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | **8.0/10** | 图形化面板、内置延迟测试、API 管理属首创；ECH 前沿支持 |
| 代码质量 | **7.0/10** | 功能完整但单文件 Worker 脚本，模块化有限；KV 缓存优化不错 |
| 实用性 | **8.5/10** | 零成本、多协议、10+ 客户端兼容，使用体验优秀 |
| 文档完善度 | **8.5/10** | 详尽中文 README、YouTube 教程、Telegram 群、博客教程 |
| 社区活跃度 | **9.0/10** | 13.3k Stars、频繁更新、活跃社区、多个配套工具 |

### 综合评分: 8.2 / 10

---

## 相关资源

- GitHub 仓库: https://github.com/byJoey/cfnew
- 优选工具: https://github.com/byJoey/yx-tools/releases
- 更新仓库: https://github.com/byJoey/cfnewup
- 文字教程: https://joeyblog.net/yuanchuang/1146.html
- Workers 视频教程: https://www.youtube.com/watch?v=aYzTr8FafN4
- Pages 视频教程: https://www.youtube.com/watch?v=JhVxJChDL-E

---

*🤖 AI 深度分析报告 | 由 Claude Code 自动生成 | 2026-05-23*
