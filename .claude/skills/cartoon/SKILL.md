---
name: cartoon
description: 生成 2D 卡通风格视频 prompt。当用户需要"卡通/Pixar/Disney/动画片/Cartoon Network/Rick and Morty/Arcane/扁平化动画/手绘动画/cartoon/cel-shaded Western/Looney Tunes/动画短片/儿童动画"时自动调用。覆盖 4 大西方动画流派（Pixar 3D/扁平化/成人动画/手绘经典），包含迪士尼 12 原则的 prompt 翻译、卡通物理学、色彩面积理论。区别于 anime-mv（日系动漫美学）。
---

# 2D 卡通风格 (Cartoon / Western Animation)

卡通 ≠ 动漫。**卡通是西方动画的视觉语言**：夸张变形、卡通物理、简化构图、色块思维。跟日系赛璐璐动画完全不同的美学体系。

## 调用时机

**强触发词**：
- 卡通 / 动画片 / 西方动画
- Pixar / Disney / 迪士尼 / 皮克斯
- Cartoon Network / Adventure Time / Steven Universe
- Rick and Morty / Arcane / 成人动画
- Looney Tunes / Tom and Jerry / 手绘
- 扁平化 / flat animation / cel-shaded Western

**典型请求**：
- "做一个 Pixar 风格的角色动画"
- "Rick and Morty 那种荒诞科幻卡通"
- "Looney Tunes 物理喜剧的短片"
- "Arcane 暗黑手绘风的战斗"

**与 anime-mv 的边界**：
| | cartoon | anime-mv |
|---|---|---|
| **美学根源** | 西方（美国/欧洲） | 日系（日本） |
| **线条** | 粗、圆润、简化 | 精细、有棱角 |
| **色彩** | 大色块、高饱和 | 渐变、光影层次 |
| **运动** | 夸张变形（squash & stretch） | 有限动画 + 定格 |
| **表情** | 极端夸张 | 微妙内敛 |
| **物理** | 卡通物理（违反牛顿） | 相对写实（或极度夸张后回弹） |

---

## 4 大卡通流派

### 流派 1: Pixar / Disney 3D 风

**代表作**：《玩具总动员》《超人总动员》《冰雪奇缘》《寻梦环游记》

**视觉特征**：
- **圆润角色**：大眼睛、圆脸、表情极度丰富
- **Subsurface Scattering**：皮肤有透光感
- **温暖配色**：金色主调、柔和阴影
- **材质细腻**：布料纹理、毛发每根可见
- **光照电影级**：三点布光 + 环境光

**Prompt 关键词**：
```
Pixar-style 3D animation, rounded character design, expressive
oversized eyes, subsurface scattering on skin, warm golden
lighting, detailed fabric textures, soft ambient shadows,
Toy Story / Coco aesthetic
```

### 流派 2: Cartoon Network 扁平风

**代表作**：《探险时光》《OK K.O.!》《Steven Universe》《飞天小女警》

**视觉特征**：
- **粗线条**：统一粗细的黑色轮廓线
- **纯色填充**：极少渐变，大面积单色
- **几何简化**：人物由圆形/方形/三角形组成
- **有限动画**：关键帧间距大，动作干脆
- **高对比配色**：粉蓝黄绿等鲜艳色块

**Prompt 关键词**：
```
Flat 2D cartoon style, bold uniform black outlines, solid color
fills without gradients, geometrically simplified character
design, high contrast vivid color palette, Adventure Time /
Steven Universe aesthetic
```

### 流派 3: 成人动画

**代表作**：《Rick and Morty》《Arcane》《恶魔城》《辛普森》

#### 3a. 荒诞科幻（Rick and Morty 型）
- 简化画风 + 荒诞设计 + 大量 sci-fi 元素
- 怪异生物、传送门、多维宇宙
- **Prompt**: `Adult cartoon with simplified art style, absurdist sci-fi elements, portal effects, bizarre alien creatures, Rick and Morty aesthetic`

#### 3b. 暗黑手绘混合（Arcane 型）
- 手绘笔触 + 3D 混合 + 暗色调
- 油画质感 + 粒子特效
- **Prompt**: `Dark painterly animation style mixing hand-drawn textures with 3D elements, oil-paint brush strokes visible, moody atmospheric lighting, Arcane / Castlevania aesthetic`

### 流派 4: 手绘经典

**代表作**：《猫和老鼠》《兔八哥》《大力水手》

**视觉特征**：
- **水彩/铅笔背景** + 赛璐璐角色
- **物理喜剧**：被砸成纸片弹回来
- **表情瞬变**：0.1 秒内切换情绪
- **音效驱动**：视觉紧跟音效节奏

**Prompt 关键词**：
```
Classic hand-drawn animation, watercolor painted backgrounds,
cel-animated characters, slapstick cartoon physics, exaggerated
facial expressions, Looney Tunes / Tom and Jerry aesthetic
```

---

## 迪士尼 12 原则 → Prompt 翻译

动画黄金法则如何变成 AI 能理解的 prompt 语言：

### 1. Squash & Stretch（挤压与拉伸）
角色运动时形体会变形——跳起时拉长，落地时压扁。
- **Prompt**: `Character body deforms with squash-and-stretch — elongating during leaps and compressing on landing`

