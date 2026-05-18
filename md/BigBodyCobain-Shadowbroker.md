# ShadowBroker — GitHub Trending 深度分析报告

> **Open-source intelligence for the global theater — 全球实时地缘空间情报平台**

| 指标 | 数值 |
|------|------|
| Stars | 6,794 |
| Today Stars | +165 |
| Forks | 1.1k |
| Language | Python 61% / TypeScript 34.6% / Rust 2.4% |
| License | AGPL-3.0 |
| Latest Release | v0.9.79 (2026-05-12) |

**标签：** `OSINT` `geospatial` `real-time` `maplibre` `fastapi` `next.js` `decentralized` `AI-agent` `self-hosted`

---

## 项目简介与核心功能

**ShadowBroker** 是一个开源的去中心化实时情报聚合平台，将来自 **60+ 个公开情报数据源**的全球实时遥测数据汇聚到统一的暗黑风格地图界面中。从私人飞机、间谍卫星到地震事件、CCTV 网络，所有数据实时更新在一个屏幕上。

**核心定位：** 将散落在数十个工具和 API 中的全球公开遥测数据（ADS-B 航空广播、AIS 海事信号、卫星轨道数据、地震传感器等）聚合到一个可自托管的统一界面中。

### 核心功能亮点

- **航空追踪** — 商用/私人/军用飞机实时位置，包括空军一号和亿万富翁私人飞机；支持盘旋检测、地面检测
- **海事追踪** — 25,000+ AIS 船只实时位置，包含航母打击群追踪（GDELT 新闻抓取估算定位）
- **卫星追踪** — 2,000+ 颗活跃卫星实时轨道位置，按军事侦察、SAR、SIGINT 等任务类型彩色编码
- **SAR 地面变化检测** — 穿透云层、全天候检测毫米级地面变形、洪水范围、植被干扰和破坏评估
- **37 个可切换数据图层** — 涵盖地震、火灾、火山、天气预警、空气质量、军事基地、数据中心等
- **11,000+ CCTV 摄像头** — 伦敦、纽约、加州、西班牙、新加坡等 6 国实时摄像头流
- **5 种视觉模式** — DEFAULT / SATELLITE / FLIR（热成像）/ NVG（夜视）/ CRT（复古终端）
- **右键情报报告** — 点击地球上任意位置获取国家简报、元首信息、最新 Sentinel-2 卫星照片
- **AI 代理命令通道** — HMAC 签名的双向代理桥，让 AI 代理完全操控地图
- **InfoNet 去中心化通信** — 首个内置于 OSINT 工具中的去中心化情报通信和治理层
- **时间机器** — 快照回放功能，可暂停、回放、快进整个遥测数据流

---

## 技术架构与特点

### 技术栈

| 层级 | 技术 |
|------|------|
| 前端框架 | Next.js + React |
| 地图引擎 | MapLibre GL (WebGL 渲染) |
| 后端框架 | FastAPI (Python) |
| 调度系统 | APScheduler (fast/slow 双层调度) |
| 密码学核心 | Rust crate (privacy-core) |
| 容器化 | Docker / Podman / Helm (K8s) |
| 数据缓存 | ETag + Gzip (92% 压缩率) |

### 三层架构

1. **Operator UI（操作员界面层）** — Next.js + MapLibre GL WebGL 渲染
2. **Backend Service Plane（后端服务层）** — FastAPI 驱动，60+ API 数据源
3. **Decentralized Layer（去中心化层）** — InfoNet 实验性测试网

### 架构亮点

- **视口裁剪** — 仅渲染可见地图范围 (+20% 缓冲) 内的数据点
- **命令式地图更新** — 高频数据层绕过 React 调和，直接调用 setData()
- **集群渲染** — MapLibre 聚类降低低缩放级别下的渲染负载
- **位置插值** — 10 秒 tick 动画平滑连接数据刷新
- **多架构支持** — linux/amd64 + linux/arm64（树莓派 5）
- **HMAC-SHA256 代理通道** — 批量并发执行，最多 20 个命令

---

## 应用场景

- **地缘政治分析** — 实时追踪全球冲突事件、乌克兰前线动态、空袭警报
- **航空/海事监控** — 追踪空军一号、航母打击群、亿万富翁私人飞机/游艇
- **灾害响应** — 地震、火山、野火、GPS 干扰区的实时可视化
- **网络安全研究** — Shodan 集成搜索联网设备，互联网中断监控
- **软件定义无线电** — 500+ KiwiSDR 接收器，警察/消防扫描器
- **AI 辅助情报分析** — AI 代理自动解析多层数据发现隐藏关联
- **环境监测** — 空气质量、天气预警、夜光变化检测
- **教育与科普** — 直观展示全球公开数据的力量

> ⚠️ 该项目仅聚合公开可用的 OSINT 数据，不引入新的监控能力。所有数据均来自公开 API 和广播信号。

---

## 为什么火 (Trending 原因)

### 核心驱动力：将"不可能"的情报聚合能力平民化

