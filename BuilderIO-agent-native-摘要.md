# Agent-Native 深度分析摘要

> **项目**：[BuilderIO/agent-native](https://github.com/BuilderIO/agent-native) · 代理原生应用框架
> **作者**：Builder.io（CEO Steve Sewell）　**语言**：TypeScript　**协议**：MIT
> **热度**：~1.1k ⭐ / 119 Forks　**包名**：`@agent-native/core`　**官网**：agent-native.com
> **综合评分**：**8.4 / 10**（强烈关注）　**报告日期**：2026-06-20

---

## 一句话定位
Builder.io 开源的「代理原生（Agent-Native）应用」框架。它让 **AI Agent 不再只是「挂在聊天框旁边」，而是真正在应用内部行动**——人类用户与 Agent 共享同一套动作、数据、权限与上下文。

> "Don't choose between a rich UI and an autonomous Agent. Every Agent-Native app is both."
> 在丰富的可视化界面与自主 Agent 之间，不必再做选择题。

---

## 核心理念：Click it or ask for it
同一个产品能力，既能在 UI 里点击触发，也能被 Agent 用工具调用执行——背后共享**同一份动作定义、同一份数据状态、同一套权限**。

### 软件演化三阶「梯子」
| 阶段 | 含义 | 判据 | 例子 |
|---|---|---|---|
| **AI-Enabled**（AI 辅助） | 产品有 AI 功能，去掉 AI 仍基本可用 | 拿掉 AI 产品还能用？→ 是 | 带 AI 摘要按钮的项目管理工具 |
| **AI-Native**（AI 原生） | AI 是产品价值核心，去掉就垮 | 拿掉 AI 产品就垮？→ 是 | 编码助手、图像生成器 |
| **Agent-Native**（代理原生） | AI 居中，**且**产品拥有完整人机界面，二者共享动作/数据/权限 | UI 与 Agent 能操作同一工作流？→ 是 | 邮件客户端：人手动分类，Agent 通过相同动作归档/起草/打标/路由 |

---

## 技术架构：核心原语
框架为「产品级 Agentic 软件」提供原语：**共享动作、SQL 驱动状态、身份、工具、技能、任务、可观测性** + 协同的 UI 表面。**后端完全可替换**（任意 Drizzle 支持的 SQL 数据库 + 任意 Nitro 兼容的托管）。

### 灵魂：统一动作模型（One Action Model）
一次 `defineAction`，自动暴露为 **UI 变更 / Agent 工具 / HTTP 端点 / CLI / MCP 工具 / A2A 工具**——从源头消灭「每个表面各写一份」带来的漂移（drift）。

```ts
export default defineAction({
  description: "Reply to an email thread",
  schema: z.object({ emailId: z.string(), body: z.string() }),
  run: async ({ emailId, body }) => {
    await db.insert(replies).values({ emailId, body });
  },
});
```

### 五大架构原则
1. **Agent UI Parity**（代理-界面对等）：UI 能做的 Agent 也能做，且可被看见/检查/控制。Agent 不屏幕抓取，而是调用驱动产品的同一底层能力。
2. **One Shared Action Model**：能力只定义一次，多面暴露。
3. **Shared State/Data/Context**：Agent 知道你在看什么、选中什么；`view-screen` 给快照、`navigate` 移动 UI；**数据库是人与 Agent 的协调层**（动作写 SQL → 版本变 → UI 失效更新）。
4. **Protocol-Ready by Design**：协议支持（MCP、A2A）是架构属性而非一次性集成；动作已是共享单元，暴露给 MCP/A2A/CLI 只是「路由问题」。
5. **Governed Execution**：Agent 遵守与用户相同的权限边界，操作可限定、可审计、必要时可撤销。

### 实时与工作区
- **Real-time Multiplayer**：人与 Agent 实时协作，CRDT 合并 + 实时存在感（光标/选区），Agent 是一等「对等编辑者」，可在任意 SQL/任意主机（含 Serverless）运行。
- **SQL-backed Workspace**：技能、记忆、指令、子 Agent、MCP 服务器全部 SQL 化、按用户/组织定制——把 Claude Code 级灵活性带进 SaaS 经济模型。
- **Agents Call Agents**：跨 App 标记 Agent，经 A2A 互相发现、跨栈行动。
- **Reusable Integrations**：Dispatch 连接一次供应商，密钥入 vault，多 App 共享。

---

## 一个 Agent，三种产品形态（无需重建 Agent 契约）
| 形态 | 交付物 | 底层共享 |
|---|---|---|
| **Headless**（无头） | 代码/CLI/HTTP/MCP/A2A 调用 | `defineAction`、auth、skills、memory、jobs、observability |
| **Rich Chat**（富聊天） | 独立/嵌入式聊天，原生表格/图表/审批/设置流 | 共享聊天运行时 + BYO 适配器 + 动作原生渲染器 |
| **Whole App**（完整应用） | 完整 SaaS UI，聊天可居中/侧栏，与应用状态同步 | SQL 状态、动作、上下文感知、深链、实时同步 |

**协议随框架附赠**：A2A、MCP、MCP Apps、远程 MCP OAuth、AG-UI、Claude Agent SDK、Vercel AI SDK、OpenAI 运行时连接器等，全挂在同一动作表面。

---

## 核心创新点
1. **Action 即「单一事实来源」**——`defineAction` 收敛产品能力，消灭 UI/API/工具/CLI 漂移。
2. **数据库作为协调层**——人与 Agent 共享 SQL 状态，简洁、可移植、可审计，无需脆弱的浏览器自动化。
3. **可克隆 SaaS（Cloneable Apps）**——每个模板是完整开源 SaaS，fork 即用，拥有代码与数据，打破「一刀切」SaaS 的所有权困局。
4. **零配置跨应用 A2A**——同源部署带来共享登录 + 跨 App A2A，`@mail` 在日历聊天里直接调起邮件 Agent。
5. **应用自我演进**——Agent 不发版即可加功能、修 bug、优化 UI；运行时工具成熟后「毕业」为模板特性。
6. **SQL 化工作区经济**——指令/记忆/技能/子 Agent/定时任务存 SQL，把 Claude Code 体验带进 SaaS。

---

## 应用场景（已提供可克隆模板）
| 模板 | 对标 | Agent 角色 |
|---|---|---|
| 📅 Calendar | Google Calendar / Calendly | 管理日程、Google 同步、AI 排程、公开预约页 |
| 📝 Content | 开源 Obsidian（MDX） | 编辑 MD/MDX、生成富交互块、起草/改写/发布 |
| 🗂️ Plans | 编码 Agent 可视化计划模式 | `/visual-plan` + `/visual-recap` 技能 |
| 🎤 Slides | Google Slides / Pitch | 提示或点击生成/编辑 React 演示文稿 |
| 📊 Analytics | Amplitude / Mixpanel | 连接数据源、提示生成图表、可复用仪表盘 |
| 🎬 Clips | Loom | 录屏+自动转录+分享，Agent 摘要/字幕/编辑 |
| ✉️ Mail / 📋 Forms | 邮件 / 表单 SaaS | 三步分诊、跨系统拉取上下文、自动路由 |

**落地路径**：个人（周末克隆 + 自带 LLM Key 跑真实工作流）→ 团队（托管/鉴权/权限/治理，由 Builder.io 承担「团队层」）→ 生态（跨 App Agent 互联）。

---

## 快速开始
```bash
npx @agent-native/core@latest create my-platform   # 多选模板，一个 workspace 装多个 app
cd my-platform && pnpm install && pnpm dev

npx @agent-native/core@latest create my-app --standalone --template mail   # 单 App
npx @agent-native/core@latest skills add visual-plan   # 只给编码 Agent 加技能
npx @agent-native/core@latest deploy                   # 同源部署，共享登录 + 零配置 A2A
```

---

## 竞品对比
| 方案 | UI | AI/Agent | 可定制 | 所有权 | 核心差异 |
|---|---|---|---|---|---|
| 传统 SaaS | 精美但僵化 | 外挂式 | 几乎不能 | 租用 | Agent 只能「旁白」 |
| 裸 Agent（Claude Projects） | 无 | 强大 | 指令/技能 | 半自有 | 空白画布、无产品形态 |
| AI 应用构建器（Bolt/Lovable/v0） | 生成 UI | 生成式 | 代码可改 | 自有 | 偏一次生成，缺运行时 Agent-UI 同步 |
| CopilotKit / 应用内 AI SDK | 嵌入组件 | 聊天优先 | 组件级 | 自有 | 把 AI 嵌进现有 App，非 Agent-Native 架构 |
| LangGraph / Mastra / VoltAgent | 无内置 | 编排强大 | 高 | 自有 | 专注编排，UI/产品形态需自建 |
| **Agent-Native** | **完整 UI、fork 即用** | **Agent 优先、深度集成** | **Agent 直接改 App** | **自有代码+数据** | **UI 与 Agent 共享同一动作表面** |

**护城河**：竞品多在单点上很强，Agent-Native 的稀缺之处在于**架构层面就强制 Agent 与 UI 对等**，并以「可克隆 SaaS + 统一动作模型」给出从个人到团队的可落地路径。

---

## 综合评估
| 维度 | 评分 |
|---|---|
| 概念创新性 | **9.0** |
| 技术架构 | **8.6** |
| 工程成熟度 | **7.8** |
| 文档与生态 | **8.5** |
| 社区活跃度 | **7.5** |
| 商业潜力 | **8.5** |

**✅ 优势**：概念前瞻、架构优雅（消灭漂移）、开箱即用多模板、原生拥抱 MCP/A2A/AG-UI、商业闭环清晰（开源 + 团队层托管）。
**⚠️ 风险**：较新（~1.1k⭐，API/模板快速演进）、概念需市场教育、存在框架锁定倾向、Agent 权限等同用户使安全面扩大。

**适合谁**：想构建「人机协作型 SaaS」并拥有代码/数据的独立开发者与初创团队；要把内部工具 Agent 化又不想从零搭 UI 的工程团队；希望在产品中嵌入「真正能操作产品的 Agent」的产品团队。

---

## 结论
Agent-Native 不仅是框架，更是 Builder.io 对「下一代软件架构」的押注：**未来应用，人能做的 Agent 也能做，且共享同一套动作、数据与权限**。它用统一动作模型、数据库协调层和可克隆 SaaS，把抽象理念落成了可 fork、可改造、可托管的工程现实。对关注 Agent 与产品融合趋势的开发者，值得现在就用真实工作流去验证。

*"Clone a template this weekend. Use your own API key. The agent is already there."*

---
**数据来源**：[GitHub 仓库 README](https://github.com/BuilderIO/agent-native) · [Builder.io 架构博客](https://www.builder.io/blog/agent-native-architecture) · [How to build agent-native apps](https://www.builder.io/blog/agent-native-apps) · TrendShift
