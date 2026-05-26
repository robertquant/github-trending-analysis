# Anthropic-Cybersecurity-Skills 深度分析

> **754 个结构化网络安全技能，让 AI 代理拥有资深安全分析师的能力**

| 基本信息 | 详情 |
|----------|------|
| **仓库** | [mukul975/Anthropic-Cybersecurity-Skills](https://github.com/mukul975/Anthropic-Cybersecurity-Skills) |
| **Stars** | 6,700+ |
| **技能数** | 754 |
| **安全领域** | 26 个 |
| **框架映射** | MITRE ATT&CK, NIST CSF 2.0, MITRE ATLAS, D3FEND, NIST AI RMF |
| **标准** | agentskills.io |
| **许可证** | Apache 2.0 |
| **语言** | Python |

---

## 项目简介与核心功能

Anthropic-Cybersecurity-Skills 是一个为 AI 代理（Claude Code、GitHub Copilot、Codex CLI、Cursor 等）设计的**结构化网络安全技能库**。它不是一堆安全脚本或检查清单，而是一套 AI 原生的知识库，遵循 agentskills.io 开放标准。

### 核心功能

- **754 个结构化技能**：覆盖 26 个安全领域，从云安全到勒索软件防御
- **五框架映射**：每个技能同时映射 MITRE ATT&CK、NIST CSF 2.0、MITRE ATLAS、D3FEND、NIST AI RMF
- **渐进式披露架构**：每个技能仅 ~30 tokens 扫描元数据，完整加载 500-2000 tokens
- **20+ 平台兼容**：Claude Code、Copilot、Cursor、Gemini CLI、LangChain 等开箱即用
- **ATT&CK 全覆盖**：14 个战术全覆盖，200+ 技术映射

---

## 技术架构与特点

### 技能结构（YAML + Markdown）

```
skills/performing-memory-forensics-with-volatility3/
├── SKILL.md              # YAML 前置元数据 + Markdown 工作流
├── references/
│   ├── standards.md      # 框架映射 (ATT&CK, ATLAS, D3FEND, NIST)
│   └── workflows.md      # 深度技术流程参考
├── scripts/
│   └── process.py        # 可执行的辅助脚本
└── assets/
    └── template.md       # 报告模板和检查清单
```

### YAML 前置元数据示例

```yaml
name: performing-memory-forensics-with-volatility3
description: >-
  Analyze memory dumps to extract running processes, network connections,
  injected code, and malware artifacts using the Volatility3 framework.
domain: cybersecurity
subdomain: digital-forensics
tags: [forensics, memory-analysis, volatility3, incident-response, dfir]
atlas_techniques: [AML.T0047]
d3fend_techniques: [D3-MA, D3-PSMD]
nist_ai_rmf: [MEASURE-2.6]
nist_csf: [DE.CM-01, RS.AN-03]
```

### 关键架构特点

- **Token 经济设计**：元数据扫描仅 ~30 tokens，AI 代理可一次扫描全部 754 个技能
- **结构化决策工作流**：每个技能包含 When to Use → Prerequisites → Workflow → Verification 完整链路
- **跨框架互操作**：一个技能同时满足 5 大安全框架的合规要求
- **agentskills.io 标准**：遵循开放标准，确保跨平台兼容性

### 五框架映射覆盖

| 框架 | 版本 | 覆盖范围 |
|------|------|----------|
| MITRE ATT&CK | v18 | 14 战术 · 200+ 技术 |
| NIST CSF 2.0 | 2.0 | 6 功能 · 22 类别 · 106 子类别 |
| MITRE ATLAS | v5.4 | 16 战术 · 84 技术 |
| MITRE D3FEND | v1.3 | 7 类别 · 267 技术 |
| NIST AI RMF | 1.0 | 4 功能 · 72 子类别 |

---

## 应用场景

| 场景 | 技能示例 | 价值 |
|------|----------|------|
| 安全运营中心 (SOC) | SIEM 关联分析、告警分诊、事件升级 | 将告警处理效率提升 10x |
| 威胁狩猎 | 假设驱动狩猎、LOTL 检测、行为分析 | 从被动响应转向主动防御 |
| 数字取证与事件响应 | 内存取证、磁盘取证、时间线重建 | 标准化取证工作流 |
| 云安全审计 | AWS/Azure/GCP 加固、CSPM、云取证 | 多云环境统一安全覆盖 |
| 渗透测试 | 网络/Web/云/移动/无线渗透 | 标准化攻击路径模拟 |
| 恶意软件分析 | 静态/动态分析、逆向工程、沙箱 | 自动化恶意样本分类 |
| 合规与治理 | CIS 基准、SOC 2、法规框架 | 自动化合规检查映射 |
| AI 安全防御 | ATLAS 威胁映射、AI RMF 风险管理 | 保护 ML 管道和 AI 系统 |

---

## 为什么火（Trending 原因分析）

1. **网络安全人才缺口巨大**：ISC2 报告 2024 年全球有 480 万网络安全岗位空缺，AI 代理可部分填补这一空白
2. **AI Agent 生态爆发**：Claude Code、Copilot、Cursor 等 AI 编程工具爆发式增长，对专业化技能需求强烈
3. **五框架映射独一无二**：唯一将技能同时映射 5 大安全框架的开源项目，一个技能满足多重合规需求
4. **社区驱动快速成长**：从 611 个技能快速增长到 754 个，被多个 Awesome List 收录，社交传播广泛
5. **被 Anthropic 红队相关生态带动**：Claude Mythos 等安全能力发布提升了整体关注度

---

## 同类项目对比

| 项目 | 技能数 | 框架映射 | 标准 | 特点 |
|------|--------|----------|------|------|
| **Anthropic-Cybersecurity-Skills** | **754** | **ATT&CK + NIST CSF + ATLAS + D3FEND + AI RMF** | **agentskills.io** | **最全面的安全技能库，五框架映射** |
| anthropics/skills | ~50 | 无 | agentskills.io | Anthropic 官方通用技能，覆盖面窄 |
| VoltAgent/awesome-agent-skills | 1000+ | 无 | 索引 | 优秀列表，但非结构化技能 |
| addyosmani/agent-skills | ~30 | 无 | agentskills.io | 前端/通用开发技能，非安全领域 |
| Security Wordlists/Scripts | varies | 无 | 无 | 提供工具/字典，非结构化决策流 |

**核心优势**：这是目前唯一将每个技能同时映射到 5 大安全框架的开源项目。

---

## 适合谁使用

| 用户群体 | 使用方式 | 价值 |
|----------|----------|------|
| 安全分析师 / SOC 团队 | 配合 Claude Code / Copilot 自动化安全分析 | 获得资深分析师级别的工作流指引 |
| 渗透测试工程师 | 使用渗透测试技能标准化攻击路径 | 确保测试覆盖全面，减少遗漏 |
| 安全工具开发者 | 集成技能到安全自动化平台 | 快速增加安全能力覆盖面 |
| 合规与审计团队 | 利用五框架映射进行合规检查 | 一次操作满足多重合规要求 |
| AI/ML 工程师 | 利用 ATLAS/AI RMF 映射保护 AI 系统 | 专门覆盖 AI 对抗威胁 |
| 安全学习者 | 将技能作为系统化学习路径 | 从真实工作流而非理论文档学习 |

---

## 快速上手指南

### 1. 安装技能库

```bash
# 方法 1：npx（推荐）
npx skills add mukul975/Anthropic-Cybersecurity-Skills

# 方法 2：Git clone
git clone https://github.com/mukul975/Anthropic-Cybersecurity-Skills.git
cd Anthropic-Cybersecurity-Skills
```

### 2. 在 Claude Code 中使用

```
# 克隆后，直接在 Claude Code 中打开项目目录
# AI 代理会自动扫描 SKILL.md 的 YAML 元数据
# 根据你的提问自动匹配最相关的技能

# 示例：分析内存转储
User: 分析这个内存转储中的凭据窃取痕迹
Agent: # 自动加载 performing-memory-forensics-with-volatility3
       # 自动加载 hunting-for-credential-dumping-lsass
       # 按 Workflow 步骤执行 Volatility3 插件
```

### 3. 在其他平台使用

兼容 GitHub Copilot、Codex CLI、Cursor、Gemini CLI、Windsurf、Cline、Aider 等 20+ 平台，无需额外配置。

### 4. 贡献新技能

```bash
# 按照 CONTRIBUTING.md 中的模板创建新技能
# 提交 PR，标题格式：Add skill: your-skill-name
# 48 小时内完成技术审查

# 优先需要贡献的领域：
# - Deception Technology（仅 2 个技能）
# - Compliance & Governance（仅 5 个技能）
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | ⭐ 9.0/10 | 首次将 AI 代理技能与五大安全框架统一映射，token 经济的渐进式披露设计极具前瞻性 |
| **代码质量** | ⭐ 8.5/10 | YAML+Markdown 结构清晰规范，内容结构一致性强 |
| **实用性** | ⭐ 9.5/10 | 直击网络安全人才缺口痛点，20+ 平台即插即用 |
| **文档完善度** | ⭐ 8.8/10 | README 极为详尽，包含框架对比、覆盖率分析、使用示例、贡献指南 |
| **社区活跃度** | ⭐ 8.8/10 | 6.7K+ Stars 快速增长，被多个 Awesome List 收录，PR 审查及时 |

### 综合评分：⭐ 8.9 / 10 — 强烈推荐

> AI 安全领域的里程碑项目，将网络安全专业知识以 AI 原生的方式结构化呈现，填补了「AI 代理 + 网络安全」的关键空白。对安全从业者、AI 工程师和合规团队都有极高的实用价值。

---

*分析日期：2026-05-26 | 由 AI 深度分析生成 | Powered by Claude Code*