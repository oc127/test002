---
name: fashion-lookbook
description: 生成时尚/走秀/lookbook 视频 prompt。当用户需要"时尚视频/走秀/runway/lookbook/服装展示/fashion film/时装周/穿搭/outfit/造型展示/haute couture/街拍视频"时自动调用。专注服装在人体上的动态展示——面料流动、剪裁轮廓、搭配层次感，区别于 ecommerce-video（卖货转化）和 product-360（无人转台）。
---

# 时尚 Lookbook (Fashion Lookbook / Runway Film)

时尚视频的核心：**让衣服在动态中展示它的灵魂**。面料怎么垂坠、剪裁怎么贴合、走动时裙摆怎么飘——这些是图片做不到的。

## 调用时机

**强触发词**：
- 时尚视频 / 走秀 / runway / lookbook
- fashion film / 服装展示 / 穿搭
- 时装周 / 造型展示 / outfit
- haute couture / 街拍 / editorial

**典型请求**：
- "做一个秋冬系列 lookbook 视频"
- "高定走秀风格的 15 秒视频"
- "街拍风的穿搭展示"

---

## 4 种时尚视频风格

### 风格 1: Runway（走秀）
模特在 T 台上走来，展示整套造型。
- 固定机位 + 模特走向镜头
- 全身 → 中景 → 特写（面料/配饰）
- 干净背景（白/灰/黑）
- **Prompt**: `Fashion runway walk, model approaching camera in full-length view, transitioning to medium shot showing outfit details, clean minimal backdrop, professional catwalk lighting`

### 风格 2: Editorial（杂志大片感）
像 Vogue 封面拍摄，有造型、有情绪、有氛围。
- 精心布光（Rembrandt / butterfly）
- 模特有表演性（pose + micro-movements）
- 场景有叙事感（废墟/花田/建筑）
- **Prompt**: `High fashion editorial, model posing with subtle movement in a cinematic location, dramatic directional lighting, Vogue-quality composition`

### 风格 3: Street Style（街拍）
真实城市环境，行走中展示日常穿搭。
- 手持跟拍 + 自然光
- 城市街道 / 咖啡馆 / 地铁
- 真实感 > 精致感
- **Prompt**: `Street style fashion video, model walking through urban environment, natural daylight, handheld following shot, candid authentic feel`

### 风格 4: Lookbook（目录展示）
简洁高效地展示多套造型。
- 每套 2-3 秒，快切
- 统一背景（studio 或统一场景）
- 正面 → 侧面 → 背面
- **Prompt**: `Lookbook catalog style, model showcasing outfit from front, side, and back views, 2-second cuts between angles, consistent studio lighting and backdrop`

---

## 面料视觉语言

时尚视频的高级感来自**面料的动态表现**：

| 面料 | 动态特征 | Prompt 描述 |
|------|---------|------------|
| 丝绸 | 流动、反光 | `silk fabric flowing with liquid movement, catching light` |
| 针织 | 拉伸、回弹 | `knit texture stretching naturally with body movement` |
| 皮革 | 硬挺、折痕 | `leather surface with structured creases, catching edge light` |
| 薄纱 | 透光、飘逸 | `sheer fabric floating with air movement, backlit translucency` |
| 牛仔 | 质感、做旧 | `denim texture with visible weave and authentic wear patterns` |
| 羊毛 | 蓬松、温暖 | `wool texture with soft fuzzy surface, warm tactile quality` |

---

## 时尚灯光方案

| 灯光 | 效果 | 适用 |
|------|------|------|
| **Butterfly 光** | 鼻下蝴蝶阴影，高级感 | Editorial / Haute Couture |
| **侧光 Split** | 一半亮一半暗 | 戏剧性 / 暗黑风 |
| **自然窗光** | 柔和真实 | Street Style / Lookbook |
| **环形灯 Ring** | 均匀无阴影 | 电商 / 快时尚 |
| **Rim Light** | 轮廓勾边 | 走秀 / 剪影效果 |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
High fashion editorial video. A model in an elegant oversized
wool coat walks slowly through a misty autumn garden. Natural
golden hour backlight creates a warm rim light around the
silhouette. The coat's fabric moves with weight and structure.
Camera tracks smoothly at medium shot level, then transitions
to a close-up of the coat's texture and collar detail. Soft
depth of field, warm amber and deep green color palette.
Vogue editorial quality. Slow deliberate pacing.
```

### Kling（中文）
```
高端时尚编辑视频。模特穿着优雅的超大款羊毛大衣缓步走过
雾气缭绕的秋日花园。自然金色时刻逆光在轮廓周围创造温暖
的边缘光。大衣面料随动作展现重量和结构感。相机在中景平滑
跟拍，然后过渡到大衣质地和领口细节特写。柔和景深，
暖琥珀和深绿色调。Vogue 编辑品质。
```

### Runway Gen-3
```
Fashion editorial. Model in oversized wool coat walking through
misty autumn garden. Golden hour backlight, warm rim light on
silhouette. Fabric moves with weight. Smooth tracking medium
shot transitioning to texture close-up. Shallow depth of field.
Warm amber and deep green palette. Vogue quality.
```

---

## 避坑

1. ❌ **不展示面料运动** → 时尚视频的价值就是"衣服动起来"，纯 pose 不如拍照
2. ❌ **模特动作太多** → 让衣服做主角，模特只需简洁的走/转/停
3. ❌ **背景抢戏** → 背景服务于衣服，不能比衣服更抢眼
4. ❌ **灯光太平** → 没有光影层次的时尚视频 = 淘宝图动起来

## 输出规范

```
## 👗 [系列名/标题]（[风格]时尚视频）

**风格**: [Runway / Editorial / Street Style / Lookbook]
**服装**: [具体描述]
**面料**: [丝绸/针织/皮革/薄纱/牛仔/羊毛]
**灯光**: [Butterfly/侧光/自然光/Ring/Rim]

**Prompt**（按模型）
```

## 质量自检

- [ ] 风格明确（4 选 1）
- [ ] 面料有动态描述（不只说颜色）
- [ ] 灯光有方向和质感（不是"好看的光"）
- [ ] 模特动作简洁服务于衣服
- [ ] Higgsfield prompt 不含 banned words
