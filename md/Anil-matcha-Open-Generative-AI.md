# Open-Generative-AI — 开源 AI 图像与视频生成工作室

> **Anil-matcha/Open-Generative-AI** | JavaScript | 14,073 Stars | +356 today
> 
> 开源 AI 视频/图像平台的免费替代方案，集成 200+ SOTA 模型，无内容过滤，可自部署，MIT 许可。

---

## 项目简介与核心功能

Open-Generative-AI 是一个**一站式 AI 创意媒体生成平台**，将图像生成、视频生成、唇形同步、电影级拍摄、工作流编排整合到同一个现代化界面中。项目由 Anil Chandra Naidu Matcha 开发，前身为 Open-Higgsfield-AI，后扩展为通用生成式 AI 工具。

### 六大工作室

| 工作室 | 功能 | 模型数 |
|--------|------|--------|
| **Image Studio** | 文生图 / 图生图（双模式自动切换） | 105+ |
| **Video Studio** | 文生视频 / 图生视频 | 100+ |
| **Lip Sync Studio** | 人像驱动 / 视频口型同步 | 9 |
| **Cinema Studio** | 电影级虚拟摄影控制 | — |
| **Workflow Studio** | 可视化多步骤 AI 管道编排 | — |
| **Local Inference** | 本地模型推理（sd.cpp / Wan2GP） | 11 |

### 核心亮点

- **200+ 模型一站式访问**：Flux、Midjourney、Kling、Sora、Veo、Seedream、Wan、Hunyuan 等主流模型全覆盖
- **零内容过滤**：无审查、无提示词拦截，完整创作自由
- **多图输入**：最多支持 14 张参考图输入（Nano Banana 2 Edit）
- **本地推理**：桌面端支持 sd.cpp（Metal/CUDA/Vulkan）和 Wan2GP 两种引擎
- **跨平台桌面应用**：macOS / Windows / Linux 均有一键安装包
- **完全自部署**：数据留在本地，无厂商锁定

---

## 技术架构与特点

### 技术栈

```
Next.js 14 (App Router) + React 18 + Tailwind CSS v3 + Electron
├── npm workspaces monorepo
├── packages/studio — 共享 React 组件库（模型定义、API 客户端）
├── Vite proxy 处理 CORS
└── Muapi.ai 作为 AI 模型 API 网关
```

### 架构设计

```
Open-Generative-AI/
├── app/                    # Next.js App Router
├── components/             # Shell、API Key 管理
├── packages/studio/src/    # 核心 SDK
│   ├── models.js           # 200+ 模型定义（单一数据源）
│   ├── muapi.js            # API 客户端
│   └── components/         # 各工作室 UI 组件
└── electron/               # 桌面端封装
```

### 关键技术特点

1. **双模式自动切换**：Image/Video Studio 根据是否上传参考图自动切换 t2i/i2i 或 t2v/i2v 模式
2. **统一模型管理**：所有模型定义集中在 `models.js`，一处更新全局生效
3. **两步异步 API 模式**：Submit → Poll 轮询，支持长时间生成任务
4. **本地推理双引擎**：sd.cpp（打包集成，支持 Metal GPU）+ Wan2GP（外部 Python 服务器）
5. **工作流编排引擎**：基于 Vibe-Workflow 子模块的节点式可视化管道

---

## 应用场景

| 场景 | 说明 |
|------|------|
| **内容创作者** | 快速生成社交媒体图片、短视频素材 |
| **独立游戏开发** | 批量生成角色立绘、场景概念图 |
| **影视前期** | Cinema Studio 模拟虚拟摄影，快速出分镜 |
| **AI 数字人** | Lip Sync Studio 生成口型同步的虚拟主播视频 |
| **自动化媒体管道** | Workflow Studio + Generative-Media-Skills 驱动 AI Agent 批量生产 |
| **本地隐私创作** | 自部署 + 本地推理，适合敏感内容创作 |

---

## 为什么火（Trending 原因）

1. **踩中 AI 视频爆发节点**：2025-2026 年 AI 视频生成技术井喷（Sora、Kling、Veo），用户迫切需要统一入口管理这些碎片化的模型
2. **"零过滤"定位引爆传播**：在主流平台普遍加强内容审查的背景下，"No content filters" 成为强烈卖点，在 Reddit、Instagram 等社区病毒式传播
3. **降低使用门槛**：200+ 模型通过一个 API Key（Muapi.ai）统一访问，不需要分别注册各家平台
4. **桌面应用覆盖广**：一键安装包覆盖 macOS/Windows/Linux，非技术用户也能使用
5. **MIT 开源许可**：商业友好的开源协议，吸引开发者参与和二次开发
6. **社交媒体助推**：创作者在 Instagram Reels、LinkedIn 上广泛传播"整个十亿级 AI 视频栈现在免费了"的概念

---

## 同类项目对比

