# notebooklm-py - GitHub Trending 深度分析

> **teng-lin/notebooklm-py** | ⭐ 12,385+ Stars | 🐍 Python 3.10+ | 📄 MIT License | 🔥 24h 爆款

## 📖 项目简介与核心功能

**notebooklm-py** 是由 [teng-lin](https://github.com/teng-lin) 开发的非官方 Python 库，通过逆向工程 Google NotebookLM 的未公开 RPC API，为开发者提供**完整的编程接口**来操控 NotebookLM 的所有功能。

**核心亮点：** 不仅实现了 Web UI 的全部功能，更暴露了 Web UI 不具备的高级能力——批量下载、结构化导出、PPTX 幻灯片、思维导图 JSON 提取等。

### 三大使用方式

| 方式 | 适用场景 | 入口 |
|------|----------|------|
| **Python API** | 应用集成、异步工作流、自定义管道 | `from notebooklm import NotebookLMClient` |
| **CLI** | Shell 脚本、快速任务、CI/CD 自动化 | `notebooklm <command>` |
| **Agent 集成** | Claude Code、Codex、LLM Agent 自然语言自动化 | `npx skills add teng-lin/notebooklm-py` |

---

## ⚡ 功能全景

### 笔记本与来源管理
- **笔记本**：创建、列表、重命名、删除
- **来源**：URL、YouTube、PDF、文本、Markdown、Word、EPUB、音频、视频、图片、Google Drive、粘贴文本

### 内容生成（全部制品类型）

| 类型 | 选项 | 下载格式 |
|------|------|----------|
| 音频概览 | 4格式（深度/简报/评论/辩论）、3长度、50+语言 | MP3/MP4 |
| 视频概览 | 3格式（讲解/简报/电影感）、9视觉风格 | MP4 |
| 幻灯片 | 详细/演示者格式，可调长度，单张修订 | PDF、PPTX |
| 信息图 | 3方向、3细节级别 | PNG |
| 测验 | 可配置数量和难度 | JSON、Markdown、HTML |
| 闪卡 | 可配置数量和难度 | JSON、Markdown、HTML |
| 报告 | 简报、学习指南、博客文章、自定义提示 | Markdown |
| 数据表 | 自然语言自定义结构 | CSV |
| 思维导图 | 交互式层级可视化 | JSON |

### 研究 Agent
- Web 和 Google Drive 研究代理（快速/深度模式），自动导入来源

### 对话与分享
- 基于来源的问答、对话历史、自定义人设
- 公开/私密链接、用户权限（查看者/编辑者）、保存对话到笔记

### 超越 Web UI 的能力
- 批量下载所有制品
- 测验/闪卡结构化导出（JSON/Markdown/HTML）
- 思维导图层级 JSON 提取
- 数据表 CSV 导出
- PPTX 可编辑幻灯片
- 单张幻灯片自然语言修订
- 来源全文访问
- 程序化权限管理
- 多账户配置切换
- 浏览器 Cookie 导入

---

## 🏗️ 技术架构与特点

- **逆向工程 API**：通过捕获和分析 NotebookLM 的内部 RPC 调用，实现完整封装
- **异步架构**：基于 `asyncio` 的异步设计，支持高效并发操作
- **认证机制**：Playwright 浏览器自动化获取 Google 认证 Cookie，支持多账户和 Cookie 导入
- **三端统一**：Python API / CLI / Agent Skill 共享同一核心引擎
- **跨平台**：macOS、Linux、Windows 全支持，CI 全平台测试
- **Agent 生态**：内置 Claude Code Skill、Codex AGENTS.md、`npx skills` 发现

```python
import asyncio
from notebooklm import NotebookLMClient

async def main():
    async with await NotebookLMClient.from_storage() as client:
        nb = await client.notebooks.create("Research")
        await client.sources.add_url(nb.id, "https://example.com", wait=True)
        result = await client.chat.ask(nb.id, "Summarize this")
        print(result.answer)
        await client.artifacts.generate_audio(nb.id, instructions="make it fun")
        await client.artifacts.download_audio(nb.id, "podcast.mp3")

asyncio.run(main())
```

---

## 🔥 为什么火（Trending 原因）

1. **填补官方 API 空白**：Google NotebookLM 没有公开 API，开发者一直被 Web UI 限制。这个项目直接解锁了全部编程能力
2. **超越 Web UI**：不仅复刻了全部功能，还暴露了 Web UI 不支持的能力
3. **AI Agent 原生支持**：内置 Claude Code Skill 和 Codex 支持，踩中 Agent 热潮
4. **病毒式传播**：24 小时内获得 12,385 Stars，在 Reddit、LinkedIn、Threads、Instagram 全面引爆
5. **NotebookLM 热度飙升**：Google NotebookLM 本身正在快速增长，音频播客功能爆红
6. **文档与体验出色**：6 种用户角色的安装指南、完整的 CLI/API 文档

---

## 🎯 应用场景

| 场景 | 说明 | 示例 |
|------|------|------|
| 研究自动化 | 批量导入来源，运行研究查询，提取洞察 | 学术论文批量摘要、竞品分析 |
| 内容工厂 | 从文档自动生成播客、视频、幻灯片 | 每周技术报告 → 自动生成播客 |
| 教育工具 | 生成测验、闪卡、学习指南 | 教材 → 互动测验 + 闪卡 + 思维导图 |
| AI Agent 编排 | 让 Claude Code / Codex 直接操控 NotebookLM | 自动研究 → 生成报告 → 导出 |
| 知识管理 | 程序化管理笔记、来源、分享权限 | 团队知识库自动更新与分发 |

---

## ⚖️ 同类项目对比

| 项目 | 特点 | 对比 |
|------|------|------|
| **notebooklm-py**（本项目） | 全功能覆盖、Python API+CLI+Agent、超越 Web UI、跨平台、MIT | ✅ 最全面 |
| **NotebookLlama**（Meta） | 仅 PDF→播客管道，基于 Llama 模型 | ❌ 功能范围极窄 |
| **NotebookLM 企业 API**（Google） | 功能有限，仅面向大型组织 | ❌ 普通开发者无法使用 |
| **浏览器自动化脚本** | Selenium/Puppeteer 模拟操作 | ❌ 脆弱易断，无结构化 API |
| **自建 RAG 系统**（Gemini API） | 需从零构建 | ❌ 缺少内容生成能力 |

---

## 👥 适合谁使用

| 用户类型 | 推荐度 | 理由 |
|----------|--------|------|
| AI/ML 开发者 | ⭐⭐⭐⭐⭐ | API 集成到自定义管道，Agent 技能扩展能力边界 |
| 研究人员 | ⭐⭐⭐⭐⭐ | 批量研究自动化，论文摘要，洞察提取 |
| 教育工作者 | ⭐⭐⭐⭐⭐ | 一键生成测验、闪卡、学习指南、思维导图 |
| 内容创作者 | ⭐⭐⭐⭐ | 从文档自动生成播客、视频、幻灯片 |
| Agent 开发者 | ⭐⭐⭐⭐⭐ | 内置 Claude Code/Codex 技能，直接纳入工作流 |
| 产品经理 | ⭐⭐⭐ | CLI 快速上手，但需基本命令行能力 |

> ⚠️ **注意**：本库使用 Google 未公开 API，可能随时变更。适合原型、研究和个人项目，不建议用于关键生产环境。

---

## 🚀 快速上手指南

### 1. 安装

```bash
pip install "notebooklm-py[browser]"   # 核心库 + Playwright
playwright install chromium             # 安装浏览器（~170 MB）
```

### 2. 认证

```bash
notebooklm login                       # 打开浏览器登录 Google
notebooklm auth check --test --json    # 验证认证状态
```

### 3. 创建笔记本并添加来源

```bash
notebooklm create "My Research"
notebooklm use <notebook_id>
notebooklm source add "https://en.wikipedia.org/wiki/Artificial_intelligence"
notebooklm source add "./paper.pdf"
```

### 4. 对话与生成内容

```bash
notebooklm ask "What are the key themes?"
notebooklm generate audio "make it engaging" --wait
notebooklm generate video --style whiteboard --wait
notebooklm generate quiz --difficulty hard
notebooklm generate mind-map
```

### 5. 下载制品

```bash
notebooklm download audio ./podcast.mp3
notebooklm download quiz --format markdown ./quiz.md
notebooklm download mind-map ./mindmap.json
```

---

## 📊 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | 9.0/10 | 逆向工程未公开 API，暴露超越 Web UI 的能力 |
| **代码质量** | 8.5/10 | 异步架构、跨平台 CI、结构清晰 |
| **实用性** | 9.5/10 | 填补 Google 官方 API 空白，Agent 生态集成 |
| **文档完善度** | 9.0/10 | 6种用户角色安装指南，完整 API/CLI 文档 |
| **社区活跃度** | 9.5/10 | 24h 12K+ Stars，社交媒体病毒传播 |

### 🏆 综合评分：9.1 / 10 · 极力推荐

---

## 🔗 相关链接

- **GitHub 仓库**：[github.com/teng-lin/notebooklm-py](https://github.com/teng-lin/notebooklm-py)
- **PyPI**：[pypi.org/project/notebooklm-py](https://pypi.org/project/notebooklm-py/)
- **Medium 文章**：[NotebookLM-py: The CLI Tool That Unlocks Google NotebookLM](https://medium.com/@tentenco/notebooklm-py-the-cli-tool-that-unlocks-google-notebooklm-1de7106fd7ca)
- **Reddit 讨论**：[r/notebooklm 社区讨论](https://www.reddit.com/r/notebooklm/comments/1qbopkm/)
- **TrendShift**：[trendshift.io 趋势追踪](https://trendshift.io/repositories/19116)

---

📊 GitHub Trending 深度分析 | 2026-05-22 | Powered by Claude Code AI