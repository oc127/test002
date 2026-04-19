---
name: motion-design-ad
description: 生成 SaaS/科技产品 Motion Design 广告视频 prompt。当用户需要"SaaS 广告/App 演示/UI 动画/软件产品视频/科技产品广告/landing page 视频/product demo/tech ad/motion graphics/界面动效/数据可视化动画"时自动调用。专注 UI mockup 动态展示、数据流动可视化、科技感粒子和光线，区别于 ecommerce-video（实物产品）。
---

# 科技产品 Motion Design 广告 (Motion Design Ad / Tech Product Video)

科技产品不能"拿在手里转"——你卖的是**屏幕里的体验**。Motion Design 用动效让抽象的 SaaS 功能变成可感知的视觉体验。

## 调用时机

**强触发词**：
- SaaS 广告 / App 演示 / 科技产品视频
- UI 动画 / 界面动效 / product demo
- motion graphics / motion design / tech ad
- landing page 视频 / 数据可视化
- 软件功能展示 / dashboard 动画

**典型请求**：
- "做一个 SaaS 产品 landing page 的英雄视频"
- "App UI 功能演示动画"
- "AI 产品的数据流可视化广告"

**与 ecommerce-video 的边界**：
| | motion-design-ad | ecommerce-video |
|---|---|---|
| **产品类型** | 虚拟（SaaS/App/API） | 实物（CPG/服装/美妆） |
| **展示方式** | UI mockup + 动效 | 实物拍摄 + 使用场景 |
| **核心卖点** | 功能/效率/数据 | 外观/材质/体验 |
| **视觉语言** | 几何线条/粒子/渐变 | 光影/材质/色彩 |

---

## 4 种科技产品视频类型

### 类型 1: UI Showcase（界面展示）
展示 App 或 Web 界面的功能和交互流程。
- 设备 mockup 浮在空间中（isometric 或 3/4 角度）
- 光标 / 手指在界面上操作
- UI 元素弹出、滑入、变形
- **Prompt**: `Floating device mockup in 3/4 perspective, UI elements animating smoothly — buttons pressing, panels sliding, data populating in real-time`

### 类型 2: Data Flow（数据流动）
用可视化动画展示"数据怎么流动"、"AI 怎么处理"。
- 抽象粒子从 A 点流向 B 点
- 节点网络亮起、信息传递
- 数字/图表实时变化
- **Prompt**: `Abstract data visualization, luminous particles flowing between connected nodes, real-time chart animations, neural network-style pathways illuminating sequentially`

### 类型 3: Feature Highlight（功能高亮）
聚焦一个核心功能，用动效放大它的价值。
- 界面某个区域 zoom in
- 功能触发 → 视觉反馈 → 结果
- 前后对比（Before/After split）
- **Prompt**: `Camera zooms into a specific UI element, the feature activates with a satisfying visual feedback animation, split-screen before/after comparison`

### 类型 4: Brand Tech Reel（品牌科技感）
不展示具体功能，只传达"科技感"和"未来感"。
- 抽象几何 + 品牌色
- 粒子/光线/网格
- 文字叠加品牌 slogan
- **Prompt**: `Abstract tech brand reel, geometric shapes morphing with brand colors, luminous particle systems, grid lines extending to infinity, bold text overlay with brand tagline`

---

## 科技视觉元素词典

| 元素 | Prompt 描述 | 适用场景 |
|------|------------|---------|
| 浮动设备 | `floating device mockup in isometric view` | UI Showcase |
| 粒子流 | `luminous particle stream flowing along data pathways` | Data Flow |
| 网格地面 | `infinite grid floor extending to horizon` | Brand Reel |
| 全息 UI | `holographic UI panels floating in 3D space` | Feature Demo |
| 渐变光晕 | `soft gradient glow behind device, brand-colored halo` | All |
| 连线动画 | `animated connection lines between nodes, pulsing with data` | Data Flow |
| 玻璃质感 | `glassmorphism UI elements with frosted transparency` | UI Showcase |
| 数据雨 | `cascading data streams, matrix-style digital rain in brand colors` | Brand Reel |

---

## 科技配色方案

| 品牌调性 | 主色 | 辅色 | 高光 |
|---------|------|------|------|
| **专业稳重** | 深蓝 #1a1a2e | 灰白 #e0e0e0 | 青蓝 #00d4ff |
| **活力创新** | 紫色 #6c5ce7 | 粉色 #fd79a8 | 白色 #ffffff |
| **AI/数据** | 深灰 #0d1117 | 绿色 #00ff88 | 青色 #00ffff |
| **金融科技** | 黑色 #000000 | 金色 #ffd700 | 白色 #ffffff |
| **健康科技** | 白色 #ffffff | 薄荷绿 #00b894 | 珊瑚 #ff7675 |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Motion design tech product showcase. A sleek smartphone mockup
floats in isometric view against a deep navy gradient background.
UI elements animate smoothly — cards slide in from the right,
a progress bar fills with a satisfying glow, data charts populate
in real-time. Luminous particle trails connect the device to
floating data nodes. Soft brand-colored halo radiates behind the
device. Camera slowly orbits the mockup. Glassmorphism frosted
panels. Clean sans-serif typography. Smooth 60fps motion design
aesthetic.
```

### Kling（中文）
```
科技产品 Motion Design 展示。一部精致的手机 mockup 以等距视角
漂浮在深蓝渐变背景中。UI 元素流畅动画——卡片从右侧滑入，
进度条发光填充，数据图表实时生成。发光粒子轨迹连接设备和
浮动数据节点。设备后方散发柔和的品牌色光晕。相机缓慢环绕。
磨砂玻璃质感面板。干净无衬线字体。60fps 流畅动效美学。
```

### Runway Gen-3
```
SaaS product motion design. Floating smartphone mockup in
isometric view, deep navy gradient background. UI elements
animate — cards sliding, charts populating, progress bar
filling with glow. Luminous particle trails between device
and data nodes. Brand-colored halo behind device. Slow orbit
camera. Glassmorphism panels. Clean typography. 60fps motion.
```

---

## 避坑

1. ❌ **展示太多功能** → 一条视频只讲 1 个核心功能/价值，多了记不住
2. ❌ **真实 UI 截图直接用** → AI 无法精确渲染真实 UI，用"概念化 mockup"更稳
3. ❌ **暗色背景+暗色设备** → 设备看不见，确保设备和背景有对比度
4. ❌ **过度粒子效果** → 粒子一多就喧宾夺主，产品反而被淹没

## 输出规范

```
## 💻 [产品名/标题]（[类型]科技广告）

**视频类型**: [UI Showcase / Data Flow / Feature Highlight / Brand Tech Reel]
**配色方案**: [主色] + [辅色] + [高光]
**设备**: [Phone / Laptop / Tablet / Abstract]

**分镜**
[0-Xs] ...

**Prompt**（按模型）
```

## 质量自检

- [ ] 视频类型明确（4 选 1）
- [ ] 产品/功能清晰可见（不被特效淹没）
- [ ] 配色统一（不超过 3 色 + 白/黑）
- [ ] 动效流畅（描述了 smooth / 60fps / easing）
- [ ] Higgsfield prompt 不含 banned words