### 2. Anticipation（预备动作）
任何大动作前都有一个**反方向的小动作**。
- **Prompt**: `Clear anticipation before each major action — brief reverse motion building energy`

### 3. Exaggeration（夸张）
所有动作、表情、反应都比现实**大 3 倍**。
- **Prompt**: `Highly exaggerated motion and expressions, 3x larger than realistic`

### 4. Staging（舞台调度）
画面一眼能看清"谁在做什么"，不需要猜。
- **Prompt**: `Clear staging with strong silhouette readability, action readable in a single glance`

### 5. Arcs（弧线运动）
自然运动走弧线，不走直线。
- **Prompt**: `All character movement follows natural arcs, never straight-line motion`

### 6. Appeal（吸引力）
角色设计让人想看——不一定要"好看"，但要"有趣"。
- **Prompt**: `Appealing character design with distinctive silhouette and memorable proportions`

---

## 卡通物理学

如何用 prompt 描述"违反物理但视觉合理"的运动：

| 经典效果 | Prompt 描述 |
|---------|------------|
| 跑出悬崖不立刻掉 | `character runs past the cliff edge, pauses mid-air in realization, then gravity takes effect` |
| 被砸成纸片弹回来 | `character flattens on contact then pops back to normal shape with elastic bounce` |
| 追逐时腿变成旋风 | `legs spin into a circular blur during rapid running, classic cartoon speed effect` |
| 眼睛弹出眼眶 | `eyes pop out of head in surprise, connected by stretchy stalks` |
| 碰墙留下轮廓印记 | `character-shaped impression left in the wall after contact` |
| 怒火从头顶冒出 | `visible frustration with warm amber energy rising from the character's head` |

---

## 色彩面积理论（60-30-10 法则）

卡通用色必须**大面积统一**，不像电影那样靠光影变化：

```
60% — 主色（背景 + 最大面积元素）
30% — 辅色（角色主体 / 次要元素）
10% — 点睛色（眼睛 / 道具 / 特效高光）
```

### 流派 × 配色方案

| 流派 | 60% 主色 | 30% 辅色 | 10% 点睛 |
|------|---------|---------|---------|
| Pixar | 暖金 / 天蓝 | 角色肤色 | 红色配饰 |
| CN 扁平 | 鲜粉 / 亮绿 | 深紫 / 靛蓝 | 黄色高光 |
| 成人动画 | 深灰 / 墨绿 | 霓虹青 | 品红/酸绿 |
| 手绘经典 | 水彩蓝天 | 棕色地面 | 角色红色鼻子 |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Pixar-style 3D cartoon animation. A round-faced character with
oversized expressive eyes walks through a colorful fantasy market.
Warm golden lighting with subsurface scattering on skin. The
character's body stretches slightly with each bouncy step
(squash-and-stretch principle). Soft ambient shadows, detailed
fabric textures on clothing. Background painted in warm watercolor
tones. Camera follows with a gentle tracking movement. Coco /
Inside Out aesthetic. Vertical 9:16.
```

### Kling（中文）
```
皮克斯风格 3D 卡通动画。一个圆脸大眼睛的角色走过彩色奇幻
集市，每一步都有弹跳感的挤压拉伸。温暖金色灯光照亮角色，
皮肤有通透的次表面散射效果。柔和阴影，服装布料纹理精细。
背景是温暖的水彩色调。相机轻柔跟拍。寻梦环游记/头脑特工队
美学。竖屏 9:16。
```

### Runway Gen-3
```
Pixar 3D animation style. Round-faced character with large
expressive eyes bouncing through a fantasy market. Squash and
stretch on body with each step. Warm golden key light, subsurface
scattering, soft shadows. Watercolor-toned background. Gentle
tracking camera. Coco / Inside Out aesthetic.
```

---

## 避坑

1. ❌ **混用卡通和动漫风格词** — 不要同时写 "Pixar" 和 "Makoto Shinkai"，结果会四不像
2. ❌ **写实光影用在扁平风** — Cartoon Network 风格不需要 "volumetric rays"，要 "flat lighting"
3. ❌ **忽略 squash & stretch** — 没有变形的卡通角色看起来像木偶
4. ❌ **配色太杂** — 遵守 60-30-10，超过 4 种主要颜色就会乱
5. ❌ **描述太多细节** — 卡通的美在于简化，prompt 也要简洁

## 输出规范

```
## 🎨 [标题]（[流派]卡通）

**流派**: [Pixar 3D / CN 扁平 / 成人动画 / 手绘经典]
**配色**: 60% [主色] + 30% [辅色] + 10% [点睛]
**动画原则**: [选 2-3 个迪士尼原则]

**分镜**
[0-Xs] ...

**Prompt**（按模型）

— Higgsfield（⚠️ 已过 content-filter）—
<prompt>

— Kling —
<中文 prompt>
```

## 质量自检

- [ ] 流派明确且只选一个（不混用日系和西方）
- [ ] 配色遵守 60-30-10
- [ ] 至少使用 2 个迪士尼动画原则
- [ ] 角色设计有明确轮廓可读性
- [ ] Higgsfield prompt 不含 banned words
