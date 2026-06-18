# zai-org/GLM-5 深度分析摘要

> **"From Vibe Coding to Agentic Engineering"** —— 智谱 Z.ai 面向复杂系统工程与长程 Agent 任务的开源旗舰大模型
> 📅 分析日期：2026-06-19

## 📌 一句话定位
GLM-5（含 5.1 / 5.2）是智谱 AI（Z.ai / 清华系 THUDM）的下一代开源旗舰基座模型，用 **MoE + DeepSeek 稀疏注意力 + 自研 slime 异步 RL**，在**真实工业级编码**与**长程 Agent 任务**上达到开源 SOTA 并逼近/反超顶级闭源模型，叠加 **MIT 开源、1M 上下文与国产芯片 Day-0 适配**，是国内"模型能力 + 自主可控 + 工程落地"三者兼得的标杆。

## 🔑 核心事实速览
| 维度 | 详情 |
|---|---|
| **架构** | 稀疏混合专家 MoE，**744B 总参 / ~40B 单 Token 激活**（256 专家，激活率 ~5.9%） |
| **注意力** | **DeepSeek Sparse Attention (DSA)**，~90% 稀疏，长序列注意力计算量砍半 |
| **预训练数据** | **28.5T tokens**（较 GLM-4.5 的 23T 扩充） |
| **上下文** | 基础 200K；**GLM-5.2 提供可用 1M 上下文** |
| **后训练** | 自研开源 **slime 异步 RL 基础设施**，支撑长程 Agent 持续优化 |
| **版本线** | GLM-5（2026 初）→ **GLM-5.1**（2026-04，Agentic）→ **GLM-5.2**（2026-06-14，1M 上下文） |
| **开源协议** | **MIT**（5.x 系列，商用友好） |
| **权重** | Hugging Face（BF16/FP8）· ModelScope |
| **推理框架** | vLLM（v0.19+，含 vLLM-Ascend）· SGLang（v0.5.10+）· xLLM · KTransformers |
| **国产芯片** | 华为昇腾 / 摩尔线程 / 寒武纪 等 **七大平台 Day-0 适配**（FlagOS 跨芯） |

## 🏆 关键评测成绩
- **SWE-Bench Pro（真实工业级代码修复）**：GLM-5.1 **58.4% 榜首**，超越 GPT-5.4（57.7%）、Claude Opus 4.6（57.3%）
- **NL2Repo（从需求生成完整仓库）**：GLM-5.1 **42.7%**，领先 Claude 的 33.4%
- **SWE-Bench Verified**：GLM-5 ~72.8%（Claude Fable 5 ~95% 仍居首）
- **Vending Bench 2（模拟经营一年长程任务）**：GLM-5 开源第一，$4432 余额，逼近 Claude Opus 4.5

## 💡 核心创新点
1. **"跑得越久越好"的 Agent**：GLM-5.1 在数百轮、上千次工具调用中持续优化，突破模型"用尽套路即停滞"的瓶颈
2. **MoE + DSA 的"大而省"**：旗舰容量 / 中等算力，长序列部署成本**降约 50%**
3. **slime 异步 RL**：开源的高吞吐 RL 训练栈，让长程 Agent 后训练可规模化迭代
4. **1M 可用上下文**：可承载项目级代码库，一次任务覆盖完整工程
5. **国产算力 Day-0 适配**：自主可控，金融/政务/央国企私有化首选
6. **真实工业级编码 SOTA**：在非合成基准上登顶开源

## 🎯 应用场景
自主编码 Agent 后端 · 复杂系统工程（前后端/终端）· 长程自主任务（数小时自主运行）· 深度推理与数学 · 超长文档/代码库理解 · 私有化合规部署 · 工具调用与多智能体编排

## ⚔️ 竞品对比（要点）
- **vs Claude (Fable/Opus)**：Claude 综合榜单（SWE-Bench Verified）仍领先、闭源体验最稳；**GLM-5 在真实工业编码(SWE-Bench Pro/NL2Repo) 反超**，且开源 + 自主可控
- **vs GPT-5.x**：闭源、价格高、无国产芯片；GLM-5.1 在 SWE-Bench Pro 反超 GPT-5.4
- **vs DeepSeek V4**：最直接开源对手（同为 MoE + 1M 上下文 + 国产适配），工程落地与成本高度竞争

## 🛠️ 部署建议
- **偶发/中小团队**：API 优先（Z.ai 开放平台限时免费 / OpenRouter）
- **有合规/长程 Agent/规模化需求**：自托管 FP8 + 国产芯片，兼顾可控与成本
- **硬件门槛**：全精度需 8× H200（~1.1TB 显存 + 800GB NVMe）；社区有 4-bit（4× H100）、1-bit/2-bit（~180GB / Mac Studio）量化方案

## ⭐ 综合评分：**9.0 / 10**
| 维度 | 分数 |
|---|---|
| 模型能力（推理/编码/Agent） | 9.4 |
| 技术创新（MoE+DSA+slime RL） | 9.3 |
| 开源与开放性 | 9.5 |
| 工程落地（多框架+国产芯片） | 9.2 |
| 社区与生态热度 | 8.2 |
| 成本与可及性 | 8.6 |
| 自主可控 / 合规 | 9.0 |

> **结论**：开源大模型的"旗舰 + 攻坚手"。**国内自主可控与企业 Agent 落地的首选开源基座之一**，唯一明显短板是全精度自托管门槛高、综合榜单仍略逊于 Claude Fable 5。

## 🔗 相关链接
- 仓库：https://github.com/zai-org/GLM-5
- 权重：https://huggingface.co/zai-org/GLM-5
- 技术报告：https://arxiv.org/abs/2602.15763
- RL 框架 slime：https://github.com/THUDM/slime
- 官方文档：https://docs.bigmodel.cn/cn/guide/models/text/glm-5
