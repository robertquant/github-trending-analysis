# NVlabs/Sana - 高效高分辨率图像合成框架

> **SANA: Efficient High-Resolution Image Synthesis with Linear Diffusion Transformer**

![Stars](https://img.shields.io/badge/Stars-6,469-yellow) ![Today](https://img.shields.io/badge/Today%20Stars-+376-orange) ![Language](https://img.shields.io/badge/Language-Python-blue) ![License](https://img.shields.io/badge/License-Apache%202.0-green)

---

## 项目简介

**SANA** 是由 NVIDIA Labs (NVlabs) 开发的面向效率的高分辨率图像与视频生成框架。它基于 **线性扩散变换器 (Linear Diffusion Transformer)** 架构，能在消费级 GPU 上实现高达 **4096×4096** 分辨率的文本到图像生成，同时保持极快的推理速度。

SANA 已发展为一个完整的生态系统，包含多个子项目：

| 子项目 | 功能 |
|---|---|
| **SANA** | 基础文本到图像生成，支持最高 4K 分辨率 |
| **SANA-1.5** | 高效训练/推理时间计算扩展，质量更优 |
| **SANA-Sprint** | 单/少步生成，H100 上 0.1s 生成 1024px 图像 |
| **SANA-Video** | 高效视频生成，Block Linear Attention |
| **SANA-WM** | 2.6B 可控世界模型，720p 1分钟视频 + 6-DoF 相机控制 |
| **Sol-RL** | NVFP4 推理 + BF16 训练 RL，收敛速度提升 4.64× |

---

## 核心技术架构

### 1. 线性注意力 (Linear Attention)
替代 DiT 中的标准注意力机制，在高分辨率下实现线性复杂度，大幅降低计算开销。

### 2. DC-AE (深度压缩自编码器)
实现 **32× 图像压缩**（传统方法仅 8×），将潜在 token 数量减少至原来的 1/4。

### 3. Decoder-only 文本编码器
使用现代 Decoder-only LLM 替代传统文本编码器，利用上下文学习能力提升文本-图像对齐度。

### 4. Flow-DPM-Solver
减少采样步骤的高效训练和采样方法。

### 5. sCM 蒸馏
通过连续时间一致性蒸馏实现单步/少步生成。

### 6. Block Causal Linear Attention & Causal Mix-FFN
专为长视频生成设计的高效注意力和前馈网络。

---

## 性能表现

### 图像生成 (1024×1024)

| 方法 | 吞吐量 (samples/s) | 延迟 (s) | 参数量 (B) | 加速比 | FID↓ | CLIP↑ | GenEval↑ | DPG↑ |
|---|---|---|---|---|---|---|---|---|
| FLUX-dev | 0.04 | 23.0 | 12.0 | 1.0× | 10.15 | 27.47 | 0.67 | 84.0 |
| **Sana-0.6B** | 1.7 | 0.9 | 0.6 | 39.5× | 5.81 | 28.36 | 0.64 | 83.6 |
| **Sana-1.6B** | 1.0 | 1.2 | 1.6 | 23.3× | 5.92 | 28.94 | 0.69 | 84.5 |
| **Sana-1.5 1.6B** | 1.0 | 1.2 | 1.6 | 23.3× | 5.70 | 29.12 | **0.82** | 84.5 |
| **Sana-1.5 4.8B** | 0.26 | 4.2 | 4.8 | 6.5× | 5.99 | **29.23** | 0.81 | **84.7** |

### 视频生成 (VBench 720p)

| 模型 | 延迟 (s) | 参数量 (B) | VBench Total↑ | Quality↑ | Semantic↑ |
|---|---|---|---|---|---|
| Wan-2.1-14B | 1897 | 14 | 83.73 | 85.77 | 75.58 |
| Wan-2.1-1.3B | 400 | 1.3 | 83.38 | 85.67 | 74.22 |
| **SANA-Video-2B** | **36** | **2** | **84.05** | 84.63 | **81.73** |

---

## 为什么火 (Trending 原因)

1. **NVIDIA 官方出品**：来自 NVIDIA Labs 的顶级研究团队，技术背书极强
2. **顶会认可**：ICLR 2025 Oral、ICML 2025、ICCV 2025 Highlight、ICLR 2026 Oral，学术界高度认可
3. **极致效率**：比 Flux-12B 快 100 倍、小 20 倍，却保持同等质量
4. **消费级硬件友好**：4-bit 量化后仅需 <8GB VRAM，笔记本即可运行
5. **全栈生态**：从图像到视频，从训练到推理，从 0.6B 到 4.8B，覆盖完整
6. **完全开源**：Apache 2.0 许可，训练代码、推理代码、模型权重全部开放
7. **快速迭代**：从 SANA 到 1.5、Sprint、Video、WM、Sol-RL，持续演进
8. **广泛集成**：已集成 diffusers、ComfyUI、SGLang 等主流生态

---

## 同类项目对比

| 特性 | SANA | Flux (Black Forest Labs) | Stable Diffusion 3.5 | DALL-E 3 |
|---|---|---|---|---|
| **最大分辨率** | 4096×4096 | ~2048 | ~1024 | 1024 |
| **参数量** | 0.6B - 4.8B | 12B | 2B-8B | ~20B(估计) |
| **开源程度** | 完全开源 | 部分开源 | 完全开源 | 闭源 |
| **推理速度** | 极快 (线性注意力) | 中等 | 中等 | 慢(API调用) |
| **VRAM 需求** | 最低 8GB (4bit) | 12GB+ | 6GB+ | N/A(云端) |
| **许可证** | Apache 2.0 | FLUX.1-schnell: Apache | Stability AI | 闭源 |
| **视频生成** | 支持 | 有限 | 不支持 | 不支持 |

---

## 应用场景

- **创意设计**：高分辨率 AI 艺术创作、概念设计
- **内容生产**：电商产品图、营销素材批量生成
- **游戏开发**：角色设计、场景生成、纹理制作
- **视频制作**：文本到视频、可控世界模型
- **研究实验**：扩散模型训练与微调、RL 后训练
- **移动端部署**：量化后可在笔记本/边缘设备运行

---

## 适合谁使用

| 用户群体 | 推荐理由 |
|---|---|
| AI 研究人员 | 完整训练管线，可复现，顶会论文 |
| 创意工作者 | 高分辨率快速出图，ComfyUI 集成 |
| 游戏开发者 | 4K 纹理/场景生成 |
| 独立开发者 | 低 VRAM 需求，API 友好 (SGLang) |
| 企业用户 | Apache 2.0 商用友好 |
| 学生/爱好者 | 免费开源，文档完善，社区活跃 |

---

## 快速上手

### 安装

```bash
git clone https://github.com/NVlabs/Sana.git
cd Sana && ./environment_setup.sh sana
```

### 推理 (diffusers)

```python
import torch
from diffusers import SanaPipeline

pipe = SanaPipeline.from_pretrained(
    "Efficient-Large-Model/SANA1.5_1.6B_1024px_diffusers",
    torch_dtype=torch.bfloat16,
)
pipe.to("cuda")

prompt = 'a cyberpunk cat with a neon sign that says "Sana"'
image = pipe(
    prompt=prompt,
    height=1024,
    width=1024,
    guidance_scale=4.5,
    num_inference_steps=20,
    generator=torch.Generator(device="cuda").manual_seed(42),
)[0]

image[0].save("sana.png")
```

### 4-bit 量化 (低 VRAM)

只需 8GB GPU 即可运行 Sana 4K 模型。

---

## 综合评分

| 维度 | 评分 (满分 10) | 说明 |
|---|---|---|
| **创新性** | 9.5/10 | 线性注意力 + 32× 压缩 + 多个子项目创新 |
| **代码质量** | 9.0/10 | NVIDIA 团队出品，工程化程度极高 |
| **实用性** | 9.5/10 | 完整训练推理管线，消费级硬件可运行 |
| **文档完善度** | 9.0/10 | 详尽文档、教程、ComfyUI/SGlang 集成指南 |
| **社区活跃度** | 9.0/10 | 高频更新，Discord 活跃，贡献者众多 |

**综合评分：9.2/10** — 顶级开源 AI 图像/视频生成框架，效率与质量的完美平衡

---

## 相关链接

- GitHub: https://github.com/NVlabs/Sana
- 项目主页: https://nvlabs.github.io/Sana/
- 论文: https://arxiv.org/abs/2410.10629
- SANA-1.5 论文: https://arxiv.org/abs/2501.18427
- HuggingFace 模型: https://huggingface.co/Efficient-Large-Model
- Discord: 见 GitHub README

---

*分析日期: 2025-05-19 | 数据来源: GitHub、arXiv、社区评测*