| 特性 | Open-Generative-AI | ComfyUI | AUTOMATIC1111 SD WebUI | Midjourney | Runway |
|------|---------------------|---------|------------------------|------------|--------|
| **开源** | MIT | GPL | AGPL | 否 | 否 |
| **模型数量** | 200+（API 聚合） | 大量自定义节点 | SD 系列 | 专有 | 专有 |
| **图像生成** | 50+ T2I / 55+ I2I | 支持 | 支持 | 支持 | 有限 |
| **视频生成** | 40+ T2V / 60+ I2V | 通过节点 | 有限 | 有限 | 支持 |
| **Lip Sync** | 9 个模型 | 社区插件 | 无 | 无 | 无 |
| **本地推理** | sd.cpp + Wan2GP | 原生 | 原生 | 无 | 无 |
| **桌面应用** | Electron | 无 | 无 | 无 | 无 |
| **使用门槛** | 低（一键安装） | 高（节点式） | 中 | 低（Discord） | 低 |
| **费用** | 免费 + API 按量 | 免费 | 免费 | 订阅制 | 订阅制 |

**核心差异**：Open-Generative-AI 是**聚合器**而非推理框架——它把 200+ 商业和开源模型统一到一个 UI 中，通过 Muapi.ai API 网关转发请求。ComfyUI 和 SD WebUI 则是本地推理工具。

---

## 适合谁使用

| 用户类型 | 适合度 | 原因 |
|----------|--------|------|
| **内容创作者 / 自媒体** | ★★★★★ | 一站式生成图片视频，无需多个平台 |
| **AI 艺术探索者** | ★★★★★ | 200+ 模型自由切换，零过滤 |
| **独立开发者** | ★★★★☆ | MIT 许可，可嵌入自己的产品 |
| **AI Agent 开发者** | ★★★★☆ | Generative-Media-Skills 支持 Claude Code / Codex 驱动 |
| **企业级用户** | ★★★☆☆ | 依赖第三方 API（Muapi.ai），自部署需考虑稳定性 |
| **硬核本地推理用户** | ★★★☆☆ | 本地推理引擎仍在早期，不如 ComfyUI 灵活 |

---

## 快速上手指南

### 方式一：桌面应用（推荐新手）

1. 前往 [Releases](https://github.com/Anil-matcha/Open-Generative-AI/releases) 下载对应平台安装包
2. 安装并启动（macOS 需执行 `xattr -cr "/Applications/Open Generative AI.app"`）
3. 启动后输入 Muapi.ai API Key（免费注册获取）
4. 选择工作室，输入提示词，点击 Generate

### 方式二：从源码构建

```bash
# 克隆（含子模块）
git clone --recurse-submodules https://github.com/Anil-matcha/Open-Generative-AI.git
cd Open-Generative-AI

# 安装依赖并构建工作区包
npm run setup

# 启动桌面应用（Electron）
npm run electron:dev

# 或启动 Web 版（Next.js）
npm run dev
```

### 方式三：在线体验

访问 https://dev.muapi.ai/open-generative-ai ，注册免费账号即可在浏览器中使用。

### 本地模型推理（桌面端）

1. 打开 Settings → Local Models
2. 安装 sd.cpp 引擎（一键下载）
3. 下载模型（推荐 Dreamshaper 8，仅 2.1GB）
4. 在 Image Studio 点击 ⚡ Local 切换到本地推理

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | ★★★★☆ (8/10) | 作为聚合器定位独特，但底层模型非自研；本地推理双引擎设计有亮点 |
| **代码质量** | ★★★★☆ (7.5/10) | Monorepo 结构清晰，模型管理单一数据源设计优雅；但部分组件耦合较紧 |
| **实用性** | ★★★★★ (9/10) | 解决了 200+ 模型碎片化的真实痛点，桌面应用覆盖主流 OS |
| **文档完善度** | ★★★★★ (9/10) | README 超级详细，包含架构图、模型列表、安装指南、硬件说明、故障排除 |
| **社区活跃度** | ★★★★☆ (8/10) | 14K+ Stars 快速增长，Reddit/Instagram 病毒传播；但贡献者集中度高 |

**综合评分：8.3 / 10**

---

## 总结

Open-Generative-AI 是当前最全面的**开源 AI 创意媒体聚合平台**。它不是推理引擎，而是一个精心设计的统一入口，让用户通过一个界面访问 200+ AI 图像/视频模型。在 AI 视频生成技术井喷的 2025-2026 年，这种"一站式+零过滤+可自部署"的定位精准击中了创作者和开发者的需求，这也是它能快速获得 14K+ Stars 的核心原因。

对于想要快速体验多种 AI 生成模型、不想在多个平台之间切换的用户来说，这是目前最好的选择。但需要注意，云端生成依赖 Muapi.ai 第三方 API，重度用户需关注 API 成本和可用性。

---

*分析日期：2026-05-17 | 数据来源：GitHub、Web Search*
