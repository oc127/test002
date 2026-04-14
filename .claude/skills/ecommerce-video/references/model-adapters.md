# 电商视频的模型 Adapter

电商场景下，不同模型的表现和调用姿势。核心关注：**产品细节还原度 + 文字可生成 + 真实人物动作**。

---

## 模型能力对比（针对电商场景）

| 模型 | 产品还原 | 文字生成 | 真人动作 | UGC 风格 | 推荐度 |
|------|---------|---------|---------|---------|--------|
| **Runway Gen-3** | ★★★★ | ★★ | ★★★★ | ★★★ | ⭐⭐⭐⭐⭐ 首推 |
| **Kling 2.0** | ★★★★ | ★★★ | ★★★★★ | ★★★★ | ⭐⭐⭐⭐⭐ 首推 |
| **Higgsfield Seedance 2.0** | ★★★★★ | ★ | ★★★ | ★★ | ⭐⭐⭐⭐ 电影感带货 |
| **Luma Ray 2** | ★★★★ | ★ | ★★★ | ★★ | ⭐⭐⭐ 图生视频强 |
| **Sora** | ★★★★★ | ★★★ | ★★★★ | ★★★ | ⭐⭐⭐⭐ 待平台普及 |

> 注：AI 视频模型目前都存在"字幕/文字容易乱码"的问题，商业用字幕建议后期添加。

---

## 1. Runway Gen-3 — 电商推荐 🏆

### 为什么电商首选
- 工具链完整：生成 → 延长 → 图生视频 → 批量
- 画面质感商业化（默认就像广告片）
- 有 Camera Control，运镜可控

### 电商 Prompt 模板

**Hero Shot 产品展示**：
```
[Product description]. Clean [color] studio background.
Soft studio lighting from 45 degrees. Subtle reflection on the surface.
Slow 360 degree rotation. Macro details visible. Commercial photography style.
```

**In-Use 使用场景**：
```
A [人物描述] in [场景] is [动作 with product]. Natural daylight.
Authentic lifestyle moment. Shallow depth of field with product in focus.
Warm color grade.
```

**Before/After 对比**：
```
Split screen: left side shows [问题], right side shows [方案].
Same person, same lighting, identical framing. Clean visual comparison.
```

### Runway 电商小技巧
- **用 `--seed` 保持角色一致**：做 5 条不同卖点视频用同一个 seed
- **图生视频更可控**：先用 Midjourney/Ideogram 生成关键帧，再 img2video
- **关键词 `commercial photography`**：比 `product shot` 效果更好

---

## 2. Kling 2.0 — 真人带货神器 🏆

### 为什么适合带货 UGC
- 真人动作最自然（快手血统）
- 中文 prompt 最好用
- 嘴型匹配度高（配音同步）

### 电商 Prompt 模板（中文）

**UGC 种草**：
```
竖屏手持视角。年轻女孩坐在床上，面对镜头说话，
手里拿着 [产品名]，开心地展示。自然窗光从左侧照入，
卧室背景略虚化。vlog 风格，自拍视频质感，真实感强。
```

**使用场景**：
```
中景。[人物] 在 [场景] 正在 [动作]，[产品] 清晰可见。
动作自然流畅，面部表情真实，日光，电影感色调。
```

**ASMR 产品特写**：
```
微距慢动作。[产品] 的 [细节动作，如切开/挤出/涂抹]，
显示出 [材质/效果]。纯色干净背景，顶部柔光，极致质感。
```

### Kling 电商小技巧
- **先上传参考图**：主播形象/产品图 → Kling 能保持一致性
- **用"说话"触发嘴部动作**：`女孩对着镜头说"这款真的好用"`
- **适合做"直播切片"风**：描述"略晃的手持 + 店内背景"

---

## 3. Higgsfield Seedance 2.0 — 电影感带货

### 适合什么
- 高端品牌（奢侈品、香水、腕表）
- 需要"电影质感"而非"淘宝质感"
- 10-15 秒的品牌片 + 带货融合

### Prompt 模板
```
Cinematic commercial shot of [product]. [Camera move from camera-moves.md].
[Lighting from lighting.md]. Shot on [film stock reference].
Premium luxury aesthetic, shallow depth of field.
```

