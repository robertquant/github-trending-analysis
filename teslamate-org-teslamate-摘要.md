# TeslaMate 深度分析摘要

> **仓库**：[teslamate-org/teslamate](https://github.com/teslamate-org/teslamate)
> **类型**：自托管特斯拉数据记录与分析平台
> **主语言**：Elixir（Phoenix / Erlang OTP）　**数据库**：PostgreSQL　**可视化**：Grafana　**协议**：MIT
> **生成日期**：2026-06-16

## 一、项目概述
TeslaMate 是一款**开源、完全自托管（self-hosted）的特斯拉数据记录器**，由 Adrian Kumpf（@adriankumpf）于 2019 年创建，灵感源自更早的 TeslaLogger，但以"现代软件工程"重写：**Elixir 语言 + PostgreSQL 持久化 + Grafana 可视化 + 全容器化**。项目现已迁至 **teslamate-org** 组织由社区维护。它解决的痛点是——特斯拉官方只给你"当下状态"，却给不了**历史**：无法回看每次行程能耗、追踪多年电池衰减、精确统计充电花费、或把"到家"事件接入智能家居。TeslaMate 把这些数据持续细粒度地沉淀到你自己的数据库，把用车经验升级为**可分析的数据资产**。

## 二、关键指标（2026-06）
| 指标 | 数值 |
|---|---|
| GitHub Stars | 6,000+ |
| Forks | 750+ |
| 首版发布 | 2019（v1.0） |
| 技术栈 | Elixir · Phoenix · LiveView · OTP/BEAM |
| 数据库 | PostgreSQL |
| 可视化 | Grafana（预置十余个看板） |
| 部署 | Docker / Docker Compose（x86 + ARM 多架构） |
| 实时总线 | Mosquitto MQTT（→ Home Assistant） |
| 许可证 | MIT |

## 三、技术架构（核心差异点）
**采集层**：Elixir 的 GenServer/Supervisor 树（运行于 Erlang BEAM）调度，天然适合"一台车一进程、长期常驻、高容错"的采集任务。**双通道采集**：REST Fleet API 按"休眠友好"间隔轮询状态（车辆休眠时主动停采，保护 12V 电瓶与电池），Streaming API 在车辆活跃时建立 WebSocket 推送秒级高频遥测（车速/功率/海拔/胎压）。**数据流**：`特斯拉车辆 → Tesla Cloud（REST + Streaming）→ TeslaMate（Elixir/Phoenix 核心）→ PostgreSQL → Grafana / MQTT / TeslaMateApi(Go)`。地理围栏引擎把 GPS 流自动归因为可读地址与"到家/到公司"事件。

## 四、核心创新点
1. **数据主权（Data Ownership）** —— 每字节数据写入你自己的 Postgres，无第三方留存、可导出、可离线分析，隐私与长期价值根本领先于 SaaS。
2. **Elixir/OTP 高容错采集** —— 选 BEAM 而非 Python/Node，"let it crash"哲学与 Supervisor 树兜住 7×24 常驻、车辆随机上下线、网络抖动，长期稳定。
3. **顶级的开箱 Grafana 看板** —— 社区公认同类最佳：行程能耗拆解、充电曲线、衰减趋势、年度报告、终身驾驶地图，部署即用。
4. **MQTT → 智能家居闭环** —— 实时发布车辆状态到 MQTT，触发 Home Assistant 自动化（到家开灯/离家布防/低电量提醒）。
5. **地理围栏自动归因** —— GPS 流自动识别行程起止点与常去地点，行程记录天然结构化、可报销、可统计。
6. **睡眠友好的采集策略** —— 智能判断休眠状态主动暂停轮询，避免涓流损耗与电瓶亏电，"懂特斯拉"的设计。

## 五、应用场景
个人用车分析（行程能耗/效率/路线回放）、电池健康与衰减长期追踪、充电成本核算（家充/超充）、Home Assistant 智能家居联动（到/离家、充电完成）、商务/报销里程日志生成、homelab 数据极客折腾、小型车队或多车统一记录、以及作为二次开发数据源（经 TeslaMateApi 或直连 Postgres 喂给 ABRP 续航规划等）。核心用户是**技术型特斯拉车主、homelab 玩家、智能家居爱好者**，通常已拥有 NAS/树莓派并习惯 Docker 部署。

## 六、竞品对比（TeslaMate vs TeslaLogger vs TeslaFi vs Teslascope）
| 维度 | TeslaMate | TeslaLogger | TeslaFi | Teslascope |
|---|---|---|---|---|
| 部署形态 | 自托管 (Docker) | 自托管 | 云端 SaaS | 云端 SaaS |
| 费用 | 免费开源 | 免费开源 | ~$5/月订阅 | 付费订阅 |
| 数据所有权 | 🏆 完全自有 | 完全自有 | 平台托管 | 平台托管 |
| 语言 | Elixir (BEAM) | C# (.NET) | 闭源 SaaS | 闭源 SaaS |
| 可视化 | 🏆 Grafana 顶级 | 内置（丰富） | 内置 | 内置 |
| MQTT/智能家居 | 🏆 原生支持 | 部分 | 有限 | 有限 |
| 上手难度 | 中等 | 中等 | 极简 | 极简 |
| 可二次开发 | 🏆 完全可改 | 可改 | 不可 | 不可 |

## 七、综合评分：**8.0 / 10**
- 数据所有权/隐私 9.8｜运行可靠性 9.0｜可视化 9.2｜文档 8.8｜社区 8.2｜生态 8.4｜部署/上手 6.8｜维护可持续 7.0

**结论**：是把"用车经验"转化为"数据资产"的最佳开源方案——Elixir/OTP 保证长期稳定，Postgres + Grafana 给予顶级的可视与可控，MQTT 让车辆无缝融入智能家居。若你有常开的 Docker 宿主、在意隐私与长期数据价值，它无可替代；若只求零门槛、即开即看且不介意订阅费与数据托管，TeslaFi / Teslascope 这类 SaaS 更省心。需持续关注特斯拉 API（Fleet API 转型）政策变化对长期维护的影响。

---
*完整可视化报告见同目录 `teslamate-org-teslamate-深度分析报告.html`*
