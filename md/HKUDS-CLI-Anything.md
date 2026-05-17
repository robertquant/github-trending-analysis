# CLI-Anything 深度分析：让所有软件变为 Agent 原生

> **GitHub:** [HKUDS/CLI-Anything](https://github.com/HKUDS/CLI-Anything) | **Stars:** 35,338 (+333) | **语言:** Python | **协议:** Apache 2.0

---

## 项目简介

**CLI-Anything** 是香港大学数据科学实验室 (HKUDS) 推出的开源项目，核心理念：**将任何有源代码的软件自动转化为 AI Agent 可直接调用的命令行工具**。

无需 API、无需 GUI 自动化、无需重建软件 — 一条命令即可让 Agent 原生控制专业级软件。

### 核心功能

- **七阶段自动化流水线**：从代码分析到 PyPI 发布全自动
  1. Analyze — 扫描源码，映射 GUI 到 API
  2. Design — 设计命令组和状态模型
  3. Implement — 构建 Click CLI + REPL + JSON 输出
  4. Plan Tests — 创建测试计划
  5. Write Tests — 实现完整测试套件
  6. Document — 更新文档
  7. Publish — 打包发布
- **CLI-Hub 包管理器**：统一管理、安装、更新所有社区 CLI
- **SKILL.md 生成**：Agent 可自动发现和安装所需工具
- **多平台支持**：Claude Code、Pi、OpenCode、Codex、Copilot CLI 等

---

## 技术架构与特点

| 特性 | 说明 |
|------|------|
| 真实软件集成 | 直接调用 Blender bpy、LibreOffice headless、FFmpeg 等真实后端 |
| 双模式交互 | 状态 REPL 交互 + 子命令脚本 |
| Agent 原生设计 | `--json` 结构化输出，`--help` 自动发现 |
| 零配置安装 | `pip install -e .` 即可使用 |
| 统一 REPL | ReplSkin 提供一致的交互体验 |
| 命名空间 | `cli_anything.*` 避免冲突 |

---

## 已覆盖软件（37+）

| 类别 | 软件 | 测试数 |
|------|------|--------|
| 创意与媒体 | GIMP, Blender, Inkscape, Krita, Audacity, Kdenlive, Shotcut, OBS Studio | 1,301 |
| 办公与文档 | LibreOffice, Draw.io, Mermaid, MuseScore | 362 |
| AI/ML | ComfyUI, Ollama, AnyGen, NotebookLM | 239 |
| 开发工具 | iTerm2, LLDB, RenderDoc, Nsight Graphics, Unreal Insights | 326 |
| 游戏开发 | Godot Engine, s&box, Slay the Spire II | 268 |
| 科学计算 | FreeCAD, QGIS, CloudCompare, Uni-Mol Tools | 203 |
| 自动化/网络 | n8n, Dify, AdGuard, WireMock, PM2 | 112+ |
| **总计** | **37+ 应用** | **2,280+ (100% 通过)** |

---

## 应用场景

- **Agent 驱动自动化**：AI Agent 直接操作 Blender 3D 建模、LibreOffice 文档生成、OBS 直播控制
- **企业工具链统一**：一个 CLI 封装 Mailchimp + Zoom + n8n，Agent 无需逐个调 API
- **科研工程加速**：Agent 自主完成 FreeCAD 建模 → QGIS 地图分析 → 可视化全流程
- **游戏开发**：Agent 通过 CLI 自动生成 Godot 游戏场景

---

## 为什么火？Trending 原因

1. **切中 2026 最大风口** — Agent-Native 是年度最热话题，CLI vs MCP 大辩论中 CLI-Anything 是旗舰项目
2. **学术 + 实战双验证** — 香港大学出品，arXiv 论文支撑，37 个真实软件 + 2,280 测试 + 100% 通过率
3. **极低入门门槛** — `/cli-anything ./gimp` 一条命令即生成完整 CLI
4. **活跃社区** — 35k Stars、3.5k Forks、636 Commits，SkillTrust 评分 92
5. **Token 效率** — CLI 方式比 MCP 节省 4-32 倍 Token，直击开发者痛点

---

## 同类项目对比

| 维度 | CLI-Anything | MCP | OpenAI Function Calling |
|------|-------------|-----|------------------------|
| 理念 | 自动生成 CLI 控制软件 | 标准化 Agent 通信协议 | 模型内嵌函数调用 |
| Token 消耗 | **最低** | 高（4-32x） | 中等 |
| 覆盖范围 | **任何有源码的软件** | 需要 MCP Server | 仅 OpenAI 生态 |
| 行业支持 | 新兴社区 | OpenAI/Google/MS | OpenAI |
| 可靠性 | **CLI 确定性执行** | 依赖 Server 状态 | 依赖 API |
| 学习成本 | **极低（一条命令）** | 需理解协议 | 需定义 Schema |
| 测试标准 | **2,280+ / 100%** | 无统一标准 | 无统一标准 |

---

## 适合谁使用

- AI Agent 开发者（扩展 Agent 工具能力）
- Claude Code / Copilot 重度用户
- DevOps 工程师（自动化复杂软件工作流）
- 开源贡献者（为喜欢的软件构建 Agent CLI）
- 科研人员（Agent 自动化科研工具链）
- 内容创作者（Agent 辅助 3D/视频/音频制作）

---

## 快速上手

```bash
# 1. 安装插件（Claude Code）
/plugin marketplace add HKUDS/CLI-Anything
/plugin install cli-anything

# 2. 生成 CLI
/cli-anything ./gimp

# 3. 安装使用
cd gimp/agent-harness && pip install -e .
cli-anything-gimp --help
cli-anything-gimp --json project new --width 1920 --height 1080

# 4. 迭代优化
/cli-anything:refine ./gimp "batch processing and filters"
```

---

## 综合评分

| 维度 | 分数 | 说明 |
|------|------|------|
| 创新性 | **9.0/10** | 首创 Agent-Native Software 概念，7 阶段流水线独创 |
| 代码质量 | **9.5/10** | 2,280+ 测试，100% 通过，统一架构设计 |
| 实用性 | **9.2/10** | 37+ 真实软件覆盖，一条命令即用 |
| 文档完善度 | **8.8/10** | 多语言 README，HARNESS.md 专业方法论 |
| 社区活跃度 | **9.3/10** | 35k Stars，活跃贡献，SkillTrust 92 分 |

### **综合评分：9.2 / 10 — S 级项目**

> Agent-Native 时代的基石工具。如果你在构建 AI Agent 应用，CLI-Anything 是 2026 年必须了解的项目。

---

*分析日期：2026-05-18 | AI 自动生成*
