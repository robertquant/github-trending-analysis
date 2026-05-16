# witr - Why Is This Running?

> 跨平台 CLI 工具，追踪进程、服务或端口的起源和责任链，用人类可读的方式解释**为什么**某个东西正在运行。

| 属性 | 详情 |
|---|---|
| **仓库** | [github.com/pranshuparmar/witr](https://github.com/pranshuparmar/witr) |
| **作者** | Pranshu Parmar (pranshuparmar) |
| **语言** | Go |
| **Stars** | 16,536 (+484 today) |
| **协议** | Apache-2.0 |
| **平台** | Linux / macOS / Windows / FreeBSD |

---

## 项目简介

`witr`（Why Is This Running?）是一个回答单一问题的工具：**为什么这个进程在运行？**

它追踪进程的完整祖辈链，展示进程从哪里来、怎么启动的、哪些系统负责它的存在。不再需要手动组合 `ps` + `lsof` + `ss` + `pstree` + `systemctl`。

---

## 核心功能

- **进程溯源追踪** — 展示完整的父进程链（parent chain），从 init 到目标进程
- **交互式 TUI 模式** — 实时终端仪表盘，搜索、过滤、导航
- **多维度查询** — 按进程名、PID、端口号、打开的文件
- **容器感知** — 自动检测 Docker、Podman、Kubernetes、Containerd
- **服务检测** — 识别 systemd、launchd、Windows Services、rc.d 关联
- **健康警告** — 标注 root 进程、公网端口绑定、高内存占用等风险
- **录制回放** — atop 风格的录制回放，事后分析
- **丰富输出格式** — 标准、简洁、树形、JSON、环境变量、详细六种格式
- **Shell 补全** — Bash、Zsh、Fish、PowerShell
- **零配置** — 无需配置文件，安装即用

---

## 技术架构

- **Go 语言** — 编译为单一二进制文件，零依赖
- **跨平台** — Linux、macOS、Windows、FreeBSD
- **分发渠道** — Homebrew、Conda、AUR、Winget、NPM、Chocolatey、Scoop、Nix、FreeBSD Ports 等 15+ 包管理器
- **设计哲学** — "一个问题，一个工具"；有主见的优先排序；压力下可读

---

## 使用示例

```bash
# 查询某个进程为什么在运行
witr nginx

# 通过 PID 查询
witr --pid 1234

# 查询占用某个端口的进程
witr --port 8080

# 交互式 TUI 模式
witr -i

# JSON 输出（适合脚本集成）
witr --format json nginx

# 树形展示进程祖辈关系
witr --format tree nginx

# 录制系统状态
witr record -o session.witr

# 回放录制
witr replay session.witr
```

---

## 应用场景

1. **SSH 登录陌生服务器** — 快速理解"这个系统上到底在跑什么"
2. **排障与安全审计** — 追溯可疑进程来源、服务归属、网络监听
3. **容器环境调试** — 识别容器类型，展示宿主机与容器的映射关系
4. **新员工入职** — 快速了解生产服务器服务拓扑
5. **CI/CD 调试** — 排查端口冲突、进程残留

---

## 为什么火 (Trending 原因)

1. **填补真实痛点** — 每个 Linux 用户都问过这个问题，但从未有专门工具
2. **一工具替代一串命令** — ps + lsof + ss + systemctl + pstree 的统一替代
3. **极低上手门槛** — 单一二进制、零配置、`brew install` 即用
4. **社区热议** — Hacker News、Reddit、YouTube 多平台传播
5. **TUI 体验优秀** — 美观实用，符合现代 CLI 工具审美
6. **命名即品牌** — 名字本身就是最好的推广
7. **时机恰好** — DevOps/SRE 文化和"可观测性"热潮下需求旺盛

---

## 同类项目对比

| 功能 | witr | ps+pstree | htop/btop | procs | lsof/ss |
|---|---|---|---|---|---|
| 进程溯源 | ✅ | ❌ | ❌ | ❌ | ❌ |
| 服务关联 | ✅ | ❌ | ❌ | ❌ | ❌ |
| 容器感知 | ✅ | ❌ | ❌ | ❌ | ❌ |
| 网络端口追踪 | ✅ | ❌ | ✅ | ❌ | ✅ |
| 健康警告 | ✅ | ❌ | ✅ | ❌ | ❌ |
| 交互式 TUI | ✅ | ❌ | ✅ | ❌ | ❌ |
| JSON 输出 | ✅ | ❌ | ❌ | ✅ | ❌ |

**独特定位：** witr 是"因果关系解释器" — 不只展示数据，而是解释因果链。

---

## 适合谁

- **SRE / DevOps 工程师** — 日常排障、On-call 值班必备
- **系统管理员** — 快速理解多台服务器上运行的服务
- **安全工程师** — 安全审计时追溯可疑进程来源
- **Linux 学习者** — 通过可视化理解系统启动和服务模型
- **容器开发者** — 理解容器内外进程映射关系
- **后端开发者** — 调试本地端口冲突、进程残留

---

## 快速上手

```bash
# 安装（选择其一）
brew install witr
go install github.com/pranshuparmar/witr@latest

# 使用
witr nginx          # 查询进程
witr --port 8080    # 查询端口
witr -i             # TUI 模式
witr --format json nginx | jq .  # JSON 输出
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|---|---|---|
| 创新性 | 8.5/10 | 概念新颖，填补长期空白 |
| 代码质量 | 8.0/10 | Go 项目结构清晰，跨平台支持完善 |
| 实用性 | 9.5/10 | 每个 Linux 用户都需要的工具 |
| 文档完善度 | 9.0/10 | README 详尽，功能矩阵、安装指南齐全 |
| 社区活跃度 | 8.5/10 | 多平台讨论，15+ 包管理器支持 |

**综合评分：8.7 / 10 — 强烈推荐**

---

*分析日期: 2026-05-17 | 数据来源: GitHub, Hacker News, Reddit*
