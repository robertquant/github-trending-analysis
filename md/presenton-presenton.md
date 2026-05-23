# Presenton - 开源 AI 演示文稿生成器 & API

> GitHub Trending 深度分析 | 2026-05-24

| 信息 | 详情 |
|------|------|
| **项目** | [presenton/presenton](https://github.com/presenton/presenton) |
| **Stars** | ~5,900 |
| **License** | Apache 2.0 |
| **语言** | TypeScript / Python |
| **定位** | Gamma / Beautiful AI / Decktopus 的开源替代品 |

---

## 项目简介 & 核心功能

Presenton 是一款完全开源的 AI 演示文稿生成工具，支持通过自然语言提示词或上传文档自动生成专业的 PPT 演示文稿。最大特色是**无 SaaS 锁定、无强制订阅、完全掌控模型和数据**。

**核心功能：**

- **AI 演示文稿生成** — 从自然语言提示词或上传文档（PDF、Word 等）自动生成完整演示文稿，支持自定义幻灯片数量、语言、语调和模板
- **自定义模板 & 布局** — 使用 HTML + Tailwind CSS 创建无限自定义设计模板，支持从现有 PowerPoint 文档逆向生成 AI 模板
- **完全本地化 / 自托管** — 通过 Docker 一键部署或使用桌面应用（Mac/Windows/Linux），所有数据处理在本地完成
- **多模型支持 (BYOK)** — 支持 OpenAI、Gemini、Anthropic、Azure、Bedrock、Fireworks、Together、Ollama、LM Studio 等十余种 LLM 提供商
- **演示文稿生成 API** — 内置 RESTful API 服务，支持 HTTP Basic Auth 认证，可集成到自动化工作流
- **PPTX & PDF 导出** — 生成完全可编辑的 PowerPoint 或 PDF 格式

---

## 技术架构 & 特点

Presenton 采用 **Next.js (前端) + FastAPI (后端) + Electron (桌面封装)** 的三层架构：

| 层级 | 技术栈 | 说明 |
|------|--------|------|
| 前端 UI | Next.js + React + Tailwind CSS | 幻灯片编辑器，实时预览，模板管理 |
| 后端 API | Python FastAPI + SQLAlchemy | LLM 调度、文档解析、演示文稿生成引擎 |
| 桌面封装 | Electron | 原生桌面应用，支持离线使用 |
| AI 记忆 | Mem0 OSS + Qdrant + FastEmbed | 按演示文稿级别的 AI 上下文记忆 |
| 文档解析 | LiteParse (OCR) | PDF/Word 文档解析和内容提取 |
| 图像生成 | DALL-E 3 / Gemini Flash / Pexels / Pixabay / ComfyUI | 多源图像生成和素材集成 |
| 本地模型 | Ollama / LM Studio | 完全离线运行，GPU 加速支持 |
| MCP 协议 | Built-in MCP Server | 支持 Model Context Protocol 远程调用 |

---

## 应用场景

- **企业内部培训** — 快速将培训文档转化为交互式演示文稿
- **产品路演 & 融资展示** — 从产品描述自动生成专业 Pitch Deck
- **学术报告** — 将研究论文或数据报告转为可视化演示
- **自动化批量生成** — 通过 API 集成到 CI/CD 或数据管道，定期生成报告型演示文稿
- **教育内容创作** — 教师从课程大纲一键生成课件
- **销售 & 营销团队** — 从 CRM 数据自动生成客户定制化演示

---

## 为什么火（Trending 原因）

1. **填补开源 AI 演示工具空白** — AI 演示工具市场被 Gamma、Beautiful AI 等 SaaS 产品垄断，Presenton 以 Apache 2.0 许可证填补了这一空白
2. **BYOK 模式击中隐私痛点** — 支持自托管 + Ollama 本地模型，企业和个人无需将数据发送到第三方 SaaS
3. **多模型支持降低门槛** — 支持十余种 LLM 提供商（包括 ChatGPT 登录直连），用户无需切换工具
4. **API-first 设计满足企业需求** — 内置 REST API + MCP Server，可轻松集成到自动化工作流
5. **社区驱动的模板生态** — 自定义模板使用 HTML + Tailwind CSS，开发者可快速创建精美模板

---

## 同类项目对比

| 特性 | Presenton | Gamma | Beautiful AI | Marp |
|------|-----------|-------|-------------|------|
| 开源 | Apache 2.0 | 商业 SaaS | 商业 SaaS | MIT |
| 自托管 | Docker / Desktop | 否 | 否 | 本地 CLI |
| AI 生成 | 多模型 | 内置 AI | DesignerBot | 无 |
| PPTX 导出 | 完全可编辑 | 有限 | 是 | 是 |
| API 接口 | REST API + MCP | 否 | 企业版 | 无 |
| 本地模型 | Ollama / LM Studio | 无 | 无 | 无 |
| 自定义模板 | HTML+Tailwind | 有限 | 品牌模板 | Markdown+CSS |
| 价格 | 免费 (仅付 API 费) | 免费受限/Pro $10/月 | Pro $12/月 | 免费 |

---

## 适合谁使用

- **开发者 & 工程师** — 需要 API 集成到自动化流程、喜欢 Docker 部署的技术用户
- **企业 IT 团队** — 需要自托管 AI 工具、数据不出内网的企业
- **教育工作者** — 需要快速将课程资料转化为课件的老师和培训师
- **数据分析师** — 需要定期将数据报告生成演示文稿的分析师

---

## 快速上手指南

### 方式一：Docker 一键启动（推荐）

```bash
# 拉取并运行 Presenton
docker run -it --name presenton -p 5000:80 \
  -v "./app_data:/app_data" \
  ghcr.io/presenton/presenton:latest

# 使用 OpenAI 模型
docker run -it --name presenton -p 5000:80 \
  -e LLM="openai" \
  -e OPENAI_API_KEY="sk-xxx" \
  -e IMAGE_PROVIDER="dall-e-3" \
  -v "./app_data:/app_data" \
  ghcr.io/presenton/presenton:latest

# 使用 Ollama 本地模型（完全离线）
docker run -it --name presenton -p 5000:80 \
  -e LLM="ollama" \
  -e OLLAMA_MODEL="llama3.2:3b" \
  -v "./app_data:/app_data" \
  ghcr.io/presenton/presenton:latest
```

### 方式二：API 调用生成演示文稿

```bash
curl -u admin:password \
  -X POST http://localhost:5000/api/v1/ppt/presentation/generate \
  -H "Content-Type: application/json" \
  -d '{
    "content": "AI 技术在金融领域的应用",
    "n_slides": 8,
    "language": "Chinese",
    "template": "general",
    "export_as": "pptx"
  }'
```

### 方式三：桌面应用

```bash
git clone https://github.com/presenton/presenton.git
cd presenton/electron
npm run setup:env
npm run dev
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 8.5/10 | 开源 AI 演示工具赛道的先行者，BYOK 模式创新 |
| 代码质量 | 8.0/10 | 架构清晰，多语言栈组织合理，但项目较新需要时间验证 |
| 实用性 | 9.0/10 | 直接解决实际需求，部署简单，API 设计合理 |
| 文档完善度 | 9.0/10 | README 详尽覆盖所有部署场景和配置项，API 文档完善 |
| 社区活跃度 | 8.5/10 | 快速增长中（~5,900 Stars），Reddit/Dev.to 活跃讨论 |

**综合评分: 8.6 / 10**

---

## 分析总结

Presenton 是目前 GitHub 上最成熟的开源 AI 演示文稿生成项目。它精准切中了市场痛点：AI 演示工具市场缺乏高质量开源替代品。通过 BYOK 模式和多模型支持，为用户提供了前所未有的灵活性。适合对数据隐私有要求的企业、需要批量生成演示文稿的自动化场景，以及希望摆脱 SaaS 订阅的个人用户。

---

*GitHub: [presenton/presenton](https://github.com/presenton/presenton) | 官网: [presenton.ai](https://presenton.ai)*

*AI 深度分析 | Powered by Claude Code | 2026-05-24*