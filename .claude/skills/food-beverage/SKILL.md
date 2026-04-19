---
name: food-beverage
description: 生成美食/饮品/餐饮视频 prompt。当用户需要"美食视频/食物拍摄/food video/餐厅宣传/饮品广告/recipe video/cooking/烹饪过程/甜品展示/咖啡拉花/鸡尾酒/food porn/美食博主"时自动调用。专注食物质感（光泽/蒸汽/浇淋/切开瞬间）的极致展现，让观众"看饿了"。
---

# 美食与饮品 (Food & Beverage Video)

美食视频只有一个标准：**看完让人想吃**。所有的灯光、运镜、节奏都服务于这一个目标。

## 调用时机

**强触发词**：
- 美食视频 / 食物拍摄 / food video
- 餐厅宣传 / 饮品广告 / recipe video
- cooking / 烹饪 / 甜品 / 咖啡 / 鸡尾酒
- food porn / 美食博主 / 吃播

**典型请求**：
- "做一个汉堡的慢动作特写视频"
- "咖啡拉花的 8 秒短片"
- "餐厅新菜品的宣传视频"
- "巧克力浇淋的 food porn"

---

## 5 种美食视频类型

### 类型 1: Hero Shot（英雄镜头）
成品食物的极致展示——就是让你看饿了的那一秒。
- 微距特写 + 浅景深
- 暖光 + 食物光泽
- 微微的蒸汽/烟气
- **Prompt**: `Extreme close-up hero shot of [food], shallow depth of field, warm directional lighting emphasizing texture and gloss, subtle steam rising, appetizing food photography`

### 类型 2: Process（制作过程）
烹饪过程的视觉享受——切、炒、翻、浇。
- 俯拍（top-down）+ 侧面切换
- 动作是核心（刀切的瞬间、酱汁浇下、翻锅）
- 声音暗示（虽然是视频但要"看到"声音）
- **Prompt**: `Overhead cooking process shot, chef's hands preparing [food], satisfying cutting motion, sauce pouring in slow motion, kitchen ambient lighting`

### 类型 3: Pour / Drizzle（浇淋/倾倒）
液体动态——巧克力、酱汁、咖啡、蜂蜜、鸡尾酒。
- 慢动作是必须的
- 液体的光泽和粘稠感
- 黑色或深色背景突出液体
- **Prompt**: `Slow motion pour of [liquid] over [food/surface], viscous flow catching warm light, dark background for contrast, liquid dynamics with satisfying drip detail`

### 类型 4: Reveal（揭示）
切开/掰开/打开的瞬间——里面是什么？
- 横截面展示（面包的气孔、蛋糕的层次、汉堡的叠层）
- 慢动作切开 + 内部流出（cheese pull, lava cake）
- 极浅景深聚焦截面
- **Prompt**: `Satisfying food reveal — [food] being cut open in slow motion, cross-section showing internal layers and textures, melted filling flowing out, extreme shallow depth of field`

### 类型 5: Lifestyle（场景化）
食物在真实环境中——餐桌、咖啡馆、野餐。
- 强调氛围 > 食物细节
- 自然光 + 手持
- 有人的手 / 有互动
- **Prompt**: `Lifestyle food scene, [food/drink] on a rustic table with natural daylight from a nearby window, hands reaching for the dish, warm lived-in atmosphere, shallow depth of field`

---

## 食物质感词典

| 质感 | 视觉特征 | Prompt 描述 |
|------|---------|------------|
| 光泽 | 酱汁/糖霜反光 | `glossy sheen reflecting warm light` |
| 蒸汽 | 热食冒烟 | `gentle steam rising from the surface` |
| 脆皮 | 酥脆表面纹理 | `crispy golden crust with visible crunch texture` |
| 拉丝 | 芝士/糖浆拉丝 | `stretchy cheese pull with long gooey strands` |
| 多汁 | 肉汁/果汁溢出 | `juices glistening on the surface, droplets forming` |
| 气泡 | 碳酸/啤酒泡沫 | `effervescent bubbles rising through the liquid` |
| 粉霜 | 糖粉/可可粉 | `fine powder dusting settling on the surface` |
| 冰霜 | 冰淇淋/冷饮 | `frost crystals forming on the cold surface` |

---

## 美食灯光

| 灯光类型 | 效果 | 适用食物 |
|---------|------|---------|
| **侧逆光 45°** | 蒸汽可见 + 质感突出 | **万能（首选）** |
| **顶光** | 平面均匀 | 俯拍 / 制作过程 |
| **背光** | 轮廓光 + 透光感 | 饮品 / 透明液体 |
| **暖窗光** | 自然温暖 | 生活方式 / 餐厅 |

**关键原则**：食物灯光必须**暖色温**（3200-4000K）。冷光让食物看起来不好吃。

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Cinematic food hero shot. A freshly assembled gourmet burger sits
on a dark wooden board, warm side-backlight at 45 degrees
emphasizing the glossy sauce and golden toasted bun. Gentle steam
rises from the patty. Camera slowly pushes in from medium to
extreme close-up, revealing melted cheese stretching slightly.
Shallow depth of field, background softly blurred. Warm amber
color grade, appetizing food photography lighting. Slow deliberate
pacing.
```

### Kling（中文）
```
电影级美食英雄镜头。一个刚组装好的精品汉堡放在深色木板上，
45 度暖色侧逆光强调酱汁光泽和金黄色烤面包。肉饼上升起
柔和蒸汽。相机从中景缓慢推近到极致特写，展示融化的芝士
轻微拉丝。浅景深，背景柔和虚化。暖琥珀色调，令人垂涎的
美食摄影灯光。
```

### Runway Gen-3
```
Food hero shot. Gourmet burger on dark wood, warm 45-degree
side-backlight on glossy sauce and golden bun. Steam rising from
patty. Camera slowly pushes to extreme close-up, cheese stretching.
Shallow depth of field. Warm amber grade. Appetizing lighting.
```

---

## 避坑

1. ❌ **冷色灯光** → 食物在冷光下看起来像塑料模型，必须暖光
2. ❌ **全部俯拍** → 俯拍适合制作过程，成品要侧面/45° 展示立体感
3. ❌ **没有蒸汽/动态** → 静止的食物像假的，加蒸汽/浇淋/拉丝
4. ❌ **背景太花** → 食物是主角，碗碟和背景越简越好

## 输出规范

```
## 🍽️ [菜品名]（[类型]美食视频）

**视频类型**: [Hero Shot / Process / Pour / Reveal / Lifestyle]
**食物**: [具体菜品]
**关键质感**: [光泽/蒸汽/脆皮/拉丝/多汁]
**灯光**: [侧逆光/顶光/背光/窗光]

**Prompt**（按模型）
```

## 质量自检

- [ ] 灯光是暖色温（不是冷白光）
- [ ] 有至少一个动态元素（蒸汽/浇淋/拉丝/切开）
- [ ] 景深浅（食物清晰，背景虚化）
- [ ] 食物是画面绝对主角
- [ ] Higgsfield prompt 不含 banned words
