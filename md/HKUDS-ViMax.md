# ViMax 深度分析报告

> **HKUDS/ViMax** — Agentic Video Generation (导演、编剧、制片人、视频生成器四合一)

| 信息 | 详情 |
|------|------|
| **仓库** | [github.com/HKUDS/ViMax](https://github.com/HKUDS/ViMax) |
| **组织** | 香港大学数据科学实验室 (HKUDS) |
| **语言** | Python |
| **类型** | 多智能体视频生成框架 |
| **许可** | Open Source |
| **Trending日期** | 2026-05-21 |

---

## 项目简介

**ViMax** 是由香港大学数据科学实验室（HKUDS）开发的开源多智能体（Multi-Agent）视频生成框架。它将视频制作的四大核心角色——**导演（Director）**、**编剧（Screenwriter）**、**制片人（Producer）**和**视频生成器（Video Generator）**整合到一个自动化流水线中，实现了从创意想法到完整视频的端到端自动生成。

**核心价值**：只需输入一个简单的创意概念，ViMax 便能自动完成剧本创作、分镜设计、角色创建、参考图管理、一致性校验以及最终视频生成，全程无需人工干预。

---

## 核心功能

### 1. Idea2Video — 创意转视频
输入一个简单的创意概念（如"如果猫和狗是最好的朋友"），ViMax 自动完成从剧本到成片的全部流程。支持风格选择（卡通、写实等）和目标受众定制。

### 2. Novel2Video — 小说转视频
智能将完整小说转化为分集视频内容，包含叙事压缩、角色追踪和逐场景视觉适配。RAG 引擎确保关键情节和角色对话完整保留。

### 3. Script2Video — 剧本转视频
提供完整剧本即可生成视频，支持对镜头数量、节奏、场景设计等精细控制。适合有明确创作意图的内容创作者。

### 4. AutoCameo — 个人客串
上传你的照片，ViMax 智能将你作为角色融入视频中，在整个视频中保持一致的外貌和自然的互动。

---

## 技术架构

ViMax 采用分层多智能体架构，整个流水线分为以下层次：

### 架构流程

```
INPUT LAYER（创意 & 剧本 & 小说 | 自然语言提示 | 参考图片 | 风格指令）
    ↓
CENTRAL ORCHESTRATION（智能体调度 | 阶段转换 | 资源管理 | 重试/回退）
    ↓
SCRIPT UNDERSTANDING（角色/环境提取 | 场景边界 | 风格意图）
    +
SCENE & SHOT PLANNING（分镜步骤 | 镜头列表 | 关键帧 & 节拍）
    ↓
VISUAL ASSET PLANNING（参考图选择 | 风格引导 | 提示词条件化）
    ↓
ASSET INDEXING（帧/参考目录 | 嵌入向量 | 检索复用）
    +
CONSISTENCY & CONTINUITY（角色/环境追踪 | 参考匹配 | 时间一致性）
    ↓
VISUAL SYNTHESIS & ASSEMBLY（图像生成 | 最优帧选择 | 首尾帧→视频 | 剪辑组装）
    ↓
OUTPUT LAYER（帧 | 片段 & 最终视频 | 日志 | 工作目录产物）
```

### 关键技术亮点

- **🧬 RAG 长脚本生成引擎** — 智能分析长篇小说类故事，自动分割为多场景剧本，保留所有关键情节和对话
- **🪄 表现力分镜设计** — 基于摄影语言创建富有表现力的分镜，为后续视频生成建立叙事节奏
- **🔮 多机位拍摄模拟** — 模拟多摄像机拍摄，在保持角色位置和背景一致的同时提供沉浸式观看体验
- **🧸 智能参考图选择** — 智能选择当前视频首帧所需的参考图，确保多角色和环境元素的准确性
- **✅ 自动一致性校验** — 并行生成多张图像，通过 MLLM/VLM 模仿人类创作者工作流程选择最佳图像
- **⚡ 高效并行镜头生成** — 对同一摄像机的连续镜头进行并行处理，实现高效视频制作

---

## 为什么火（Trending 原因）

### 1. 填补市场空白
目前市面上几乎所有的 AI 视频工具（Sora、Runway、Veo）都只关注"文生视频"的单步操作。ViMax 是唯一一个开源的、端到端的多智能体视频生成框架，覆盖从创意到成片的完整流程。

### 2. 解决核心痛点
AI 视频生成长期面临三大痛点：只能生成几秒短片、角色/场景不一致、缺乏叙事结构。ViMax 从架构层面同时解决了这三个问题。

### 3. 学术背景背书
来自香港大学数据科学实验室，学术严谨性与工程实用性兼具。已在多个社交平台和开发者社区引发广泛关注。

### 4. 时机契合
2026 年是 Agentic AI 的爆发年，多智能体框架成为最热趋势。ViMax 将这一趋势与视频生成结合，精准踩中了技术浪潮。

---

## 应用场景

| 场景 | 说明 |
|------|------|
| 🎬 短视频创作 | 快速将创意想法转化为完整短视频，适合 YouTube Shorts、TikTok 等平台 |
| 📚 小说/IP改编 | 将小说内容自动转化为视频剧集，适合 IP 孵化、故事板预可视化 |
| 🎓 教育培训 | 自动生成教学视频、培训材料，将文字教材转化为生动视频内容 |
| 🎮 游戏预告片 | 基于游戏设定和故事线自动生成游戏预告片和宣传片 |
| 📺 广告营销 | 快速生成产品宣传视频、品牌故事视频，降低制作成本 |
| 🔬 AI 研究 | 作为多智能体视频生成的研究平台，探索 AI 创意的边界 |

---

## 同类项目对比

| 维度 | ViMax (HKUDS) | OpenAI Sora | Google Veo 3 | Runway Gen-4 | Mora |
|------|:---:|:---:|:---:|:---:|:---:|
| **开源** | ✅ | ❌ | ❌ | ❌ | ✅ |
| **多智能体** | ✅ 4+ Agent | ❌ | ❌ | ❌ | 多模块 |
| **端到端流程** | ✅ 创意→成片 | 文本/图→视频 | 文本/图→视频 | 文本/图→视频 | 文本→视频 |
| **角色一致性** | ✅ 自动校验 | 有限 | 较好 | 有限 | 有限 |
| **长视频支持** | ✅ 多场景拼接 | ~20s | ~60s | ~30s | 短片段 |
| **视觉质量** | 依赖底层模型 | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ |
| **脚本生成** | ✅ 内置 | ❌ | ❌ | ❌ | ❌ |
| **成本** | API调用费 | 订阅制 | 订阅制 | 订阅制 | 免费/自部署 |

**ViMax 的独特定位**：它不是一个视频生成模型，而是一个**编排框架**。它可以灵活接入不同的底层模型（Gemini、Veo、MiniMax 等），专注于解决"如何将创意组织成有叙事结构的视频"这一更高层次的问题。

---

## 适合谁使用

- **🧑‍💻 AI 应用开发者** — 希望构建视频生成应用的开发者，可以利用 ViMax 作为核心框架
- **🎬 独立内容创作者** — 没有专业视频制作团队，但希望快速将创意转化为视频
- **🔬 AI 研究人员** — 研究多智能体系统、AI 创意生成、视频一致性等方向
- **📚 教育工作者** — 希望将文字教材自动转化为视频课程

> **注意**：使用 ViMax 需要一定的编程基础（Python），且需要配置各 AI 模型的 API Key（如 Google AI Studio、OpenRouter、MiniMax 等）。

---

## 快速上手指南

### 1. 克隆并安装

```bash
# 克隆仓库
git clone https://github.com/HKUDS/ViMax.git
cd ViMax

# 使用 uv 安装依赖（推荐）
uv sync
```

### 2. 配置 API Key

编辑 `configs/idea2video.yaml`：

```yaml
chat_model:
  init_args:
    model: google/gemini-2.5-flash-lite-preview-09-2025
    model_provider: openai
    api_key: <YOUR_API_KEY>
    base_url: https://openrouter.ai/api/v1

image_generator:
  class_path: tools.ImageGeneratorNanobananaGoogleAPI
  init_args:
    api_key: <YOUR_API_KEY>

video_generator:
  class_path: tools.VideoGeneratorVeoGoogleAPI
  init_args:
    api_key: <YOUR_API_KEY>
```

### 3. 运行创意生成

编辑 `main_idea2video.py` 中的创意：

```python
idea = """
如果一只猫和一只狗是最好的朋友，它们遇到一只新猫会发生什么？
"""
user_requirement = """
面向儿童，不超过3个场景。
"""
style = "Cartoon"

# 运行
# python main_idea2video.py
```

### 4. 使用 MiniMax 模型（可选）

MiniMax 支持超长上下文（1M tokens），适合长篇小说转视频：

```yaml
chat_model:
  init_args:
    model: MiniMax-M2.7
    model_provider: minimax
    api_key: <YOUR_MINIMAX_API_KEY>
```

| 模型 | 上下文 | 备注 |
|------|--------|------|
| MiniMax-M2.7 | 1M tokens | 最新，推荐 |
| MiniMax-M2.7-highspeed | 1M tokens | 快速变体 |
| MiniMax-M2.5 | 204K tokens | 稳定版 |
| MiniMax-M2.5-highspeed | 204K tokens | 快速变体 |

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|:---:|------|
| **创新性** | ⭐ 9.0/10 | 首个开源多智能体端到端视频生成框架，概念创新且设计完整 |
| **代码质量** | ⭐ 8.5/10 | 架构清晰，模块化设计，支持多种底层模型接入 |
| **实用性** | ⭐ 8.5/10 | 四大使用模式覆盖主要需求，快速上手，但依赖外部 API |
| **文档完善度** | ⭐ 8.0/10 | README 详细，架构图清晰，缺少 API 深度文档和教程 |
| **社区活跃度** | ⭐ 7.8/10 | 新项目，Trending 热度上升中，持续更新 |

### 综合评分：**8.4 / 10**

---

*Generated on 2026-05-21 | [GitHub - HKUDS/ViMax](https://github.com/HKUDS/ViMax)*
