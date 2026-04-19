---
name: brand-story
description: 生成品牌叙事视频 prompt。当用户需要"品牌故事/品牌片/创始人故事/品牌宣传/origin story/brand film/品牌纪录片/企业形象片/testimonial/幕后纪实/behind the scenes/品牌价值观/使命宣言/企业宣传片"时自动调用。专注情感信任+转化，区别于 cinematic-video（艺术感染力）。覆盖 4 种品牌叙事模板、纪录片手持语言、品牌价值观视觉化。
---

# 品牌叙事 (Brand Story / Brand Film)

品牌视频的目标不是"让人说好看"，而是**"让人信你"**。一条好的品牌视频看完后，观众会觉得"这个品牌懂我"。

## 调用时机

**强触发词**：
- 品牌故事 / 品牌片 / 品牌宣传 / 企业形象片
- 创始人故事 / origin story
- brand film / brand story / brand narrative
- testimonial / 用户证言 / 客户评价视频
- 幕后纪实 / behind the scenes / BTS
- 使命宣言 / 品牌价值观 / 企业文化

**典型请求**：
- "帮我做一个品牌创始人故事的视频"
- "我们需要一条讲品牌使命的 30 秒视频"
- "客户证言式的产品推荐视频"
- "工厂幕后纪实短片"

**与 cinematic-video 的边界**：
| | brand-story | cinematic-video |
|---|---|---|
| **目标** | 建立信任 → 转化 | 艺术感染力 |
| **观众角色** | 潜在客户 / 投资人 | 观赏者 |
| **核心情绪** | "我信你" | "好震撼" |
| **光照偏好** | 自然光 / 窗光 | 布光设计 |
| **运镜** | 手持呼吸感 | 稳定器精确运镜 |
| **剪辑** | 真实节奏、保留停顿 | 精确节奏控制 |

---

## 4 种品牌叙事模板

### 模板 1: Origin（创始人故事）
> "为什么做这件事"

**结构**：个人经历 → 发现问题 → 决心解决 → 成果 → CTA

**视觉语言**：
- 创始人面部特写（建立信任）
- 手持轻微晃动（真实感）
- 暖色窗光（温暖、亲切）
- 旧照片 / 早期产品穿插
- B-roll：工作场景、团队互动

**情感弧线**：共鸣（我也遇到过）→ 困境（真的很难）→ 坚持（但我没放弃）→ 突破（终于做到了）

**Prompt 关键词**：
```
Documentary-style founder portrait, natural window light, subtle
handheld movement, intimate close-up of founder's face, warm
color grade, intercut with workspace b-roll, authentic emotional
beats with natural pauses
```

### 模板 2: Mission（使命宣言）
> "我们相信什么"

**结构**：宏大愿景 → 现实差距 → 我们的行动 → 号召加入

**视觉语言**：
- 航拍大景开场（宏大感）
- 快速剪辑蒙太奇（行动感）
- 字幕叠加核心价值观
- 结尾群像 / 标志性画面

**Prompt 关键词**：
```
Brand mission film, opening aerial establishing shot, rapid
montage of purposeful action, text overlay of core values,
group portrait finale, inspirational tone, warm amber and
teal color grade
```

### 模板 3: Testimonial（用户证言）
> "客户怎么说"

**结构**：用户出镜讲述 → 使用场景 → 结果/变化 → 推荐

**视觉语言**：
- 用户面部特写（85mm 浅景深）
- 柔和自然光（不要棚拍感，太假）
- 真实环境背景（家/办公室，不要纯色）
- 产品自然出镜（不是硬塞）

**Prompt 关键词**：
```
Authentic testimonial interview, 85mm shallow depth of field,
natural ambient lighting, real environment background (home or
office), subject speaking directly to camera with genuine emotion,
product appearing naturally in the scene
```

### 模板 4: Behind-the-Scenes（幕后纪实）
> "我们怎么做的"

**结构**：原材料/起点 → 制作过程 → 匠心细节 → 成品 reveal

**视觉语言**：
- 极近微距（手指触碰材料）
- 手持跟拍（工匠/员工）
- 自然声（机器声、环境声）
- 时间推移 / 工序蒙太奇

**Prompt 关键词**：
```
Behind-the-scenes documentary, extreme macro close-ups of hands
working with materials, handheld following artisans, natural
ambient sound atmosphere, process montage showing raw material
to finished product, authentic workshop lighting
```

---

## 纪录片手持语言

品牌视频的运镜不是"越稳越好"，适度的手持感 = 真实感 = 信任感。

### 手持晃动程度
| 等级 | 描述 | 适用 |
|------|------|------|
| **Level 1: 微晃** | 3-5% 轻微呼吸式 | 创始人采访、证言 |
| **Level 2: 跟拍** | 10% 走路式 | 幕后纪实、工厂巡视 |
| **Level 3: 手持纪实** | 15-20% 明显手持 | 街头采访、事件记录 |

**Prompt 写法**：
```
Level 1: "extremely subtle handheld movement, 3% organic sway"
Level 2: "handheld following shot with natural walking rhythm"
Level 3: "documentary handheld, raw authentic camera movement"
```

