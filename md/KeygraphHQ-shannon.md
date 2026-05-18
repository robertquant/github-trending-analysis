# Shannon — AI 自动化渗透测试工具深度分析

> **KeygraphHQ/shannon** | TypeScript | 42,526 Stars (+335 Today) | AGPL-3.0

## 项目简介

Shannon 是由 Keygraph 团队开发的自主式白盒 AI 渗透测试工具，专为 Web 应用和 API 安全测试设计。它结合源代码分析与动态漏洞利用，能像一位「永不休息的高级安全工程师」一样自动完成完整渗透测试。

**核心理念：「无利用，不报告」（No Exploit, No Report）**——Shannon 不报告理论漏洞，只有成功利用并生成可复现 PoC 的漏洞才会出现在最终报告中，实现零误报。

## 核心功能

- **完全自主运行**：一条命令启动完整渗透测试，自动处理 2FA/TOTP、SSO、浏览器导航、漏洞利用和报告生成
- **可复现 PoC**：只包含已验证的可利用漏洞，附带可复制粘贴的概念验证代码
- **OWASP 漏洞覆盖**：注入攻击、XSS、SSRF、身份认证/授权绕过
- **代码感知动态测试**：分析源代码指导攻击策略，通过实时浏览器和 CLI 工具验证漏洞
- **并行处理**：漏洞分析和利用阶段跨所有攻击类别并发执行

## 技术架构

Shannon 采用多智能体架构，以 Anthropic Claude Agent SDK 作为推理引擎：

```
Phase 1: Pre-Reconnaissance（预侦察）→ 分析源代码，识别攻击面
Phase 2: Reconnaissance（侦察）→ 浏览器自动化探索，构建攻击面地图
Phase 3: Vulnerability Analysis（漏洞分析）→ 5 个并行 Agent 按 OWASP 分类寻找漏洞
Phase 4: Exploitation（漏洞利用）→ 将假设转化为实际攻击，执行真实漏洞利用
Phase 5: Reporting（报告）→ 汇总已验证发现，生成专业安全报告
```

**技术栈**：TypeScript、Anthropic Claude SDK、Docker、Temporal、Browser Automation、pnpm

**模型分层**：
- Small (Claude Haiku 4.5) → 快速摘要
- Medium (Claude Sonnet 4.6) → 安全分析
- Large (Claude Opus 4.7) → 深度推理

## Benchmark 表现

- **XBOW Security Benchmark**: 96.15%（100/104 exploits）
- **OWASP Juice Shop**: 20+ 漏洞，包括认证绕过、数据库窃取、IDOR、SSRF
- **c{api}tal API**: ~15 个关键/高危漏洞，XSS 零误报
- **OWASP crAPI**: 15+ 关键/高危漏洞，包括 JWT 多攻击向量

## 为什么火（Trending 原因）

1. **填补安全测试频率缺口**：团队每天持续交付代码，但渗透测试一年才做一次，Shannon 让渗透测试也能持续化
2. **AI 安全赛道爆发**：2026 年 AI + 安全是最大热点之一
3. **96.15% 惊人基准测试成绩**：超越许多传统安全测试工具
4. **零误报承诺**：直击传统 SAST/DAST 工具最大痛点
5. **AGPL 开源**：核心框架完全开源，社区信任度高
6. **完整产品矩阵**：从 Lite 到 Pro，覆盖个人到企业级需求

## 同类项目对比

| 特性 | Shannon Lite | Burp Suite | OWASP ZAP | Snyk/SonarQube |
|------|-------------|------------|-----------|----------------|
| 测试类型 | 白盒+动态利用 | 黑盒代理扫描 | 黑盒扫描 | 静态分析 |
| 自主程度 | 完全自主 | 需人工操作 | 半自动 | 自动化 |
| PoC 验证 | 自动生成 | 需人工验证 | 需人工验证 | 无 |
| 误报率 | 极低 | 中等 | 较高 | 中等偏高 |
| 源码分析 | 有 | 无 | 无 | 有 |
| AI 驱动 | 是 | 否 | 否 | 部分 |
| 价格 | 开源（API~$50/次）| 付费 | 免费 | 免费/付费 |

## 适合谁使用

- **安全工程师/渗透测试员**：自动化繁重工作，提升测试效率
- **DevSecOps 团队**：CI/CD 集成，每次构建自动安全测试
- **全栈/后端开发者**：自行测试代码安全性，无需等待年度渗透测试
- **初创公司/小团队**：替代昂贵的第三方渗透测试服务
- **安全学习者**：学习渗透测试方法论和漏洞利用技术
- **企业级安全团队**：推荐 Pro 版（SAST + SCA + 商业逻辑测试）

## 快速上手

```bash
# 前置要求：Docker、Node.js 18+、Anthropic API Key

# 1. 配置凭证
npx @keygraph/shannon setup

# 2. 启动渗透测试
npx @keygraph/shannon start -u https://your-app.com -r /path/to/your-repo

# 3. 监控进度
npx @keygraph/shannon logs <workspace>

# 4. 查看报告（在 ~/.shannon/workspaces/ 目录下）
```

> **重要警告**：Shannon 会主动执行攻击，切勿在生产环境运行！仅在沙箱/测试环境使用，并确保获得系统所有者明确书面授权。

## Shannon Pro vs Lite

| 能力 | Lite | Pro |
|------|------|-----|
| 静态分析 | 代码审查提示 | 完整 SAST + SCA + 密钥检测 + 商业逻辑 |
| 动态测试 | 自主 AI 渗透 | 渗透测试 + 静动态关联 |
| 分析引擎 | 代码审查提示 | CPG 数据流 + LLM 推理 |
| CI/CD | 手动/CLI | 原生 CI/CD + GitHub PR 扫描 |
| 商业逻辑测试 | 无 | 自动不变量发现 + 利用合成 |

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 9.5/10 | AI 自主渗透测试的标杆实现，理念领先 |
| 代码质量 | 8.5/10 | 架构清晰，多 Agent 设计合理 |
| 实用性 | 9.0/10 | 直击安全测试频率痛点，开箱即用 |
| 文档完善度 | 9.0/10 | README 详尽，示例丰富，平台说明完善 |
| 社区活跃度 | 8.5/10 | 快速增长，但暂不接受外部 PR |
| **综合** | **8.9/10** | **强烈推荐** |

---

*分析日期：2026-05-18 | 数据来源：GitHub、WebSearch*
