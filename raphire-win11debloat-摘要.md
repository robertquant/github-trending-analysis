# Raphire/Win11Debloat 深度分析摘要

> GitHub Trending · Windows 系统优化工具｜数据截至 2026-06-16

## 📌 一句话定位
一款**轻量、免安装、可逆**的开源 PowerShell 脚本，一行命令即可清理 Windows 10/11 的预装臃肿软件、关闭遥测、移除侵入式元素并进行深度自定义——当前 GitHub 上最流行的脚本式 Windows 减负方案之一。

## 🔢 关键数据
| 指标 | 数值 |
|---|---|
| ⭐ Stars | **48,256** |
| 🔱 Forks | 1,945 |
| 🤝 贡献者 | 27（主作者 Raphire 417+ 提交）|
| 🏷️ 最新版本 | 2026.06.14（高频更新）|
| 💻 语言 | PowerShell |
| 📜 协议 | MIT |
| 🌐 适用 | Windows 10 / 11 |

## 🏗️ 技术架构
- **纯 PowerShell 脚本项目**（仓库仅约 2.2 MB），无编译产物、无重型依赖。
- 主脚本 `Win11Debloat.ps1` + 模块化辅助脚本（按功能拆分），绝大多数调整通过**注册表键值**实现。
- **三种运行方式**：快速短链 `& ([scriptblock]::Create((irm "https://debloat.raphi.re/")))`、传统双击 `Run.bat`、高级手动 PowerShell（支持 CLI 参数）。
- **双模交互**：交互式菜单（普通用户）+ 命令行参数（自动化/脚本化）。
- **企业能力**：支持 Windows Audit 模式、Sysprep 模式（写入默认用户配置）、向其他用户应用更改。

## 💡 核心功能（十大领域）
1. **应用卸载** —— 批量移除预装 UWP/系统应用（可经 Store 重装）
2. **隐私 & 建议内容** —— 关闭遥测、诊断数据、活动历史、定位追踪、广告 ID、Spotlight、Edge/MSN 广告
3. **AI 功能**（前沿亮点）—— 禁用 Copilot、Recall、Click to Do、AI 服务自启动及 Edge/Paint/Notepad AI
4. **系统设置** —— 恢复旧版右键菜单、关闭鼠标加速/快速启动/BitLocker 自动加密
5. **Windows Update** —— 阻止自动更新与自动重启、关闭 P2P 分发（Delivery Optimization）
6. **开始菜单 & 搜索** —— 关闭 Bing/Copilot 搜索结果、搜索高亮
7. **任务栏** —— 左对齐、隐藏冗余图标、启用「结束任务」
8. **文件资源管理器** —— 显示扩展名/隐藏文件、自定义导航窗格
9. **多任务 & 可选功能** —— 一键启用 Windows Sandbox、WSL
10. **其他** —— 关闭 Xbox Game Bar 弹窗、清理 Brave 浏览器臃肿项

## 🎯 应用场景
- 个人新机开箱清理（最典型）
- 隐私敏感用户批量关闭遥测
- 游戏玩家优化（关 Game Bar、动画）
- **企业 IT / MSP 批量装机**（Sysprep/Audit）
- VDI 镜像瘦身、老旧硬件提速
- 开发者环境搭建（经典右键、WSL、Sandbox）

## ⚔️ 竞品对比（结论）
| 工具 | 定位 | 开源 | Win11 |
|---|---|---|---|
| **Win11Debloat** | 减负+隐私+自定义，企业部署 | ✅ MIT | ✅ 原生 |
| ChrisTitusTech/winutil | 全能瑞士军刀（GUI+装软件）| ✅ | ✅ |
| Sycnex/Win10Debloater | 深度减负先驱（已停滞）| ✅ | 偏 Win10 |
| O&O ShutUp10++ | 仅隐私/遥测 | ❌（免费）| ✅ |

**结论**：winutil 是功能最全的 GUI 瑞士军刀；ShutUp10 是隐私精准利器；Win11Debloat 以**纯开源、轻量免安装、紧跟 AI 演进、可逆安全、支持企业部署**的综合优势，成为开源纯粹主义者与 IT 专业人员的首选。

## 🏆 综合评分：9.0 / 10（强烈推荐 · Tier S）
- 项目活跃度 9.6 ｜ 社区影响力 9.5 ｜ 易用性 9.2 ｜ 文档完整性 9.0
- 安全/可逆性 9.0 ｜ 实用价值 8.8 ｜ 技术质量 8.6 ｜ 功能广度 8.5

### ✅ 优势
极简轻量免安装 ｜ 覆盖面广含最新 AI 臃肿 ｜ 改动完整可逆 ｜ 支持企业级 Sysprep ｜ MIT 开源高频更新 ｜ 菜单+CLI 双模

### ⚠️ 注意
减负对真实性能提升有限（媒体实测）｜ 曾遭 Defender/Bitdefender 误报（新版已修）｜ 无 GUI ｜ 激进关闭可能影响云集成 ｜ 需自担风险并做好还原点

---
📎 [GitHub 仓库](https://github.com/Raphire/Win11Debloat) ｜ [一键脚本](https://debloat.raphi.re/) ｜ [使用 Wiki](https://github.com/Raphire/Win11Debloat/wiki/How-To-Use) ｜ [还原指南](https://github.com/Raphire/Win11Debloat/wiki/Reverting-Changes)