### 自然光偏好
品牌视频优先用**自然光**（而非布光），因为"真实 > 精致"：
- **窗光**（最推荐）：柔和方向感 + 温暖 → `natural window light from the side`
- **黄金时刻**：户外品牌必选 → `golden hour backlight`
- **Available Light**：就用现场有什么光 → `available ambient light, no artificial lighting`
- **"不完美"美学**：保留过曝/欠曝、保留阴影 → `embrace natural light imperfections`

---

## 品牌价值观 → 视觉符号映射

| 品牌价值 | 视觉符号 | Prompt 关键词 |
|---------|---------|-------------|
| **信任** | 近距离眼神、暖光、柔焦 | `intimate close-up, warm light, eye contact` |
| **创新** | 冷色科技光、动态线条、HUD | `cool tech lighting, dynamic lines, futuristic` |
| **温暖** | 金色调、家庭场景、触碰 | `golden tones, domestic scene, gentle touch` |
| **可持续** | 自然绿、户外、原材料 | `natural green palette, outdoor, raw materials` |
| **奢华** | 低 Key 光、慢运镜、材质特写 | `low-key dramatic lighting, slow movement, material texture macro` |
| **年轻** | 高饱和、快节奏、街头 | `vibrant saturated colors, energetic pacing, urban` |
| **专业** | 中性灰、对称构图、稳定 | `neutral palette, symmetrical framing, steady` |

---

## 情感信任弧线（品牌视频万能结构）

```
[Hook · 共鸣]     0-3s   "你是不是也遇到过 X？"（引起认同）
[困境 · 真实痛点]  3-8s   展示真实问题（不是编的，要有细节）
[转折 · 解决方案]  8-15s  品牌/产品如何解决（不是硬卖，是展示过程）
[价值观落地]       15-25s 升华到品牌使命（为什么做这件事比怎么做更重要）
[CTA]             25-30s 一句话行动号召（简洁，不要贪心）
```

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Documentary-style brand origin story. Intimate close-up of a
founder figure in a warmly lit workshop, natural window light
from the left, subtle handheld camera sway. The founder looks
directly at camera with calm confidence, then turns to examine
a product on the workbench. Shallow depth of field, background
softly reveals shelves of materials and tools. Warm amber and
natural wood tones dominate. Authentic, unpolished aesthetic
with visible natural light variations. 85mm portrait lens feel,
organic breathing rhythm in camera movement.
```

### Kling（中文）
```
纪录片风格品牌创始人故事。创始人在温暖的工坊里接受采访式拍摄，
自然窗光从左侧打来。轻微手持晃动增加真实感。创始人直视镜头，
表情平静而自信，然后转向工作台上的产品。浅景深，背景柔和地
展示材料架和工具。暖棕色+原木色调为主。85mm 人像镜头感，
保留自然光的不完美质感。
```

### Runway Gen-3
```
Brand documentary close-up. Founder in a workshop with natural
window light, subtle handheld sway, looking into camera then
turning to product on workbench. Shallow depth of field, warm
amber tones, authentic lighting. 85mm lens, organic camera
breathing.
```

### Sora
```
A 15-second brand story documentary. Opens with an intimate
close-up of a founder in their workshop, natural sunlight
streaming through a side window creating warm directional light.
The camera holds steady with barely perceptible handheld movement.
The founder's expression is calm, genuine — they look into the
lens for a beat, then turn to pick up their signature product
from a worn wooden workbench. The shallow depth of field reveals
shelves of raw materials and tools in the soft background. Color
palette is warm amber, natural wood, and cream. The footage has
an authentic, unpolished documentary quality — embracing natural
light variations and real workshop textures.
```

---

## 避坑

1. ❌ **太像广告** → 品牌故事的关键是"真实感"，过度美化 = 不信任
2. ❌ **全程产品特写** → 品牌故事讲"人"和"为什么"，产品只是证据
3. ❌ **用棚拍灯光** → 自然光才有纪录片真实感，布光太精致会像广告
4. ❌ **运镜太稳** → 适度手持 = 真实，完美稳定 = 做作
5. ❌ **忘了 CTA** → 感动完了不告诉观众怎么行动 = 白做
6. ❌ **价值观太空** → "我们追求卓越"不如"我们每颗螺丝检查 3 遍"

## 输出规范

```
## 🏢 [品牌名/标题]（[模板类型]品牌叙事）

**模板**: [Origin / Mission / Testimonial / BTS]
**核心价值**: [信任/创新/温暖/可持续/奢华/年轻/专业]
**光照**: [窗光 / 黄金时刻 / Available Light]
**手持等级**: [Level 1 微晃 / Level 2 跟拍 / Level 3 纪实]

**情感弧线**
[Hook] ...
[困境] ...
[转折] ...
[价值观] ...
[CTA] ...

**Prompt**（按模型）

— Higgsfield（⚠️ 已过 content-filter）—
<prompt>

— Kling —
<中文 prompt>
```

## 质量自检

- [ ] 模板类型明确（Origin/Mission/Testimonial/BTS）
- [ ] 有明确的情感弧线（不是平铺直叙）
- [ ] 自然光 > 布光（除非品牌调性要求精致感）
- [ ] 适度手持感（不是全稳定）
- [ ] 产品自然出现（不是硬塞）
- [ ] 有 CTA（哪怕只是一句话）
- [ ] Higgsfield prompt 不含 banned words
