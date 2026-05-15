# joeseesun/qiaomu-anything-to-notebooklm 深度分析

> 多源内容智能处理器：任何内容 → 播客 / PPT / 思维导图 / Quiz
> 分析日期：2026-05-16

## 基本信息

| 项目 | 详情 |
|------|------|
| 仓库 | [joeseesun/qiaomu-anything-to-notebooklm](https://github.com/joeseesun/qiaomu-anything-to-notebooklm) |
| 语言 | Python |
| Stars | 2,545 |
| 今日新增 | +465 |
| 许可证 | MIT |
| 分类 | Claude Code Skill / 内容处理 / NotebookLM |

## 项目简介

**qiaomu-anything-to-notebooklm** 是一个 **Claude Code Skill**，用自然语言把任何内容变成任何格式。核心流程：

```
用户自然语言输入 → 智能识别内容源 → 获取内容（含付费墙绕过）→ 上传 NotebookLM → AI 生成目标格式
```

一句话即可完成全流程：
- "把这篇微信文章生成播客" → podcast.mp3
- "这个付费文章做成思维导图" → mindmap.json
- "这期播客做成 PPT" → slides.pdf（25页）

## 核心功能

### 15+ 种内容源
- **社交与媒体**：微信公众号（MCP浏览器模拟）、X/Twitter（推文+长线程）、YouTube（自动提取字幕）、播客（小宇宙/喜马拉雅/B站）
- **网页（含付费墙绕过）**：300+ 付费网站（NYT/WSJ/FT/Economist 等）、任意公开网页
- **电子书与文档**：PDF（支持扫描件OCR）、EPUB、Markdown、纯文本
- **Office 文档**：Word、PowerPoint、Excel
- **其他**：图片（自动OCR）、音频（自动转录）、ZIP压缩包（批量处理）

### 6 层付费墙绕过策略
```
Level 1: 代理服务（r.jina.ai / defuddle.md）
Level 2: 站点专属 Bot UA（Googlebot ~50站 / Bingbot ~4站）
Level 3: 通用绕过（UA伪装 + X-Forwarded-For + Referer伪装 + AMP + EU IP）
Level 4: archive.today 存档（CAPTCHA 自动检测）
Level 5: Google Cache
Level 6: agent-fetch 本地工具
```

### 8 种输出格式
播客（MP3）、PPT（PDF）、思维导图、Quiz、视频、报告、信息图、闪卡

### 深度分析模式
三轮递进式提问（概览→深度挖掘→综合反刍），利用 NotebookLM 会话上下文，生成 12 个深度问答，输出结构化 JSON。

## 技术架构

```
Claude Code Skill (SKILL.md)
├── 智能识别内容源类型
├── 内容获取层
│   ├── 微信 MCP (Playwright 浏览器模拟)
│   ├── 付费墙绕过 (6层级联 Shell 脚本)
│   ├── 播客转写 (Get笔记 API)
│   └── markitdown 文件转换
├── NotebookLM API (notebooklm-py CLI)
│   ├── 上传内容源
│   └── AI 生成目标格式
└── 输出文件 (.mp3 / .pdf / .json)
```

**技术栈**：Python 3.9+ / Shell / Playwright / MCP Protocol / notebooklm-py / markitdown / Get笔记 API

## 为什么火（Trending 原因）

1. **Claude Skills 生态爆发**：2026年 Claude Code Skills 成为最热门开发趋势之一，该项目是中文社区最完整的 Skill 实践
2. **NotebookLM 热度飙升**：Google NotebookLM 的 AI 播客功能全球爆火，该项目将命令行与 NotebookLM 完美结合
3. **付费墙绕过刚需**：6 层级联策略支持 300+ 付费网站，直击信息获取痛点
4. **中文生态深度适配**：微信公众号 MCP、小宇宙播客转写、飞书文档输出，填补市场空白
5. **视频教程带动**：Bilibili 和 YouTube 教程视频极大推动了传播
6. **极低使用门槛**：Python 3.9+ + Git，一句话自然语言触发全流程

## 同类项目对比

| 项目/工具 | 类型 | 输入源 | 输出格式 | 付费墙绕过 | 中文支持 |
|-----------|------|--------|----------|-----------|---------|
| **qiaomu (本项目)** | Claude Skill | 15+ 种 | 8 种 | 300+ 网站 | 深度适配 |
| notebooklm-py | Python CLI | 文本/文件 | 播客/Audio | 无 | 基础 |
| Wondercraft | SaaS | URL/文件 | 播客 | 无 | 基础 |
| Jellypod | SaaS | URL/文件 | 播客 | 无 | 有限 |
| ElevenLabs GenFM | API | 文本 | 播客/Audio | 无 | 基础 |
| SparkPod | SaaS | URL/文件 | 播客 | 无 | 基础 |

**核心优势**：内容源数量、付费墙绕过能力、中文生态适配和输出格式多样性方面均领先同类工具。

## 适合谁使用

- **知识工作者**：每天阅读大量内容，希望将碎片化内容转化为播客在通勤时收听
- **研究人员/学生**：深度分析论文、书籍，利用深度分析模式生成结构化洞察
- **中文互联网用户**：需要处理微信公众号、小宇宙播客、飞书文档等中文特有内容
- **Claude Code 开发者**：想通过 Skill 机制扩展 AI 能力，体验 Agent 工作流
- **内容创作者**：从多种来源聚合信息，生成思维导图、报告等二次创作素材

## 快速上手

### 安装（3步）

```bash
# 1. 克隆到 Claude skills 目录
cd ~/.claude/skills/
git clone https://github.com/joeseesun/qiaomu-anything-to-notebooklm
cd qiaomu-anything-to-notebooklm

# 2. 一键安装所有依赖
./install.sh

# 3. 配置 MCP 并重启 Claude Code
```

### 首次使用

```bash
notebooklm login    # NotebookLM 认证（只需一次）
notebooklm list     # 验证成功
./check_env.py      # 环境检查（可选）
```

### 使用示例

```
"把这篇 The Information 文章生成播客 https://..."
"这期小宇宙播客做成 PPT https://xiaoyuzhoufm.com/..."
"深度分析这本书 /Users/joe/Books/sapiens.epub"
"这个推文线程做成思维导图 https://x.com/..."
"深度分析这篇微信文章并写入飞书 https://mp.weixin.qq.com/..."
```

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | **8.5**/10 | 付费墙绕过 + NotebookLM + Claude Skills 的组合创新，6层级联策略设计精巧 |
| 代码质量 | **7.5**/10 | 结构清晰，模块化合理，Shell 和 Python 混合使用略复杂 |
| 实用性 | **9.0**/10 | 直击内容消费痛点，15+ 种输入源 + 8 种输出格式 |
| 文档完善度 | **9.0**/10 | README 极其详尽，含架构图、示例、FAQ、故障排查 |
| 社区活跃度 | **7.0**/10 | 快速增长中，中文社区反响热烈，国际知名度待提升 |

**综合评分：8.2 / 10 — 推荐使用**
