# FinceptTerminal - 开源金融终端

> **GitHub**: [Fincept-Corporation/FinceptTerminal](https://github.com/Fincept-Corporation/FinceptTerminal)
> **分析日期**: 2026-05-23
> **当前版本**: v4.0.3
> **许可证**: AGPL-3.0 + 商业许可（双重授权）

---

## 项目简介

**FinceptTerminal** 是一个开源的专业级金融分析平台，定位为 **Bloomberg Terminal 的免费替代品**（Bloomberg 年费约 $24,000）。它采用 C++20 + Qt6 原生开发，内嵌 Python 进行分析计算，提供单一原生二进制文件，无需 Electron/Web 运行时。

核心理念：让专业级金融分析工具对所有人免费可用。

---

## 核心功能

### 1. 多资产分析
- DCF 估值模型、投资组合优化
- 风险指标（VaR、Sharpe Ratio）
- 衍生品定价
- 覆盖股票、固定收益、衍生品、投资组合和另类投资

### 2. AI 智能代理（37个）
- **投资大师模拟**：巴菲特、格雷厄姆、彼得·林奇、芒格、卡拉曼、霍华德·马克斯等
- **经济分析**：宏观经济框架分析
- **地缘政治分析**：国际关系映射
- 支持本地 LLM，多提供商（OpenAI、Anthropic、Gemini、Groq、DeepSeek、Ollama 等）

### 3. 100+ 数据连接器
- DBnomics、Polygon、Kraken、Yahoo Finance、FRED、IMF、世界银行、AkShare
- 政府数据库 API
- 可选 Adanos 市场情绪数据（Reddit、X、财经新闻、Polymarket）

### 4. 实时交易
- 加密货币实时 WebSocket（Kraken/HyperLiquid）
- 股票交易、算法交易
- 模拟交易引擎
- **16 家券商集成**：Zerodha、Angel One、IBKR、Alpaca、Saxo 等

### 5. QuantLib 量化套件
- 18 个量化分析模块
- 定价、风险、随机过程、波动率、固定收益

### 6. 全球情报
- 海事追踪（AIS 船舶数据）
- 地缘政治分析
- 关系映射、卫星数据

### 7. 可视化工作流
- 节点编辑器构建自动化管道
- MCP 工具集成

### 8. AI 量化实验室
- 机器学习模型、因子发现
- 高频交易策略
- 强化学习交易

---

## 技术架构

| 组件 | 技术 |
|------|------|
| **核心语言** | C++20 |
| **UI 框架** | Qt 6.8.3 |
| **分析引擎** | 嵌入式 Python 3.11.9 |
| **构建系统** | CMake 3.27.7 + Ninja 1.11.1 |
| **量化库** | QuantLib |
| **分发方式** | 单一原生二进制文件 |

**架构亮点**：
- 原生 C++ 性能，无 Electron/Web 开销
- 嵌入式 Python 提供灵活的分析能力
- 跨平台支持 Windows、Linux、macOS
- Docker 支持（CI/CD 环境）

---

## 应用场景

1. **独立交易者**：免费获取专业级分析工具
2. **基金经理**：投资组合优化和风险分析
3. **量化分析师**：QuantLib 集成 + AI 量化实验室
4. **金融教育**：大学课堂使用的专业级工具
5. **金融科技开发者**：开源贡献和二次开发
6. **地缘政治分析师**：全球情报和关系映射

---

## 为什么火（Trending 原因）

1. **Bloomberg 替代品定位**：以 $0 对比 $24,000/年的 Bloomberg 订阅，极具话题性
2. **技术栈惊艳**：C++20 + Qt6 原生应用，非 Electron，性能表现突出
3. **功能极其丰富**：37 个 AI 代理、100+ 数据源、16 家券商、18 个量化模块
4. **v4.0 重大版本**：完全重写的 v4 标志着项目成熟
5. **Hacker News 热议**：Show HN 帖子引发社区广泛讨论
6. **AI + 金融的交叉领域**：当前最热门的两个技术方向的结合
7. **YouTube/Medium 传播**："开源 Bloomberg 杀手" 的标题极具传播力

---

## 同类项目对比

| 项目 | 类型 | 价格 | 技术栈 | AI 支持 | 交易功能 |
|------|------|------|--------|---------|---------|
| **FinceptTerminal** | 桌面终端 | 免费（AGPL-3.0） | C++20/Qt6/Python | 37个AI代理 | 16家券商 |
| **Bloomberg Terminal** | 专业终端 | ~$24,000/年 | 专有 | 有限 | 广泛 |
| **OpenBB** | Web/桌面终端 | 免费（MIT） | Python/React | 有限 | 无 |
| **TradingView** | Web平台 | 免费~$60/月 | Web | 基础 | 部分券商 |
| **QuantConnect** | 量化平台 | 免费~付费 | Python/C# | 无 | 部分 |
| **Robinhood** | 券商平台 | 免费 | Web/Mobile | 无 | 自有 |

**FinceptTerminal 的优势**：原生性能最强、AI 代理最多、数据源最广、唯一集成地缘政治分析
**劣势**：商业化许可限制严格（AGPL-3.0）、社区相对较新、主要面向印度券商

---

## 适合谁使用

- **个人投资者/交易者**：免费专业工具，替代昂贵的商业终端
- **量化分析师**：QuantLib + AI 量化实验室 + Python 嵌入式环境
- **金融专业学生/教授**：大学许可计划（$799/月/20账户）
- **金融科技开发者**：开源贡献，C++/Python 技术栈
- **加密货币交易者**：实时 WebSocket + 多交易所支持
- **对冲基金分析师**（需商业许可）：专业级分析和交易

---

## 快速上手

### 方式一：下载安装包（推荐）

从 [GitHub Releases](https://github.com/Fincept-Corporation/FinceptTerminal/releases) 下载：

| 平台 | 文件 |
|------|------|
| Windows x64 | `FinceptTerminal-Windows-x64-setup.exe` |
| Linux x64 | `FinceptTerminal-Linux-x64.run` |
| macOS ARM | `FinceptTerminal-macOS-arm64.dmg` |

### 方式二：一键构建

```bash
git clone https://github.com/Fincept-Corporation/FinceptTerminal.git
cd FinceptTerminal
chmod +x setup.sh && ./setup.sh
```

### 方式三：Docker

```bash
git clone https://github.com/Fincept-Corporation/FinceptTerminal.git
cd FinceptTerminal
docker build -t fincept-terminal .
docker run --rm -e DISPLAY=$DISPLAY -v /tmp/.X11-unix:/tmp/.X11-unix fincept-terminal
```

### 方式四：手动构建

```bash
git clone https://github.com/Fincept-Corporation/FinceptTerminal.git
cd FinceptTerminal/fincept-qt
cmake --preset linux-release    # 或 win-release / macos-release
cmake --build --preset linux-release
./build/linux-release/FinceptTerminal
```

**依赖版本（精确）**：CMake 3.27.7、Ninja 1.11.1、Qt 6.8.3、Python 3.11.9、C++20 编译器

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| **创新性** | ⭐⭐⭐⭐⭐ (9/10) | C++20 原生金融终端 + 37 AI 代理，技术路线独特 |
| **代码质量** | ⭐⭐⭐⭐ (8/10) | 精确版本锁定、CMake preset、单一二进制，工程化成熟 |
| **实用性** | ⭐⭐⭐⭐⭐ (9/10) | 覆盖分析、交易、研究全链路，100+ 数据源 |
| **文档完善度** | ⭐⭐⭐⭐ (8/10) | README 详细、安装指南完善，贡献指南齐全 |
| **社区活跃度** | ⭐⭐⭐⭐ (7/10) | Hacker News 热议、YouTube 评测，但社区尚在成长阶段 |
| **综合评分** | **⭐⭐⭐⭐ (8.2/10)** | 极具潜力的开源金融终端，值得长期关注 |

---

## 注意事项

1. **许可限制**：AGPL-3.0 对商业使用有限制，企业使用需购买商业许可
2. **依赖版本严格**：必须使用精确指定的版本（Qt 6.8.3、Python 3.11.9 等）
3. **社区代币**：项目有 pump.fun 代币，需注意加密货币风险
4. **券商偏向**：16 家券商中多数为印度券商，国际券商支持有限

---

*"你的思维是唯一的限制。数据不是。" — FinceptTerminal*
