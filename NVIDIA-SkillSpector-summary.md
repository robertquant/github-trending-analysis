# NVIDIA/SkillSpector 深度分析摘要

## 基本信息
- **项目**: NVIDIA/SkillSpector
- **定位**: AI Agent Skills 安全扫描器
- **语言**: Python 3.12+
- **许可证**: Apache 2.0
- **Stars**: ~2.1k
- **日期**: 2026-06-12

## 项目概述
SkillSpector 是 NVIDIA 开发的开源安全扫描器，专为 AI Agent Skills（技能插件）设计。它帮助开发者和企业在安装 Agent 技能之前检测安全漏洞、恶意模式和安全风险。

基于研究数据：**26.1% 的技能存在漏洞，5.2% 具有恶意意图**（来自对 42,447 个技能的大规模实证研究）。

## 技术架构
- 基于 **LangGraph 工作流**构建
- **两阶段检测管线**：
  - Stage 1：快速静态分析（正则匹配 + AST 分析 + YARA 签名 + 污点追踪）
  - Stage 2：LLM 语义分析（可选，精确率提升至 ~87%）
- 支持多种 LLM Provider：OpenAI、Anthropic、NVIDIA Build、本地模型（Ollama/vLLM）

## 16 大检测类别 / 64 种模式
Prompt 注入 | 数据外泄 | 权限提升 | 供应链安全 | 过度授权 | 输出处理 | 系统提示泄露 | 记忆投毒 | 工具滥用 | 恶意代理 | 触发器滥用 | 行为 AST | 污点追踪 | YARA 签名 | MCP 最小权限 | MCP 工具投毒

## 核心创新
1. **首个** AI Agent Skills 专业安全扫描器
2. 两阶段混合检测管线（静态 + LLM 语义）
3. 独有的 MCP 协议安全检测（Unicode 欺骗、工具投毒）
4. 实时 OSV.dev CVE 查询
5. NVIDIA Verified Agent Skills 生态核心组件

## 竞品对比
| 特性 | SkillSpector | VirusTotal | 通用静态分析 | 其他 AI 扫描器 |
|------|:-----------:|:----------:|:----------:|:------------:|
| Agent Skills 专项 | ✅ | ❌ | ❌ | ✅ |
| Prompt 注入检测 | ✅ | ❌ | ❌ | ⚠️ |
| MCP 工具投毒 | ✅ | ❌ | ❌ | ❌ |
| LLM 语义分析 | ✅ | ❌ | ❌ | ⚠️ |
| 实时 CVE 查询 | ✅ | ❌ | ⚠️ | ❌ |
| 开源免费 | ✅ | ❌ | ⚠️ | ⚠️ |

## 综合评分: 9.0 / 10
- 技术创新性: 9.5
- 实用价值: 9.0
- 工程质量: 9.0
- 生态完整性: 8.5
- 社区活跃度: 8.5
- 文档完善度: 9.5

## 链接
- [GitHub 仓库](https://github.com/NVIDIA/SkillSpector)
- [官方文档](https://docs.nvidia.com/skills/scanning-agent-skills)
- [NVIDIA Blog](https://developer.nvidia.com/blog/nvidia-verified-agent-skills-provide-capability-governance-for-ai-agents/)
- [arXiv 论文](https://arxiv.org/html/2606.01494v1)
