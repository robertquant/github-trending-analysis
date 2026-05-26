# Jellyfin - 完全免费开源的媒体服务器

> The Free Software Media System - Server Backend & API

| 项目 | 信息 |
|------|------|
| GitHub | [jellyfin/jellyfin](https://github.com/jellyfin/jellyfin) |
| Stars | 56k+ |
| 开源协议 | GPL-2.0 |
| 技术栈 | C# / .NET 10 |
| 最新版本 | 10.11.x 系列 (10.11.8) |
| 官网 | [jellyfin.org](https://jellyfin.org) |

---

## 项目简介与核心功能

**Jellyfin** 是一个完全免费、开源的媒体服务器系统，让你掌控自己的媒体内容管理和串流体验。它是 Plex 和 Emby 的自由软件替代品，没有任何高级许可证、隐藏收费或付费功能。

### 核心功能

- **媒体管理与串流** — 支持电影、电视剧、音乐、照片的自动元数据抓取、整理和跨设备串流
- **硬件转码** — 支持 GPU 硬件加速（Intel QSV、NVIDIA NVENC、AMD AMF、VAAPI、VideoToolbox）
- **实时 TV 与 DVR** — 支持直播电视和节目录制功能
- **多客户端** — Web、Android、iOS、Roku、Fire TV、Android TV 等全平台支持
- **字幕支持** — 自动下载字幕，支持多字幕轨道
- **用户与权限管理** — 多用户支持，家长控制，细粒度访问控制
- **插件生态** — 60+ 社区插件，可扩展功能如主题美化、SSO 登录、书签同步等

---

## 技术架构与特点

| 组件 | 技术 |
|------|------|
| 后端服务 | C# / .NET 10（跨平台） |
| Web 前端 | Vue.js（独立 jellyfin-web 仓库） |
| 数据库 | EF Core + SQLite（10.11 统一为 jellyfin.db） |
| 媒体处理 | FFmpeg / jellyfin-ffmpeg |
| API | RESTful API（Swagger 文档） |
| 容器化 | Docker 官方镜像 |

### 架构亮点

- **10.11 重大重构** — 将遗留的 `library.db` 合并到统一的 `jellyfin.db`，完成 EF Core 迁移，这是项目历史上最大的一次数据库架构升级
- **前后端分离** — Web 客户端和服务器可独立部署和开发
- **跨平台** — 支持 Windows、Linux、macOS、Docker、NAS 等多种部署方式
- **GitHub Codespaces 支持** — 提供开箱即用的云端开发环境
- **插件架构** — 通过 File Transformation 插件机制可在不直接修改文件的情况下扩展 Web 界面

---

## 应用场景

- **家庭媒体中心** — 在 NAS 或家用服务器上搭建私人 Netflix
- **个人影音管理** — 高效管理个人收藏的电影、剧集、音乐和照片
- **远程串流** — 在外也能通过手机或浏览器访问家中的媒体库
- **宿舍/小团队共享** — 小范围内共享资源，支持多用户和权限管理
- **直播电视录制** — 配合电视调谐器实现 DVR 功能
- **数据隐私** — 不依赖任何云服务，所有数据完全掌握在自己手中

---

## 为什么火（Trending 原因）

1. **Plex 商业化转向** — Plex 近年来不断增加广告、强制引入云服务，大量用户流失到 Jellyfin
2. **10.11 里程碑版本** — 完成 EF Core 重大数据库重构，被官方称为"项目历史上最大和最有影响力的发布之一"
3. **市场份额超越 Plex** — 2024 年在自托管媒体服务器市场达到 51.2%，首次超越 Plex
4. **活跃的插件生态** — 社区插件在 2026 年持续爆发
5. **完全免费无套路** — 硬件转码、移动端同步、直播 TV、DVR 全部免费
6. **隐私保护意识提升** — 无追踪、无遥测理念契合隐私趋势

---

## 同类项目对比

| 特性 | Jellyfin | Plex | Emby |
|------|----------|------|------|
| 开源 | ✅ 完全开源 (GPL-2.0) | ❌ 闭源 | ⚠️ 部分开源 |
| 费用 | 完全免费 | 免费 + Plex Pass | 免费 + Premiere |
| 硬件转码 | 免费 | 需 Plex Pass | 需 Premiere |
| 移动端同步 | 免费 | 需 Plex Pass | 需 Premiere |
| 元数据匹配 | ~95% | ~98% | 良好 |
| 易用性 | 中等 | 最佳 | 中等 |
| 广告/追踪 | 无 | 有 | 少量 |
| 插件生态 | 最活跃 (60+) | 丰富但受限 | 较少 |
| 社区活跃度 | 极高 | 高 | 较低 |

**总结：** Plex 胜在易用性和生态打磨，Jellyfin 胜在免费、开放和隐私保护，Emby 介于两者之间。

---

## 适合谁使用

- **家庭 NAS 用户** — 有 NAS 或家用服务器，想搭建私人媒体库
- **隐私敏感用户** — 不愿让第三方公司接触自己媒体数据
- **Plex 逃离者** — 对 Plex 广告化、商业化不满的用户
- **自托管爱好者 (Homelabber)** — 喜欢搭建和维护自己的服务
- **开源支持者** — 认同自由软件理念，愿意参与社区贡献
- **学生/宿舍/小团队** — 小范围内共享媒体资源且不想付费

---

## 快速上手指南

### Docker 部署（推荐）

```bash
docker run -d \
  --name jellyfin \
  -p 8096:8096 \
  -v /path/to/config:/config \
  -v /path/to/cache:/cache \
  -v /path/to/media:/media \
  --restart=unless-stopped \
  jellyfin/jellyfin
```

### Docker Compose（生产推荐）

```yaml
version: '3'
services:
  jellyfin:
    image: jellyfin/jellyfin
    container_name: jellyfin
    ports:
      - "8096:8096"
    volumes:
      - ./config:/config
      - ./cache:/cache
      - /your/media:/media
    restart: unless-stopped
```

### 从源码构建

```bash
# 安装 .NET 10 SDK 和 FFmpeg
git clone https://github.com/jellyfin/jellyfin.git
cd jellyfin
dotnet run --project Jellyfin.Server --webdir /path/to/jellyfin-web/dist
```

### 访问与初始化

启动后访问 `http://localhost:8096` 进入设置向导，按提示添加媒体库即可。API 文档位于 `http://localhost:8096/api-docs/swagger/index.html`

---

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | 7.5/10 | 作为 Emby 分支起步，但在开源免费路线上的坚持形成了独特价值 |
| 代码质量 | 8.5/10 | .NET 生态规范，10.11 的 EF Core 迁移展现了工程能力 |
| 实用性 | 9.5/10 | 解决真实需求，覆盖几乎所有媒体管理场景 |
| 文档完善度 | 8.0/10 | 官方文档齐全，社区贡献了大量教程和指南 |
| 社区活跃度 | 9.0/10 | Reddit、Discord、GitHub 极度活跃，插件生态蓬勃发展 |

**综合评分：8.5 / 10** — 高度成熟的自由软件项目，实用价值极高，社区活力充沛

---

## 相关链接

- [GitHub 仓库](https://github.com/jellyfin/jellyfin)
- [官方网站](https://jellyfin.org)
- [官方文档](https://jellyfin.org/docs/)
- [插件生态](https://github.com/awesome-jellyfin/awesome-jellyfin)
- [State of the Fin 2026](https://jellyfin.org/posts/state-of-the-fin-2026-01-06/)

---

*分析日期：2026-05-27 | 数据来源：GitHub, Jellyfin 官方博客, 社区讨论*
