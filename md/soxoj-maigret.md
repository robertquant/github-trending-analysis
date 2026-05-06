# Maigret - OSINT 用户名情报收集工具 深度分析

> 项目地址: [github.com/soxoj/maigret](https://github.com/soxoj/maigret)
> 分析日期: 2026-05-05 | Stars: 24,345 | 今日新增: 1,119

---

## 项目简介

**Maigret** 是一款强大的开源 OSINT（开源情报）命令行工具，仅需一个用户名即可从 **3,000+ 个网站** 收集关于个人的详细档案（dossier）。它自动检查目标用户名在各大社交平台、论坛、博客等网站上的注册情况，并提取所有可获取的公开信息。

项目以法国侦探小说家乔治·西默农笔下的侦探 **儒勒·梅格雷（Jules Maigret）** 命名，寓意其侦探般的情报收集能力。

---

## 核心功能

### 1. 海量站点覆盖
- 支持 **3,000+ 个网站** 的账号检测
- 默认运行检查流量排名前 500 的站点
- 使用 `-a` 参数可扫描全部站点，或使用 `--tags` 按分类/国家筛选

### 2. 智能信息提取
- 从个人资料页面和站点 API 自动提取用户信息
- **PII（个人身份信息）提取**：姓名、位置、个人简介、头像等
- **交叉关联**：发现账号之间的链接关系，自动提取关联的其他用户名和 ID

### 3. 递归搜索
- 使用已发现的用户名和其他 ID 进行递归搜索
- 通过 `--parse URL` 解析个人资料页面，提取 ID/用户名后启动递归搜索
- 通过 `--permute` 从多个输入生成可能的用户名变体（如 `john doe` → `johndoe`, `j.doe` 等）

### 4. 反检测与绕过
- 检测并部分绕过封锁、审查和验证码
- 支持 Tor、I2P 和 HTTP/SOCKS 代理
- 适用于 `.onion` / `.i2p` 站点检测

### 5. 多格式报告输出
- **HTML 报告**：交互式图表展示
- **PDF 报告**：适合存档
- **XMind 报告**：思维导图形式
- **CSV / JSON / TXT**：机器可读格式
- **D3 图谱**：交互式网络关系图

### 6. Web 界面
- 内置 Web UI，可通过浏览器查看结果图表和下载报告
- 支持 Docker 部署

### 7. Python 库集成
- 可作为 Python 库嵌入到自己的项目中
- CLI 仅是对异步函数的薄封装，支持自定义工作流

---

## 技术架构

```
┌──────────────────────────────────────────────┐
│                  用户界面层                     │
│  ┌──────────┐ ┌──────────┐ ┌──────────────┐  │
│  │   CLI    │ │  Web UI  │ │ Telegram Bot │  │
│  └────┬─────┘ └────┬─────┘ └──────┬───────┘  │
│       │            │              │           │
├───────┼────────────┼──────────────┼───────────┤
│       │      核心引擎层           │           │
│  ┌────▼─────────────▼──────────────▼───────┐  │
│  │          Maigret Core Engine            │  │
│  │  ┌───────────┐ ┌────────────────────┐   │  │
│  │  │  站点数据库 │ │ 异步请求调度器      │   │  │
│  │  │ (data.json)│ │ (asyncio + aiohttp)│   │  │
│  │  └───────────┘ └────────────────────┘   │  │
│  │  ┌───────────┐ ┌────────────────────┐   │  │
│  │  │ 递归搜索引擎│ │ 反检测/代理模块    │   │  │
│  │  └───────────┘ └────────────────────┘   │  │
│  └────────────────────────────────────────┘  │
│                                              │
├──────────────────────────────────────────────┤
│                  输出层                       │
│  ┌──────┐ ┌──────┐ ┌──────┐ ┌──────┐       │
│  │ HTML │ │ PDF  │ │ XMind│ │ JSON │ ...   │
│  └──────┘ └──────┘ └──────┘ └──────┘       │
└──────────────────────────────────────────────┘
```

---

## 技术栈

| 类别 | 技术 |
|------|------|
| **语言** | Python 3.10+ |
| **异步框架** | asyncio, aiohttp |
| **HTML 解析** | BeautifulSoup, lxml |
| **PDF 生成** | reportlab |
| **图形可视化** | D3.js (HTML 报告), XMind SDK |
| **Web 框架** | Flask (内置 Web UI) |
| **数据存储** | JSON (站点数据库 data.json) |
| **部署** | Docker, pip, 独立 EXE |
| **代理支持** | Tor, I2P, HTTP/SOCKS5 |

---

## 应用场景

### 1. 网络安全调查
- 安全研究人员追踪威胁行为者的数字足迹
- 红队/蓝队行动中的信息收集
- 社会工程学防御

### 2. 执法与情报
- 执法机构的在线调查
- 情报分析人员的开源情报收集
- 反欺诈调查

### 3. 记者与调查报道
- 调查记者验证信息来源
- Bellingcat 等组织已将其纳入调查工具箱
- 深度报道中的背景调查

### 4. 企业安全与尽职调查
- HR 背景调查
- 企业并购中的风险评估
- 品牌保护与冒充账号检测

### 5. 个人隐私审计
- 检查自己在各平台的账号曝光情况
- 评估个人数字足迹
- 隐私加固参考

---

## 为什么火（Trending 原因）

### 1. OSINT 需求爆发
随着网络安全威胁的持续增长，OSINT 工具的需求呈现爆发式增长。Maigret 作为该领域最全面的用户名搜索工具，自然受到广泛关注。

### 2. Sherlock 的进化替代
Maigret 最初是 Sherlock 的 fork，但在功能上远超 Sherlock：
- Sherlock 仅检查约 400 个站点，Maigret 覆盖 3,000+
- Maigret 增加了信息提取、递归搜索、报告生成等高级功能
- 被社区广泛认为是 Sherlock 的"升级版"

### 3. 专业工具集成
被多个专业 OSINT 工具和平台采用：
- **Social Links API** — 专业 OSINT 分析平台
- **Social Links Crimewall** — 可视化调查平台
- **UserSearch** — 高级 OSINT 搜索平台

### 4. 持续活跃维护
- 站点数据库每日自动更新
- 活跃的社区贡献（新增/修复站点）
- 定期发布新版本（最新 v0.5.0）

### 5. 零门槛使用
- 无需 API Key
- 一行命令即可运行：`pip install maigret && maigret USERNAME`
- 提供多种使用方式（CLI / Web / Docker / Telegram Bot / Cloud Shell）

---

## 同类项目对比

| 特性 | **Maigret** | **Sherlock** | **WhatsMyName** | **Namechk** |
|------|:-----------:|:------------:|:---------------:|:-----------:|
| 覆盖站点数 | 3,000+ | ~400 | ~600 | ~100 |
| 信息提取 | 全面（PII+关联） | 仅检测存在 | 仅检测存在 | 仅检测存在 |
| 递归搜索 | ✅ | ❌ | ❌ | ❌ |
| 报告生成 | HTML/PDF/XMind/CSV | 简单文本 | Web 界面 | Web 界面 |
| 图谱可视化 | ✅ (D3.js) | ❌ | ❌ | ❌ |
| 代理/Tor 支持 | ✅ | 有限 | ❌ | ❌ |
| Web UI | ✅ | ❌ | ✅ | ✅ |
| Python 库 | ✅ | ✅ | ❌ | ❌ |
| 开源协议 | MIT | MIT | 未知 | 商业 |
| 活跃维护 | 高 | 中 | 中 | - |

**结论**：Maigret 在覆盖范围、信息深度、输出格式和功能完整性上均明显领先同类工具。

---

## 适合谁使用

### 推荐人群
- **安全研究员 / 渗透测试人员** — 信息收集阶段的利器
- **OSINT 分析师** — 专业的开源情报工作流核心工具
- **调查记者** — 快速建立目标的数字足迹画像
- **企业安全团队** — 员工/候选人背景调查
- **隐私意识强的个人** — 审计自己的在线曝光

### 不适合
- 非法入侵或跟踪他人（违反法律和道德）
- 未授权的大规模数据采集
- 不了解当地法律法规（GDPR、CCPA 等）的用户

---

## 快速上手指南

### 安装

```bash
# 最简安装（需要 Python 3.10+）
pip install maigret
```

### 基本使用

```bash
# 搜索单个用户名（默认检查 Top 500 站点）
maigret johndoe

# 生成 HTML 报告
maigret johndoe --html

# 生成 PDF 报告
maigret johndoe --pdf

# 检查所有 3000+ 站点
maigret johndoe -a

# 按标签筛选（如只检查照片和约会类站点）
maigret johndoe --tags photo,dating

# 按国家筛选
maigret johndoe --tags us
```

### 高级用法

```bash
# 同时搜索多个用户名
maigret user1 user2 user3 -a

# 通过 Tor 代理搜索
maigret johndoe --tor-proxy socks5://127.0.0.1:9050

# 解析 URL 中的用户信息并递归搜索
maigret --parse https://twitter.com/johndoe

# 生成用户名排列组合后搜索
maigret john doe --permute

# 导出为 JSON 格式
maigret johndoe --json ndjson

# 导出为交互式关系图
maigret johndoe --graph
```

### Docker 使用

```bash
# CLI 模式
docker run -v $(pwd)/reports:/app/reports soxoj/maigret:latest johndoe --html

# Web UI 模式（访问 http://localhost:5000）
docker run -p 5000:5000 soxoj/maigret:web
```

### Python 库集成

```python
import maigret

# 在自己的 Python 项目中调用
# 详见官方文档：https://maigret.readthedocs.io/
```

---

## 许可证

MIT License — 可免费用于商业用途。

---

## 参考链接

- [GitHub 仓库](https://github.com/soxoj/maigret)
- [官方文档](https://maigret.readthedocs.io/)
- [Bellingcat 工具箱](https://bellingcat.gitbook.io/toolkit/more/all-tools/maigret)
- [OSINTBench 评测](https://osintbench.com/tools/maigret)
- [OSINT 名字检查工具列表](https://github.com/soxoj/osint-namecheckers-list)

---

> **免责声明**：本工具仅供教育和合法用途。使用者有责任遵守所在司法管辖区的所有适用法律（包括 GDPR、CCPA 等）。作者不对滥用行为承担责任。
