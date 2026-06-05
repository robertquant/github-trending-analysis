# last30days-skill 深度分析摘要

**项目：** [mvanhorn/last30days-skill](https://github.com/mvanhorn/last30days-skill)
**作者：** Matt Van Horn | **Stars：** 27,000+ | **版本：** v3 | **许可证：** MIT

## 一句话定位
AI Agent 驱动的「社交搜索引擎」——聚合 Reddit、X、YouTube、TikTok、HN、Polymarket 等 12+ 平台最近 30 天的内容，按真实人类互动（投票、点赞、真金赔率）评分，生成结构化研究简报。

## 核心创新
- **智能实体解析：** 搜索前自动解析人物、公司对应的 X handles / GitHub / subreddit / YouTube 频道
- **跨源聚类合并：** 同一故事在多平台出现时自动去重合并
- **社交评分体系：** Upvotes、Likes、播放量、Polymarket 赔率替代 SEO 排序
- **BYOK 架构：** 携带自己的 API Key，数据全在本地，无中间商

## 技术栈
Python 3.12+ / Node.js / yt-dlp / ScrapeCreators API / SQLite / SKILL.md 规范 / 1,012 测试通过

## 应用场景
会议准备（30秒了解对方近30天动态）、产品对比、趋势追踪、投资研究、旅行规划、定时监控

## 竞品对比
| 维度 | last30days | Google | ChatGPT | Gemini |
|------|-----------|--------|---------|--------|
| Reddit | 深度评论+投票 | 有限 | 有限 | 无 |
| X/Twitter | 浏览器Cookie | 有限 | 无 | 无 |
| 预测市场 | Polymarket | 无 | 无 | 无 |
| 隐私 | 完全本地 | 云端 | 云端 | 云端 |

## 综合评分：8.5 / 10
- 创新性：9.5 | 实用性：9.0 | 技术实现：8.5 | 社区活跃度：9.0 | 易用性：7.5 | 可扩展性：8.5
