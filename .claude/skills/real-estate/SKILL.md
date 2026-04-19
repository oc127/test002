---
name: real-estate
description: 生成房产/建筑/室内设计视频 prompt。当用户需要"房产视频/楼盘宣传/property tour/室内设计展示/建筑可视化/architecture video/样板间/house tour/apartment walkthrough/酒店展示/空间展示/indoor tour"时自动调用。专注空间感的营造——广角穿越、自然光窗景、材质质感、生活方式暗示。
---

# 房产与建筑 (Real Estate / Architecture Video)

房产视频卖的不是房子，卖的是**"住在这里的感觉"**。每一个镜头都要让观众想象自己走进去。

## 调用时机

**强触发词**：
- 房产视频 / 楼盘宣传 / 样板间
- property tour / house tour / apartment walkthrough
- 室内设计 / 建筑可视化 / architecture
- 酒店展示 / 空间展示 / interior design
- 售楼处 / 开盘 / 楼盘航拍

**典型请求**：
- "做一个豪宅 walkthrough 视频"
- "样板间的 cinematic 展示"
- "新楼盘的航拍宣传片"
- "酒店套房的空间展示"

---

## 4 种房产视频类型

### 类型 1: Walkthrough（穿越漫游）
相机像人一样"走进"空间，从门口到客厅到卧室。
- 稳定器慢速推进
- 门框/走廊作为自然转场
- 跟着光线走（从暗到亮）
- **Prompt**: `Smooth cinematic walkthrough, camera glides through the front door into an open-plan living space, moving from dim entryway into bright natural light, stabilized low tracking shot at waist height`

### 类型 2: Reveal（空间揭示）
先看到局部（一扇窗/一个角落），然后镜头拉开揭示整个空间。
- 从特写到全景的单一运镜
- 制造"哇"的瞬间
- **Prompt**: `Dramatic space reveal — camera starts tight on a detail (window view / fireplace / texture), then slowly pulls back to reveal the entire room in all its grandeur`

### 类型 3: Aerial（航拍）
鸟瞰建筑外观 + 周边环境。
- 无人机视角 / 高空推进
- 展示位置、环境、建筑轮廓
- 适合楼盘/别墅/度假村
- **Prompt**: `Aerial drone shot, camera descends from high altitude toward the property, revealing architecture and surrounding landscape, golden hour lighting, smooth cinematic descent`

### 类型 4: Lifestyle（生活方式）
不只是展示空间，展示"住在这里的生活"。
- 有人在空间中活动（煮咖啡、看书、窗边站立）
- 自然光 + 真实生活道具
- **Prompt**: `Lifestyle real estate scene, morning light flooding through floor-to-ceiling windows, a person in casual clothing enjoying coffee while looking out at the city view, warm lived-in atmosphere`

---

## 空间感营造技巧

| 技巧 | 效果 | Prompt 描述 |
|------|------|------------|
| **广角镜头** | 空间显大 | `wide angle lens (16-24mm) emphasizing spaciousness` |
| **引导线** | 视觉纵深 | `corridor / hallway creating leading lines toward the bright end` |
| **框中框** | 层次感 | `doorframe or archway framing the room beyond` |
| **窗景** | 内外对比 | `interior framing with exterior view through large windows` |
| **低机位** | 天花板显高 | `low camera angle at waist height, ceiling appears taller` |
| **慢推进** | 沉浸感 | `slow steady forward movement, 0.5m/s walking pace` |

---

## 光照方案

| 光照类型 | 效果 | 适用场景 |
|---------|------|---------|
| **清晨窗光** | 温暖、希望感 | 卧室、客厅 |
| **正午顶光** | 空间通透 | 开放式厨房、大堂 |
| **黄金时刻** | 高级温暖 | 阳台、露台、外立面 |
| **蓝调时刻** | 高端冷静 | 城市公寓夜景 |
| **灯光组合** | 生活感 | 夜间室内（台灯+壁灯） |

---

## 材质展示

高端房产视频必须展示**材质的触感**：

| 材质 | 视觉强调 | Prompt |
|------|---------|--------|
| 大理石 | 纹理 + 反光 | `polished marble surface with visible veining, reflecting ambient light` |
| 实木 | 纹理 + 温度感 | `warm wood grain texture, natural oak tones` |
| 玻璃 | 透光 + 反射 | `floor-to-ceiling glass reflecting sky and allowing natural light to flood in` |
| 黄铜 | 光泽 + 高级 | `brushed brass fixtures catching warm light` |
| 混凝土 | 粗糙 + 工业 | `raw concrete wall with subtle texture, industrial-modern aesthetic` |
| 布艺 | 柔软 + 层次 | `soft linen upholstery with natural drape and texture` |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Cinematic real estate walkthrough. Camera glides smoothly through
the front entrance of a modern luxury apartment, transitioning
from a dim hallway into a bright open-plan living area flooded
with natural morning light through floor-to-ceiling windows.
Wide angle lens emphasizing spaciousness. Polished marble floors
reflect the warm sunlight. The camera moves at a slow walking
pace, passing a kitchen island with brushed brass fixtures,
then reveals a panoramic city view through the windows.
Stabilized low tracking shot at waist height. Warm natural
color palette with soft shadows.
```

### Kling（中文）
```
电影级房产穿越视频。相机从现代豪华公寓的前门平滑滑入，
从暗色走廊过渡到被落地窗自然晨光照亮的开放式客厅。
广角镜头强调空间感。抛光大理石地面反射温暖阳光。相机以
缓慢步行速度移动，经过带黄铜配件的厨房岛台，然后揭示
落地窗外的城市全景。稳定器低机位腰部高度跟拍。温暖自然
色调，柔和阴影。
```

### Runway Gen-3
```
Real estate walkthrough. Camera glides from dim entrance into
bright open living space with floor-to-ceiling windows. Wide
angle, polished marble floors reflecting sunlight. Slow walking
pace past kitchen island with brass fixtures. Reveals panoramic
city view. Stabilized low tracking shot. Warm natural palette.
```

---

## 避坑

1. ❌ **镜头太快** → 房产视频要慢，让观众"感受"空间，推进速度不超过步行速度
2. ❌ **没有自然光** → 自然光是房产的最大卖点，必须展示窗光
3. ❌ **全部广角** → 广角展示空间，但特写展示材质，要有切换
4. ❌ **空间空无一人** → 适当有生活道具（书/咖啡杯/植物）增加温度
5. ❌ **忽略窗外景色** → 景观是溢价最高的元素，必须给

## 输出规范

```
## 🏠 [项目名/标题]（[类型]房产视频）

**视频类型**: [Walkthrough / Reveal / Aerial / Lifestyle]
**空间**: [公寓/别墅/酒店/商业]
**光照**: [清晨窗光/黄金时刻/蓝调/灯光组合]
**核心材质**: [大理石/实木/玻璃/黄铜]

**Prompt**（按模型）
```

## 质量自检

- [ ] 镜头速度慢（步行或更慢）
- [ ] 有自然光展示（不是纯人工照明）
- [ ] 广角展示空间 + 特写展示材质
- [ ] 有窗外景观展示
- [ ] 空间有生活感（不是空荡荡的）
- [ ] Higgsfield prompt 不含 banned words
