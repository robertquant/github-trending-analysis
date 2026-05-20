# Pascal Editor — 深度分析报告

> **pascalorg/editor** | GitHub Trending 2026-05-20 | MIT License | TypeScript

---

## 项目简介

Pascal Editor 是一个完全运行在浏览器中的 **3D 建筑编辑器**，基于 React Three Fiber 和 WebGPU 构建。它允许用户创建、编辑和分享 3D 建筑模型，是 AutoCAD、Revit 等传统建筑软件的轻量级、零安装替代方案。

### 核心功能

- **3D 建筑建模** — 墙体、楼板、天花板、屋顶等建筑元素的创建和编辑
- **门窗放置** — 通过 CSG 布尔运算自动在墙体上切割门窗洞口
- **多楼层管理** — 支持堆叠/展开/单独查看等多种视图模式
- **区域划分** — 建筑内部空间的分区管理
- **3D 扫描参考** — 导入 3D 扫描数据作为设计参考
- **项目分享** — 在线创建和分享建筑项目
- **撤销/重做** — 50 步历史记录
- **数据持久化** — 自动保存到 IndexedDB

---

## 技术架构

### 技术栈

React 19 · Next.js 16 · Three.js (WebGPU) · React Three Fiber · Zustand · Zod · Zundo · three-bvh-csg · Turborepo · Bun

### Monorepo 结构

```
editor-v2/
├── apps/
│   └── editor/          # Next.js 应用（UI、工具、编辑器行为）
├── packages/
│   ├── core/            # 数据模式、状态管理、几何生成系统
│   └── viewer/          # 3D 渲染组件
```

| 包 | 职责 |
|---|---|
| @pascal-app/core | 节点模式、场景状态 (Zustand)、系统（几何生成）、空间查询、事件总线 |
| @pascal-app/viewer | 通过 React Three Fiber 进行 3D 渲染，默认相机/控件，后处理 |
| apps/editor | UI 组件、工具、自定义行为、编辑器专用系统 |

### 核心架构亮点

1. **节点系统** — 所有建筑元素以扁平字典存储（Site → Building → Level → Wall/Slab/Zone...），通过 parentId 构建层级
2. **脏标记机制** — 节点变更标记 dirty，系统仅在渲染帧中处理脏节点，高性能
3. **场景注册表** — 节点 ID 到 Three.js 对象的快速映射，无需遍历场景图
4. **CSG 布尔运算** — three-bvh-csg 在墙体上精确切割门窗洞口
5. **空间网格管理器** — 碰撞检测和放置验证
6. **三层状态管理** — useScene / useViewer / useEditor 各自独立

### 数据流

```
用户操作 → Tool Handler → useScene.createNode/updateNode
  → 节点更新 & 标记 dirty → React 重渲染 NodeRenderer
  → useRegistry 注册 3D 对象 → System 检测 dirty 节点
  → 更新几何体 → 清除 dirty 标记
```

---

## 应用场景

- **建筑设计快速原型** — 无需安装重型软件，浏览器中快速创建概念模型
- **房地产展示** — 在线 3D 楼宇模型用于展示和营销
- **室内设计规划** — 房间布局、家具摆放、区域划分
- **建筑教学** — 建筑可视化教学工具
- **DIY 装修** — 家庭用户规划装修方案
- **协作设计** — 在线分享功能实现团队协作

---

## 为什么火（Trending 原因）

1. **填补市场空白** — 浏览器端 3D 建筑编辑器几乎没有高质量开源方案
2. **技术前沿** — WebGPU + React Three Fiber，代表 Web 3D 最新方向
3. **架构优秀** — monorepo 分包、脏标记系统、CSG 运算等展现了极高工程质量
4. **零门槛** — 打开浏览器即可使用，无需安装
5. **社交传播** — Facebook、Instagram、YouTube、Threads 广泛传播
6. **开源免费** — MIT 协议，对比商业软件数千美元年费
7. **活跃更新** — 2026年4月发布 v3.51.0，持续迭代

---

## 同类项目对比

| 项目 | 运行环境 | 渲染技术 | 开源 | 专注建筑 |
|---|---|---|---|---|
| **Pascal Editor** | 浏览器 | WebGPU + R3F | ✅ MIT | ✅ |
| AutoCAD / Revit | 桌面端 | DirectX | ❌ 商业 | ✅ |
| Three.js Editor | 浏览器 | WebGL | ✅ MIT | ❌ 通用3D |
| Blender | 桌面端 | OpenGL/Vulkan | ✅ GPL | ❌ 通用3D |
| Sweet Home 3D | 桌面/浏览器 | Java/Canvas | ✅ GPL | ✅ 室内设计 |

Pascal Editor 在"浏览器端 + 专业建筑建模 + 现代渲染"交叉领域几乎没有直接竞品。

---

## 适合谁使用

- **建筑师和设计师** — 快速创建概念模型或展示设计方案
- **前端/3D 开发者** — 学习 R3F、WebGPU、CSG 的优秀参考项目
- **房地产从业者** — 快速生成楼盘 3D 可视化模型
- **建筑专业学生** — 无需昂贵许可证即可练习建筑建模
- **室内设计师** — 规划空间布局和家具摆放
- **SaaS 创业者** — 可基于此构建商业化在线建筑设计平台

---

## 快速上手

### 前提条件

- 安装 [Bun](https://bun.sh) 运行时
- 支持 WebGPU 的浏览器（Chrome 113+）

### 步骤

```bash
# 1. 克隆仓库
git clone https://github.com/pascalorg/editor.git
cd editor

# 2. 安装依赖
bun install

# 3. 启动开发服务器
bun dev
# 自动构建 core 和 viewer 包，启动 Next.js 编辑器
# 打开 http://localhost:3000

# 4. 生产构建
turbo build
```

---

## 综合评分

| 维度 | 评分 | 说明 |
|---|---|---|
| 创新性 | ⭐ 9.0/10 | 浏览器端建筑编辑器+WebGPU，创新性极高 |
| 代码质量 | ⭐ 9.5/10 | monorepo 架构清晰，脏标记系统设计精巧 |
| 实用性 | ⭐ 8.5/10 | 功能完善但仍在快速迭代中 |
| 文档完善度 | ⭐ 9.0/10 | README 详尽，架构说明清晰 |
| 社区活跃度 | ⭐ 7.5/10 | 项目较新，社区在成长中 |

### 总评：8.7 / 10 — 优秀开源项目，强烈推荐关注

---

*分析日期：2026-05-20 | 来源：[GitHub](https://github.com/pascalorg/editor) | [Trendshift](https://trendshift.io/repositories/23831) | [HelloGitHub](https://hellogithub.com/en/repository/pascalorg/editor)*
