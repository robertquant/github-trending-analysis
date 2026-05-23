# 📊 GitHub Trending 项目深度分析

> 自动追踪 GitHub 每日热门项目，AI 深度分析生成 HTML + Markdown 报告

## 📁 目录结构

```
├── html/                    # 精美 HTML 分析报告（深色科技风）
│   └── OWNER-REPO.html
├── md/                      # Markdown 分析报告
│   └── OWNER-REPO.md
├── progress.json            # 当日分析进度
├── analyzed.json            # 历史已分析项目列表
└── trending-list.json       # 当日 Trending 列表
```

## 📋 分析维度

每个项目从以下 5 个维度进行评分：

| 维度 | 说明 |
|------|------|
| 创新性 | 项目的技术创新和独特性 |
| 代码质量 | 代码组织、可维护性、测试覆盖 |
| 实用性 | 解决实际问题的能力和适用范围 |
| 文档完善度 | README、API 文档、使用指南 |
| 社区活跃度 | Stars、Forks、Issues、PR 活跃程度 |

## 🔄 更新频率

- **每日获取**: 每天 06:00 获取当日 GitHub Trending 列表
- **逐时分析**: 每小时分析 1 个待处理项目
- **自动提交**: 分析完成后自动推送到本仓库

## 📊 已分析项目

查看 [analyzed.json](./analyzed.json) 获取完整列表。

**已分析项目数**: 125

---

🤖 由 AI 自动分析生成 | Powered by Claude Code