### 例：高端护肤品
```
Cinematic macro shot of a glass skincare bottle.
Slow dolly push-in toward the bottle's cap.
Soft golden hour backlight creating a halo.
Shot on Kodak 500T film, shallow depth of field,
luxury commercial aesthetic in the style of Chanel ads.
```

### Higgsfield 电商小技巧
- 慎用：**不擅长多产品堆在一起** —— 一次只拍一个产品
- 擅长：**单一产品的极致质感展示**

---

## 4. Luma Ray 2 — 图生视频 / 物理模拟

### 适合什么
- 已有产品图，想让它动起来
- 需要真实物理效果（液体/烟雾/布料）
- 转动、悬浮、开箱效果

### 工作流
1. 先用 Midjourney/Ideogram/产品摄影图 生成产品静态图
2. 上传到 Luma 作为起始帧
3. Prompt 描述你要的"运动"

### Prompt 模板
```
[Starting frame: 产品静态图]
The [product] slowly rotates 180 degrees revealing its [feature].
[Lighting/material] subtly shifts during the rotation.
Realistic fabric/liquid/smoke physics.
```

### Luma 电商小技巧
- 极适合：液体产品（精华、香水、酒）—— 物理真实
- 极适合：布料产品（服饰、床品）—— 飘动自然
- 不适合：需要剧情/人物动作

---

## 5. Sora — 长 prompt 讲故事

### 适合什么
- 30-60 秒剧情带货
- 需要多场景连续
- 高端内容广告

### Prompt 模板（剧本式）
```
[设定] A [人物] wakes up to [问题/痛点]. [时间 30s] later,
they reach for [product]. The [product] [动作/使用过程]. [效果].
Finally, [解决后状态]. Cinematic lighting throughout.
Aspect ratio 9:16.
```

### Sora 电商小技巧
- **一个 prompt 讲完一个完整故事**，不要拆分
- **指定长度**：加 "duration 10 seconds"
- **限制风格**：别用品牌名、电影名做风格参考（版权问题）

---

## 通用电商 Prompt 禁忌

### ❌ 不要写
- "make it look premium/luxurious"（空词）
- "like Apple/Gucci ad"（可能被过滤）
- "show the product very clearly"（AI 视频默认就会）
- "with text saying 'SALE'"（文字基本会乱码）

### ✅ 改成写
- 具体视觉元素：`minimalist white background, marble surface`
- 具体参考：`commercial photography style, 45-degree key light`
- 具体构图：`product centered, rule of thirds`
- 文字用后期：画面留出"字幕区域"，后期加文字

---

## 批量生成策略

同一个产品，建议生成 5-10 条不同方向的素材，A/B 测试：

```
素材 1：痛点钩子 + 产品方案      （转化型）
素材 2：ASMR 钩子 + 细节展示     （种草型）
素材 3：UGC 钩子 + 真人使用      （信任型）
素材 4：反差钩子 + 效果对比      （惊喜型）
素材 5：数字钩子 + 权威证言      （信任型）
```

用同一个 seed 或同一个主播形象，保持品牌一致性。

---

## 实战：用同一款产品跑 5 条视频

假设产品：智能咖啡机

**Prompt 1（痛点 + Runway）**
```
Messy office desk with scattered papers, a tired person rubbing their eyes,
fluorescent overhead lighting, documentary handheld style.
```

**Prompt 2（ASMR + Kling）**
```
微距慢动作，深棕色浓缩咖啡液从机器口缓缓流入白瓷杯，
咖啡油脂层浮现，蒸汽上升，纯白背景柔光，极致质感。
```

**Prompt 3（UGC + Kling）**
```
竖屏手持，年轻女生在办公室工位，笑着按咖啡机按钮，
15 秒后拿起做好的咖啡喝了一口，满意的表情。
自拍视频风格，真实感强。
```

**Prompt 4（对比 + Runway）**
```
Split screen: left side shows a person making coffee with traditional pour-over,
taking minutes, concentrated effort. Right side shows the same person pressing
one button on a smart coffee machine, taking 15 seconds, smiling.
```

**Prompt 5（Hero + Higgsfield）**
```
Cinematic macro shot of the smart coffee machine on a marble kitchen counter.
Slow dolly push-in toward the product. Warm morning sunlight from a window.
Subtle steam rising. Premium appliance aesthetic.
```
