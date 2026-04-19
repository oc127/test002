---
name: comic-to-video
description: 将漫画/分镜/manga 转为视频 prompt。当用户需要"漫画转视频/分镜动态化/manga animation/comic panel animation/storyboard to video/漫画动起来/分镜脚本渲染"时自动调用。专注保持分格构图 → 镜头转化、对话气泡 → 字幕动画、静态画格 → 运镜设计的翻译过程。
---

# 漫画转视频 (Comic-to-Video / Panel Animation)

漫画天生就是分镜。**每一格已经是导演构好的镜头**——你的工作不是重新设计，而是让这些静态镜头"活过来"。

## 调用时机

**强触发词**：
- 漫画转视频 / 漫画动态化 / 分镜渲染
- manga animation / comic panel / storyboard to video
- 让漫画动起来 / panel animation
- 分镜脚本 / webtoon / 条漫

**典型请求**：
- "把这组漫画分镜做成 8 秒视频"
- "manga 风格的分格动画"
- "让这个 storyboard 活过来"

---

## 漫画 → 视频的 3 种翻译模式

### 模式 1: Panel-by-Panel（逐格动画）
每一格漫画 = 一个独立镜头，按顺序剪辑。
- **最稳**，AI 容易理解
- 每格 1-2 秒，4-5 格 = 8 秒
- **Prompt**: `Sequential panel animation — each comic panel becomes a separate shot, cut in reading order`

### 模式 2: Camera-Over-Page（镜头漫游）
相机在整页漫画上平移/缩放，像在"读"漫画。
- 适合大场景全页图
- 镜头从左上到右下慢推
- **Prompt**: `Camera slowly pans across a comic book page, revealing panels in reading order, Ken Burns effect on illustrated artwork`

### 模式 3: Full Animation（完全动态化）
角色从画格中"走出来"，完全动画化。
- 最难，AI 容易崩
- 适合单个角色特写格
- **Prompt**: `Character breaks free from comic panel borders, transitioning from illustrated 2D to animated motion`

---

## 漫画元素 → 视频元素映射

| 漫画元素 | 视频翻译 | Prompt 写法 |
|---------|---------|------------|
| 画格边框 | 转场分割线 | `panel borders serve as wipe transitions` |
| 对话气泡 | 字幕弹出 | `speech bubble text appears as animated subtitle overlay` |
| 速度线 | 运动模糊 | `speed lines translate to motion blur on the moving subject` |
| 音效文字（BOOM!） | 文字动画 | `onomatopoeia text animates with dynamic scale and rotation` |
| 分格大小 | 镜头时长 | 大格 = 长镜头，小格 = 快切 |
| 阅读顺序 | 剪辑顺序 | 右→左（manga）或左→右（Western） |

---

## 分镜时间分配

| 格数 | 每格时长 | 总时长 | 节奏 |
|------|---------|-------|------|
| 3 格 | 2.5s | 8s | 慢节奏，每格有呼吸空间 |
| 4 格 | 2s | 8s | 标准节奏 |
| 5 格 | 1.5s | 8s | 快节奏，动作感 |
| 6+ 格 | 1s | 8s | 极快，蒙太奇 |

---

## 阅读方向

| 类型 | 阅读方向 | 镜头移动 |
|------|---------|---------|
| 日本 Manga | 右→左，上→下 | camera pans right-to-left |
| 西方 Comic | 左→右，上→下 | camera pans left-to-right |
| 韩国 Webtoon | 上→下（竖屏长条） | camera scrolls vertically downward |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Comic panel animation sequence. Camera reveals four illustrated
manga-style panels in reading order. Each panel transitions with
a dynamic wipe effect along the panel border. Panel 1: close-up
of a character's determined eyes. Panel 2: wide shot of a
futuristic cityscape. Panel 3: the character leaps between
buildings, speed lines creating motion blur. Panel 4: landing
pose with dramatic low angle. Illustrated 2D art style with
bold ink outlines, cel-shaded coloring. Each panel holds for
2 seconds. Smooth transitions between panels.
```

### Kling（中文）
```
漫画分格动画。相机依次展示四格日漫风格画面，每格之间用画格
边框作为擦除转场。第一格：角色坚定眼神特写。第二格：未来都市
全景。第三格：角色在建筑间跳跃，速度线制造运动模糊。第四格：
落地英雄姿势，低角度仰拍。2D 插画风格，粗墨线条，赛璐璐上色。
每格停留 2 秒。
```

### Runway Gen-3
```
Animated comic book sequence. Four manga panels revealed
sequentially with wipe transitions along panel borders. Panel 1:
character eye close-up. Panel 2: cityscape wide shot. Panel 3:
character leaping with speed lines. Panel 4: hero landing low
angle. Bold ink outlines, cel-shaded coloring. 2 seconds per panel.
```

---

## 避坑

1. ❌ **一次塞太多格** → 8 秒最多 5 格，多了全糊
2. ❌ **忽略阅读方向** → manga 和 comic 方向相反，搞错很出戏
3. ❌ **让角色做复杂动作** → AI 对"从静态画变成全动画"很弱，保持简单运动
4. ❌ **丢掉漫画感** → 保留墨线、速度线、分格——这些是漫画的灵魂

## 输出规范

```
## 📖 [标题]（[类型]漫画→视频）

**翻译模式**: [Panel-by-Panel / Camera-Over-Page / Full Animation]
**阅读方向**: [右→左 Manga / 左→右 Western / 上→下 Webtoon]
**格数**: [X 格] × [每格 Xs] = [总 Xs]

**分镜**
[Panel 1 · 0-Xs] ...
[Panel 2 · X-Ys] ...

**Prompt**（按模型）
```

## 质量自检

- [ ] 翻译模式明确（3 选 1）
- [ ] 阅读方向正确（manga vs comic vs webtoon）
- [ ] 每格时长合理（1-3 秒）
- [ ] 保留漫画视觉元素（墨线/速度线/分格）
- [ ] Higgsfield prompt 不含 banned words