1. **"上帝之眼"概念引爆** — Reddit r/osinttools 上获 446+ 点赞，将好莱坞电影中的全球监控界面变成现实
2. **零门槛部署** — Docker 三行命令启动，预构建镜像无需编译，完全本地运行
3. **数据源广度前所未有** — 60+ 数据源、37 个可切换图层，在开源世界中几乎没有先例
4. **AI 代理集成** — 双向代理命令通道，从"人看的仪表板"变成"AI 可操作的情报平台"
5. **极客美学** — FLIR 热成像、NVG 夜视、CRT 复古终端等视觉模式极具传播性
6. **地缘政治热点催化** — 乌克兰前线、GPS 干扰区检测等功能具有极强现实意义
7. **去中心化叙事** — InfoNet + Sovereign Shell 治理经济，符合 Web3 技术趋势
8. **多平台媒体报道** — Hackers Arise、Hacker News、Gigazine、daily.dev 等均有报道

---

## 同类项目对比

| 项目 | 开源 | 自托管 | 数据源 | 实时地图 | AI 集成 | 许可证 |
|------|------|--------|--------|----------|---------|--------|
| **ShadowBroker** | ✅ 100% | ✅ | 60+ | ✅ MapLibre | ✅ 双向通道 | AGPL-3.0 |
| Maltego | ❌ 商业 | ❌ | Transform Hub | ❌ 关系图 | ⚠️ 有限 | 商业许可 |
| Shodan | ❌ 闭源 | ❌ | 联网设备 | ✅ 有 | ⚠️ API | 商业 |
| SpiderFoot | ✅ 开源 | ✅ | 200+ 模块 | ❌ 无地图 | ❌ 无 | MIT |
| ADS-B Exchange | ⚠️ 部分 | ❌ | 航空数据 | ✅ 有 | ❌ 无 | 商业 |

ShadowBroker 的独特价值在于将分散在 Maltego、Shodan、ADS-B Exchange 等数十个专业工具中的能力聚合到一个免费、开源、自托管的实时地图界面中。其 AI 代理集成和去中心化通信层更是同类项目中独有的。

---

## 适合谁使用

- **OSINT 分析师/研究人员** — 一站式情报聚合平台
- **安全研究员/渗透测试人员** — Shodan 集成、GPS 干扰检测
- **航空/海事爱好者** — 实时追踪全球飞机和船只
- **新闻记者/调查记者** — 地缘政治事件实时监控
- **业余无线电操作员** — KiwiSDR、Meshtastic、APRS 集成
- **AI/LLM 开发者** — AI 代理与实时情报平台集成
- **应急响应/灾害管理人员** — 地震、火灾、洪水实时可视化
- **极客/技术爱好者** — 被"上帝之眼"界面的酷炫程度吸引

> ⚠️ InfoNet 去中心化通信目前为实验性测试网，不提供隐私保证。所有通道应视为公开。

---

## 快速上手指南

### 方式一：Docker 一键启动（推荐）

```bash
git clone https://github.com/BigBodyCobain/Shadowbroker.git
cd Shadowbroker
docker compose pull
docker compose up -d
# 打开 http://localhost:3000
```

### 方式二：零代码安装

1. 从 GitHub Releases 下载最新 .zip
2. 解压到本地
3. Windows: 双击 `start.bat` / Mac/Linux: `chmod +x start.sh && ./start.sh`

### 方式三：Kubernetes / Helm

```bash
helm repo add bjw-s-labs https://bjw-s-labs.github.io/helm-charts/
helm install shadowbroker ./helm/chart --create-namespace --namespace shadowbroker
```

### 可选 API 密钥

| 密钥 | 用途 | 必需？ |
|------|------|--------|
| AIS_API_KEY | 海事船只追踪 | 推荐 |
| OPENSKY_CLIENT_ID/SECRET | 全球航班覆盖 | 推荐 |
| SHODAN_API_KEY | 联网设备搜索 | 可选 |
| SH_CLIENT_ID/SECRET | Sentinel Hub 卫星图像 | 可选 |
| NASA Earthdata | SAR 地面变化检测 | 可选 |

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | **9.5/10** | 在开源世界中几乎没有同类产品。60+ 情报源统一地图、AI 代理通道、去中心化通信层、SAR 地面变化检测均为开创性 |
| **代码质量** | **8/10** | 三层架构设计清晰，性能优化到位（92% Gzip 压缩、ETag 缓存、视口裁剪）。InfoNet 隐私原语尚未完全接线 |
| **实用性** | **9/10** | Docker 三行命令运行，覆盖多个领域的实际应用场景 |
| **文档完善度** | **9/10** | README 极其详尽，包含架构图、数据源表格、部署指南、性能策略、项目结构 |
| **社区活跃度** | **8/10** | 7k Stars、1.1k Forks、多国贡献者、Reddit/HN 热议。仍主要由单人驱动 |

### 综合评分：8.7 / 10

---

*Generated on 2026-05-18 | GitHub Trending Deep Analysis*

*Repository: [github.com/BigBodyCobain/Shadowbroker](https://github.com/BigBodyCobain/Shadowbroker)*