# Brush — 3D Reconstruction for all

> 基于 Gaussian Splatting 的跨平台 3D 重建引擎，由 Google DeepMind 研究员开发

| 指标 | 数据 |
|------|------|
| GitHub | [ArthurBrussee/brush](https://github.com/ArthurBrussee/brush) |
| Stars | 4,241 |
| 今日新增 | +78 |
| 语言 | Rust |
| 作者 | Arthur Brussee (Google DeepMind) |
| 许可证 | Apache 2.0 |
| 最新版本 | 0.3 |

---

## 项目简介

**Brush** 是一款开源 3D 重建引擎，核心基于 **3D Gaussian Splatting (3DGS)** 技术。项目愿景是让 3D 重建「人人可用」——无论你使用什么操作系统、什么 GPU 厂商，甚至只需要一个浏览器。

Brush 使用 Rust 编写，基于 Burn 深度学习框架和 wgpu/WebGPU GPU 计算接口，实现了从桌面端到移动端、从本地到浏览器的全平台覆盖。

## 核心功能

- **3D 场景训练**：接受 COLMAP 数据或 Nerfstudio 格式数据集，直接训练 Gaussian Splatting 模型
- **实时训练可视化**：训练过程中可交互查看场景，实时对比当前渲染与输入视角
- **场景查看器**：加载 .ply / .compressed.ply 文件，支持 URL 流式加载
- **4D 动画支持**：加载 splat 文件序列展示动态动画（如 Cap4D）
- **图像遮罩**：支持透明度图像和区域遮罩，精确控制训练区域
- **CLI 工具**：完整的命令行界面，支持 `--with-viewer` 实时调试
- **Rerun 集成**：使用 Rerun.io 进行额外的训练数据可视化

## 技术架构

| 组件 | 技术 | 作用 |
|------|------|------|
| 核心语言 | Rust | 高性能、内存安全、跨平台编译 |
| ML 框架 | Burn | Rust 原生深度学习框架，支持多后端 |
| GPU 计算 | wgpu / WebGPU | 跨 GPU 厂商的统一计算接口 |
| UI 框架 | egui | 即时模式 GUI，轻量级跨平台界面 |
| 可视化 | Rerun.io | 训练过程的额外数据可视化 |
| Web 部署 | WASM + Next.js | 浏览器端运行 3D 重建 |

**支持平台**：macOS / Windows / Linux / Android / Web（浏览器）

**支持 GPU**：Nvidia / AMD / Intel / Apple Silicon

### 关键技术亮点

1. **零 CUDA 依赖** — 通过 wgpu/WebGPU 统一接口，支持全系列 GPU
2. **单二进制文件** — 编译产出无依赖可执行文件，无需复杂环境配置
3. **浏览器训练** — 全球首个可在浏览器中直接进行 3DGS 训练的工具
4. **性能优于 gsplat** — 渲染和训练速度通常快于参考实现
5. **GPU Radix Sort** — 采用 Raph Levien 的高性能基数排序实现

## 应用场景

- 摄影测量与 3D 扫描
- VR/AR 内容创作
- 建筑与房地产数字化建模
- 文化遗产保护与数字化存档
- 游戏开发（真实场景转化为游戏素材）
- 影视特效与场景重建
- 科研教育（3D 重建教学与实验）
- 机器人视觉（环境感知可视化）

## 为什么火？Trending 原因分析

1. **填补跨平台空白** — 传统 3DGS 工具全部依赖 CUDA，Mac/AMD/移动端用户被排除在外。Brush 是第一个真正「全平台可用」的 3DGS 引擎
2. **Rust + WebGPU 技术吸引力** — 两个热门技术在 3D 重建领域的标杆级应用
3. **零门槛体验** — 在线 Web Demo，无需安装即可体验。HN 社区评价：「50 MB .ply 文件瞬间加载，漫游流畅无闪烁」
4. **Gaussian Splatting 爆发期** — 3DGS 是 2023-2025 年 CV 领域最热门技术之一，SIGGRAPH/NAB 大量产品采用
5. **Google DeepMind 背书** — 作者来自 Google DeepMind，同时也是 Burn 框架核心贡献者

## 同类项目对比

| 特性 | Brush | gsplat | Splatfacto | PostShot | 原版 Inria 3DGS |
|------|-------|--------|------------|----------|-----------------|
| 语言 | Rust | CUDA/Python | Python | 桌面应用 | CUDA/Python |
| CUDA 依赖 | **无需** | 必需 | 必需 | 必需 | 必需 |
| Mac 支持 | **原生** | ❌ | ❌ | ❌ | ❌ |
| 浏览器运行 | **WebGPU** | ❌ | ❌ | ❌ | ❌ |
| Android | **支持** | ❌ | ❌ | ❌ | ❌ |
| 训练速度 | 快（优于 gsplat） | 快 | 中等 | 良好 | 基线 |
| 开源 | Apache 2.0 | ✅ | ✅ | 商业 | ✅ |
| 上手难度 | 低（单二进制） | 中 | 高 | 低 | 高 |

**总结**：Brush 的核心竞争力在于「全平台 + 零依赖 + 浏览器可用」，这是其他所有 3DGS 工具都不具备的。

## 适合谁使用

- **Mac / AMD GPU 用户** — 唯一能在非 Nvidia GPU 上原生训练 3DGS 的工具
- **3D 艺术师** — 快速将照片转为 3D 场景，无需复杂环境搭建
- **Web 开发者** — 在网站中嵌入 3D 重建功能（WebGPU）
- **移动端开发者** — Android 端 3D 重建
- **Rust 社区开发者** — 对 Rust + ML/GPU 计算感兴趣的技术探索者
- **教育工作者** — 课堂演示 3D 重建技术
- **快速原型开发者** — 零配置快速验证 3D 重建想法

## 快速上手

### 安装

```bash
# 确保已安装 Rust 1.88+
rustup update stable

# 克隆仓库
git clone https://github.com/ArthurBrussee/brush.git
cd brush

# 构建并运行
cargo run --release
```

### 训练

```bash
# 使用 COLMAP 数据训练
brush train --data /path/to/colmap/dataset

# 训练并打开查看器
brush train --data /path/to/dataset --with-viewer
```

### 查看场景

```bash
# 本地查看 .ply 文件
brush view --path scene.ply

# Web 端查看（URL 参数加载）
# 浏览器访问: https://brush.demo?url=https://example.com/scene.ply
```

### Web 端开发

```bash
npm run dev     # 启动 Web Demo
wasm-pack build # 构建 WASM
```

### Android 构建

```bash
rustup target add aarch64-linux-android
cargo install cargo-ndk
cargo ndk -t arm64-v8a -o app/src/main/jniLibs/ build --release
./gradlew installDebug
```

## 综合评分

| 维度 | 评分 | 说明 |
|------|------|------|
| 创新性 | **9.0/10** | 跨平台 3DGS、浏览器训练、零 CUDA 依赖，多项突破 |
| 代码质量 | **8.5/10** | Rust 保证了内存安全和高性能，架构清晰 |
| 实用性 | **8.5/10** | 单二进制文件，覆盖几乎所有主流平台 |
| 文档完善度 | **7.5/10** | README 完整但缺少详细教程和 API 文档 |
| 社区活跃度 | **7.0/10** | 活跃的 GitHub Discussions，但贡献者相对较少 |

**综合评分：8.1 / 10** — 一个极具创新性的项目，在跨平台 3D 重建领域开辟了全新赛道。

## 参考链接

- [GitHub 仓库](https://github.com/ArthurBrussee/brush)
- [Web Demo (Chrome/Edge)](https://brushdemo.vercel.app/)
- [Radiance Fields 评测](https://radiancefields.com/gaussian-splatting-in-browser-brush)
- [Hacker News 讨论](https://news.ycombinator.com/item?id=41938831)
- [Reddit r/rust 讨论](https://www.reddit.com/r/rust/comments/1gbg5i1/brush_gaussian_splatting_using_burn_wgpu_egui_and/)
- [Burn 框架](https://burn.dev/)

---

*分析日期：2026-05-14 | GitHub Trending 深度分析*