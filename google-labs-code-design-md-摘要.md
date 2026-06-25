# 🎨 DESIGN.md 深度分析摘要

> **google-labs-code/design.md** · GitHub Stars 18.8K+ · Apache-2.0 · 格式版本 alpha · 分析日期 2026.06.26

## 一句话定位
Google Labs 推出的**开放格式规范**——用一份 Markdown 文件，把"机器可读的设计 Token"和"人类可读的设计意图"统一封装，让 AI 编码 Agent（Claude Code、Cursor 等）获得对设计系统的**持久化、结构化理解**。

## 项目背景
- **出品方**：Google Labs（`google-labs-code` 组织），脱胎于 Gemini 驱动的 AI UI 设计工具 **Stitch**（前身 Galileo AI）。
- **起源痛点**：设计到代码（Design-to-Code）交接中，设计系统规则无法稳定地传递给下游 AI Agent，导致生成的 UI 千篇一律（AI slop）。
- **核心成果**：将 Stitch 内部格式抽离规范化，2025 年底以 Apache-2.0 开源，配套 TypeScript CLI `@google/design.md`，上线即爆火，Star 迅速突破 1.8 万。

## 核心架构："一份文件、两层结构"
| 层 | 内容 | 作用 |
|---|---|---|
| YAML front matter | 设计 Token（colors / typography / rounded / spacing / components） | 给 Agent **精确数值**（规范性） |
| Markdown 正文 | Overview / Colors / Do's & Don'ts 等设计理念 | 告诉 Agent **为什么**及**如何应用** |

**配套工具链**（CLI 四大子命令）：
- `lint` — 9 条内建规则，含 **WCAG AA 对比度（4.5:1）**、断链引用、孤立 Token 检测
- `diff` — 两版对比，检测**设计回归**
- `export` — 一键导出 **Tailwind v3/v4、W3C DTCG** 标准格式
- `spec` — 输出规范，便于**注入 Agent 提示词**

## 核心创新点
1. **"Token + 意图"双层数据模型**——既给值，也给"为什么"，AI 生成有灵魂的 UI。
2. **纯文本 Markdown 对抗二进制锁定**——天然可 Git 版本化、可 diff、可 Code Review。
3. **9 条 Lint 规则**——把可访问性与一致性前移到"写设计系统"环节。
4. **diff 设计回归检测**——相当于给设计系统加了"CI"。
5. **一键导出主流生态**——一份 DESIGN.md → Tailwind / CSS / DTCG 跨工具零摩擦。
6. **spec 命令直注 Agent 上下文**——形成 Stitch 导出 → Claude Code 消费闭环。

## 应用场景
- **最核心**：Stitch → Claude Code 设计到代码交接（DESIGN.md 写入 CLAUDE.md，每个会话自动加载一致规范）。
- 消除 AI 生成 UI 的"千篇一律"，作为品牌识别护栏。
- 设计系统版本化与协作（Git PR 评审设计变更）。
- 跨设计工具互操作（导出 W3C DTCG，Figma/Penpot 无损流转）。
- CI 中接入 linter/diff 做设计令牌治理与回归保护。

## 竞品对比
| 维度 | DESIGN.md | W3C Design Tokens | Figma Variables | Style Dictionary |
|---|---|---|---|---|
| AI 原生 | ✅ 为 Agent 而生 | ✗ | △ 需 MCP | ✗ |
| 人类可读 | ✅ Markdown | ✗ JSON | △ GUI | ✗ |
| 设计意图(why) | ✅ 内建 prose | ✗ | ✗ | ✗ |
| 版本化/Diff | ✅ 纯文本 Git | ✅ | ✗ 二进制 | ✅ |
| 生态成熟度 | ★★★ 新生(alpha) | ★★★★ 标准 | ★★★★★ 主流 | ★★★★ 成熟 |

**结论**：DESIGN.md 是唯一从 AI Agent 视角出发的格式，与 W3C DTCG（标准）、Figma Variables（设计师主场）、Style Dictionary（构建引擎）互补而非完全替代。

## 综合评分：**8.4 / 10**
> 潜力巨大的"AI 设计系统标准雏形"

| 维度 | 分数 |
|---|---|
| 战略定位与时机 | 9.5 |
| 格式设计优雅度 | 9.0 |
| 工具链完整度 | 8.5 |
| 实际应用价值 | 8.5 |
| 社区热度与背书 | 8.5 |
| 生态成熟度（短期） | 6.5 |

**风险提示**：格式仍为 `alpha`，官方明确会有破坏性变更；不纳入 Google 开源漏洞奖励计划。建议非生产关键路径先行试用。

**总评**：DESIGN.md 不是"又一个 Token 库"，而是一次**范式提案**——把设计系统的服务对象从"人类设计师"翻转为"AI Agent"。在 Vibe Coding 成为主流的 2026 年，它极可能成为 AI 时代设计到代码交接的事实标准之一。

---
📎 完整深度分析报告：`google-labs-code-design-md-深度分析报告.html`
