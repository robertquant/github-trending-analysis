# zakirullin/files.md - 深度分析报告

> 🌱 **Private, quiet space for thinking. A simple app for your .md files.**

| 指标 | 数据 |
|------|------|
| GitHub | https://github.com/zakirullin/files.md |
| Stars | ~2,200+ |
| Hacker News | 708 points / 345 评论 |
| 开发时间 | 5 年 |
| 主要语言 | Go |
| 前端技术 | 原生 JS + PWA |
| 许可证 | 开源 |
| 同类项目 | Obsidian, Notion, Logseq |

---

## 项目简介

**files.md** 是一个极简主义的笔记和知识管理应用，核心理念是「用纯 Markdown 文件存储一切」。它不是又一个功能臃肿的笔记应用，而是一个安静、私密的思考空间。

> "Own your data as plain local files. Own the software that opens those files. Grow your knowledge with files and your own brain. Plain files and self-owned software can last through the ages."

### 核心功能

- **📝 笔记与文档** — 用 .md 文件组织笔记、文档、项目资料
- **💚 日记与习惯追踪** — 自动按月生成日记文件，支持习惯记录
- **✅ 任务与清单** — 轻量级待办事项、购物清单、阅读清单
- **🤖 Telegram Bot** — 通过聊天快速记录想法、任务、日记
- **🔗 知识链接** — 在笔记间建立连接，形成知识网络
- **📊 LaTeX 支持** — 文本+数学公式覆盖几乎所有记录需求

---

## 技术架构

| 层 | 技术 | 说明 |
|---|---|---|
| 前端 | 原生 JS + PWA | 无构建系统，打开 index.html 即运行 |
| 后端 | Go 单二进制 | 同步服务器为单个 Go 二进制文件 |
| 存储 | OPFS / 本地文件系统 | 默认使用 OPFS，可切换到本地目录 |
| 同步 | 云端文件夹 / 自托管 | 支持 iCloud、Dropbox、Google Drive 或自建服务器 |
| Bot | Telegram Bot | 移动端快速输入入口 |

### 架构亮点

- **无构建系统** — 10年后打开 index.html 依然能运行
- **Vendor 所有依赖** — 第三方库直接包含在仓库中
- **一人或 LLM 可理解全项目** — 极简代码，方便 AI 扩展
- **细粒度锁机制** — 数据库级、日志级、配置级细粒度锁
- **追加式同步日志** — 基于文件重命名追踪的轻量同步方案

### 仓库结构

```
web/           → Web 应用 (PWA)，index.html 为入口
web/lib/       → 前端库
cmd/server/    → 服务器入口
cmd/*/         → 实用脚本（whoop指标、wiki链接转换等）
server/bot.go  → Telegram Bot
server/sync/   → 同步 API
vendor/        → 后端依赖
tests/         → E2E 测试
```

---

## 为什么火？Trending 原因分析

### 1. 反「Second Brain」浪潮中的清流
在 Obsidian、Notion 推动知识管理风靡全球的当下，files.md 大胆提出反对观点：知识管理工具越复杂，越阻碍真正的思考。引用 "I Deleted My Second Brain" 的观点，指出大量笔记只是在拖延真正的思维劳动。

### 2. 作者个人品牌加持
zakirullin 此前的 "Cognitive load is what matters" 在 HN 获得 721 条评论。files.md 的 Show HN 帖子获得 708 点 / 345 条评论。

### 3. 5年打磨的真诚作品
不是又一个 AI wrapper，而是开发者认真用了 5 年的工具。README 中详细的 ADR 展示了对每个设计选择的深思熟虑。

### 4. AI 时代的独特思考
强调「LLM 友好」但不依赖 AI，在当前 AI 过热的氛围中独树一帜。

### 5. 极致简化的技术哲学
无构建系统、无 Electron、无 npm——"10年后打开 index.html 还能运行"的理念击中了厌倦 JS 疲劳的开发者。

---

## 同类项目对比

| 特性 | files.md | Obsidian | Notion | Logseq |
|------|----------|----------|--------|--------|
| 开源 | ✅ 完全开源 | ❌ 核心闭源 | ❌ 闭源 | ✅ 开源 |
| 数据格式 | 纯 .md 文件 | 纯 .md 文件 | 私有数据库 | 纯 .md 文件 |
| 本地优先 | ✅ 完全本地 | ✅ 本地优先 | ❌ 云端 | ✅ 本地优先 |
| 安装需求 | 零安装（浏览器） | Electron 桌面 | 浏览器/桌面 | Electron 桌面 |
| 插件系统 | LLM 定制代码 | 丰富插件生态 | API 集成 | 插件生态 |
| 同步方案 | 云文件夹/自托管 | 付费 Sync | 内置云同步 | iCloud/Git |
| LLM 友好 | ✅ 专为 LLM 设计 | 一般 | 一般 | 一般 |
| 哲学 | 「限制催生创造力」 | 功能丰富 | 全能工作台 | 大纲+双向链接 |

---

## 适合谁使用？

- **🧠 深度思考者** — 厌倦「第二大脑」繁复，想回归纯粹思考
- **👨‍💻 开发者** — 喜欢纯文本、版本控制、可被 LLM 理解的工具链
- **🔒 隐私倡导者** — 数据绝不出设备，零隐私风险
- **🤖 AI 探索者** — 想用 LLM 定制笔记工具的极客
- **✍️ 写作者** — 通过知识链接和笔记复利产出深度文章
- **🚫 不适合：** 需要团队协作、复杂数据库视图、富媒体编辑的用户

---

## 快速上手

### 方式一：在线体验（零安装）

1. 打开 [app.files.md](https://app.files.md)（推荐 Chrome）
2. 点击地址栏右侧「Install files.md」安装为 PWA
3. 打开本地文件夹以持久化数据
4. 开始记录！

### 方式二：自托管同步服务器

```bash
git clone https://github.com/zakirullin/files.md.git
cd files.md
go build -o filesmd ./cmd/server
./filesmd
```

### 常用快捷键

| 快捷键 | 功能 |
|--------|------|
| `[` | 插入文件链接 |
| `Cmd/Ctrl + K` | 搜索文件 |
| `Cmd/Ctrl + N` | 新建文件 |
| `Cmd/Ctrl + Enter` | 打开聊天 |
| `Cmd/Ctrl + Y` | 插入复选框 |

---

## 综合评分

| 维度 | 分数 | 说明 |
|------|------|------|
| 创新性 | 8.5/10 | 哲学驱动的差异化定位，LLM 友好设计 |
| 代码质量 | 9.0/10 | 极简架构，详尽的 ADR 记录，5年打磨 |
| 实用性 | 9.2/10 | 零安装、离线可用、多端同步、Bot 辅助 |
| 文档完善度 | 8.0/10 | README 详尽但缺乏独立的用户文档站 |
| 社区活跃度 | 8.8/10 | HN 热议，作者持续维护，贡献指南清晰 |

### **总分：8.7 / 10**

> 一款用5年心血打磨的极简笔记工具，哲学深度和技术品质兼备。它不是最快的，不是最强的，但可能是最真诚的。

---

*分析日期: 2026-05-21 | 数据来源: GitHub, Hacker News, Trendshift*
