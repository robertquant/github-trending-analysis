# Kronos: 金融市场"语言"的基础模型

> **shiyu-coder/Kronos** — 全球首个专为K线（蜡烛图）设计的开源金融基础模型

| 维度 | 信息 |
|------|------|
| 项目地址 | [github.com/shiyu-coder/Kronos](https://github.com/shiyu-coder/Kronos) |
| 论文 | AAAI 2026 (arXiv:2508.02739) |
| License | MIT |
| Stars | 25,000+ |
| 语言 | Python / PyTorch |
| 模型托管 | Hugging Face (NeoQuasar) |

---

## 项目简介

**Kronos** 是一个 decoder-only 基础模型家族，专门针对金融市场的"语言"——K线序列进行预训练。与通用时间序列基础模型不同，Kronos 专为处理金融数据独有的高噪声特性而设计，基于**45+全球交易所**的**120亿条K线记录**进行训练。

核心创新点：采用**两阶段框架**——先用专门的 tokenizer 将连续的多维K线数据（OHLCV）量化为**层次化离散 token**，再用大型自回归 Transformer 对这些 token 进行预训练，使其成为适用于多种量化任务的统一模型。

## 技术架构与特点

### 两阶段预训练框架
1. **Kronos-Tokenizer**：将连续 OHLCV 数据量化为层次化离散 token，捕捉K线数据的局部模式与全局趋势
2. **自回归 Transformer**：在大规模 token 序列上进行预训练，学习金融市场的"语法"和"语义"

### 模型家族

| 模型 | Tokenizer | 上下文长度 | 参数量 | 开源 |
|------|-----------|-----------|--------|------|
| Kronos-mini | Kronos-Tokenizer-2k | 2048 | 4.1M | ✅ |
| Kronos-small | Kronos-Tokenizer-base | 512 | 24.7M | ✅ |
| Kronos-base | Kronos-Tokenizer-base | 512 | 102.3M | ✅ |
| Kronos-large | Kronos-Tokenizer-base | 512 | 499.2M | ❌ |

### 关键技术特性
- **概率预测**：支持温度采样（Temperature）和核采样（Top-p），可生成多条预测路径取均值
- **批量推理**：`predict_batch` 方法支持多资产并行预测
- **微调管线**：完整的 tokenizer + predictor 微调流程，支持多 GPU 训练（torchrun）
- **Qlib 集成**：提供中国 A 股市场微调示例，含回测评估

## 应用场景

1. **价格预测**：基于历史K线数据预测未来价格走势（开高低收）
2. **量化交易**：生成交易信号，辅助策略构建
3. **市场分析**：理解市场模式，进行多市场跨资产分析
4. **风险管理**：通过概率预测评估不确定性
5. **学术研究**：金融时间序列建模、基础模型研究

## 为什么火（Trending 原因）

1. **首创性**：全球首个针对K线的开源金融基础模型，填补了空白
2. **AAAI 2026 录用**：顶会背书，学术权威性强
3. **"GPT 读蜡烛图"概念**：将金融市场比作"语言"，概念新颖，极具传播力
4. **120亿条数据训练**：数据规模惊人，覆盖45+全球交易所
5. **93% 精度优势宣称**：相比竞品的显著性能提升引发关注
6. **完整开发生态**：从预测到微调到回测的全流程工具链
7. **实时 Demo**：提供 BTC/USDT 24小时预测在线演示，直观感受效果
8. **清华背景**：作者来自清华大学，增加可信度

## 同类项目对比

| 项目 | 定位 | 数据类型 | 优势 | 劣势 |
|------|------|---------|------|------|
| **Kronos** | 金融K线专用 | OHLCV K线 | 金融专精，性能领先 | 仅限K线格式 |
| **Chronos (Amazon)** | 通用时间序列 | 任意连续值 | 通用性强，周数据表现好 | 非金融专精 |
| **TimesFM (Google)** | 通用时间序列 | 任意连续值 | 零样本能力强，月数据优 | 不擅长高频金融 |
| **MOIRAI (Salesforce)** | 通用多变量 | 多变量时序 | 多变量支持好 | 金融场景非最优 |
| **TabPFN** | 表格数据 | 表格特征 | 小样本极强 | 非时序专精 |
| **FinceptTerminal** | 金融终端 | 多源数据 | 综合金融工具 | 非基础模型 |

**Kronos 的核心差异化**：100% 金融数据训练 + 层次化 token 编码，使其在金融场景下显著优于通用时间序列模型。

## 适合谁使用

| 用户类型 | 适合度 | 用途 |
|----------|--------|------|
| 量化交易研究员 | ⭐⭐⭐⭐⭐ | 策略开发、信号生成、回测验证 |
| 金融 AI 研究者 | ⭐⭐⭐⭐⭐ | 论文复现、模型改进、基准对比 |
| 个人投资者（技术型） | ⭐⭐⭐⭐ | 辅助分析、趋势判断 |
| 金融工程学生 | ⭐⭐⭐⭐ | 学习金融AI、课程项目 |
| 传统交易员（非技术） | ⭐⭐ | 上手门槛高，需编程基础 |

## 快速上手指南

### 安装

```bash
git clone https://github.com/shiyu-coder/Kronos.git
cd Kronos
pip install -r requirements.txt
```

### 5行代码预测

```python
from model import Kronos, KronosTokenizer, KronosPredictor
import pandas as pd

tokenizer = KronosTokenizer.from_pretrained("NeoQuasar/Kronos-Tokenizer-base")
model = Kronos.from_pretrained("NeoQuasar/Kronos-small")
predictor = KronosPredictor(model, tokenizer, max_context=512)

df = pd.read_csv("your_kline_data.csv")
pred_df = predictor.predict(
    df=df[['open','high','low','close','volume','amount']],
    x_timestamp=df['timestamps'],
    y_timestamp=future_timestamps,
    pred_len=120, T=1.0, top_p=0.9, sample_count=1
)
```

### 微调自己的数据

```bash
# 1. 准备数据集
python finetune/qlib_data_preprocess.py

# 2. 微调 Tokenizer
torchrun --standalone --nproc_per_node=2 finetune/train_tokenizer.py

# 3. 微调 Predictor
torchrun --standalone --nproc_per_node=2 finetune/train_predictor.py

# 4. 回测评估
python finetune/qlib_test.py --device cuda:0
```

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | ⭐⭐⭐⭐⭐ (9.5/10) | 首创K线 token 化 + 金融基础模型，概念突破性强 |
| **代码质量** | ⭐⭐⭐⭐ (8.5/10) | 架构清晰，接口设计优雅，含完整示例 |
| **实用性** | ⭐⭐⭐⭐ (8.0/10) | 预测即用，微调完善，但需注意交易成本建模 |
| **文档完善度** | ⭐⭐⭐⭐⭐ (9.0/10) | README 详尽，含端到端示例，论文可获取 |
| **社区活跃度** | ⭐⭐⭐⭐⭐ (9.0/10) | 25K+ Stars，AAAI顶会，持续更新 |
| **综合** | ⭐⭐⭐⭐⭐ (8.8/10) | 金融AI领域的里程碑级开源项目 |

## 注意事项

- 项目明确声明：微调示例仅为演示，**非生产级量化系统**
- 真实交易需要组合优化、风险因子中性化等更复杂技术
- 模型生成的是原始信号，需后处理才能获得"纯 Alpha"
- 回测应仔细建模交易成本、滑点和市场冲击

---

*分析日期：2026-05-26 | 数据来源：GitHub、arXiv、AAAI、技术博客*
