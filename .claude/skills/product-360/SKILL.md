---
name: product-360
description: 生成 360° 产品转台视频 prompt。当用户需要"360度展示/产品转台/turntable/产品旋转/全角度展示/product spin/产品环绕/360 product view/旋转展示台"时自动调用。专注单一产品在转台上的环绕展示，区别于 3d-cgi（复杂 CGI 动画）和 ecommerce-video（故事性广告）。极简主义——只有产品和光。
---

# 360° 产品转台 (Product 360 / Turntable)

转台视频只做一件事：**让产品自己说话**。没有故事，没有场景，没有演员——只有产品在光线中缓慢旋转，展示每一个角度。

## 调用时机

**强触发词**：
- 360 度展示 / 产品转台 / 旋转展示
- turntable / product spin / 360 view
- 产品环绕 / 全角度 / 环绕拍摄
- 转台拍摄 / 展示台旋转

**典型请求**：
- "做一个球鞋 360 度转台视频"
- "手表产品 turntable 展示"
- "新包包的全角度旋转视频"

**与 3d-cgi / ecommerce-video 的边界**：
| | product-360 | 3d-cgi | ecommerce-video |
|---|---|---|---|
| **焦点** | 单产品旋转 | CGI 动画 | 故事性广告 |
| **运镜** | 固定环绕 | 多种运镜 | 多镜切换 |
| **背景** | 极简/纯色 | 抽象环境 | 使用场景 |
| **复杂度** | 最低 | 高 | 中 |

---

## 3 种转台模式

### 模式 1: Simple Spin（简单旋转）
产品在原地匀速旋转 360°，相机不动。
- 最经典、最安全
- 适合任何产品
- **Prompt**: `Product centered on a seamless background, rotating 360 degrees at constant speed on an invisible turntable, camera fixed at eye level`

### 模式 2: Orbit（相机环绕）
产品不动，相机围着产品转 360°。
- 更电影感
- 可以加高低角度变化
- **Prompt**: `Camera slowly orbits 360 degrees around a stationary product, maintaining constant distance, smooth orbital movement`

### 模式 3: Multi-Angle（多角度切换）
不是连续旋转，而是在 4-8 个关键角度之间切换。
- 适合有"最佳角度"的产品
- 每个角度停顿 1-2 秒
- **Prompt**: `Product showcased from 4 key angles — front, 3/4 left, side profile, back — cutting between each view with smooth transitions`

---

## 光照方案

转台视频的光照 = 一切。产品没有场景帮忙，全靠光线塑造质感。

| 产品类型 | 推荐光照 | Prompt 描述 |
|---------|---------|------------|
| **金属/手表** | 硬光 + 高光反射 | `crisp directional lighting with sharp specular highlights on metal surfaces` |
| **皮革/布料** | 柔光 + 质感强调 | `soft diffused lighting emphasizing leather grain and textile texture` |
| **玻璃/透明** | 背光 + 折射 | `backlit with visible light refraction through transparent material` |
| **哑光产品** | 均匀柔光 | `even soft lighting with minimal shadows, studio softbox setup` |
| **鞋类** | 侧光 + 地面反射 | `side key light with reflective surface underneath showing mirror reflection` |
| **食品包装** | 暖光 + 自然感 | `warm natural-feeling light, as if near a window, appetizing warmth` |

---

## 背景选择

| 背景类型 | 适用 | Prompt |
|---------|------|--------|
| 纯白无缝 | 电商标准 | `seamless pure white background, no shadows, product photography studio` |
| 渐变灰 | 高级感 | `smooth gradient from light gray to darker gray, studio backdrop` |
| 纯黑 | 奢侈品 | `pure black background, product illuminated by rim light` |
| 反光面 | 科技/奢侈 | `dark reflective surface underneath, mirror-like floor reflection` |
| 环境光 HDRI | 真实感 | `subtle environmental reflections on product surface, studio HDRI` |

---

## 旋转参数

| 时长 | 转速 | 适用 |
|------|------|------|
| 5s | 360°/5s = 72°/s | 快速浏览 |
| 8s | 360°/8s = 45°/s | **标准（推荐）** |
| 10s | 360°/10s = 36°/s | 慢速细品 |
| 15s | 360°/15s = 24°/s | 奢侈品高端展示 |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Product turntable showcase. A premium white sneaker centered on
a seamless light gray gradient background, rotating smoothly
360 degrees on an invisible turntable. Crisp studio lighting
with a soft key light from upper left and subtle fill light.
The shoe's material textures — leather panels, mesh sections,
rubber sole — are clearly visible as it rotates. Reflective
dark surface underneath shows a subtle mirror reflection.
Camera fixed at slightly above eye level. Smooth constant
rotation speed. Clean product photography aesthetic.
```

### Kling（中文）
```
产品转台展示。一只高端白色运动鞋居中放置在浅灰渐变无缝背景上，
在隐形转台上平滑旋转 360 度。清晰的影棚灯光，左上方柔和主光
加微弱补光。旋转时皮面、网布、橡胶底等材质纹理清晰可见。
下方深色反光面展示镜面倒影。相机固定在略高于平视的角度。
匀速旋转。干净的产品摄影美学。
```

### Runway Gen-3
```
360 product turntable. Premium white sneaker on seamless gray
gradient, rotating smoothly. Studio key light from upper left,
subtle fill. Material textures visible — leather, mesh, rubber
sole. Dark reflective surface below. Fixed camera slightly
above eye level. Constant rotation speed. Clean studio aesthetic.
```

---

## 避坑

1. ❌ **旋转太快** → 看不清细节，8 秒一圈最安全
2. ❌ **背景太复杂** → 转台的重点是产品，背景必须极简
3. ❌ **多个产品同时转** → AI 处理多物体旋转很不稳，一次只放一个
4. ❌ **没有反光面** → 加一层地面反射立刻提升高级感

## 输出规范

```
## 🔄 [产品名]（360° 转台展示）

**转台模式**: [Simple Spin / Orbit / Multi-Angle]
**产品**: [具体产品描述]
**光照**: [硬光/柔光/背光/侧光]
**背景**: [纯白/渐变灰/纯黑/反光面]
**时长**: [Xs] / 转速: [360°/Xs]

**Prompt**（按模型）
```

## 质量自检

- [ ] 只有一个产品（不堆多个）
- [ ] 背景极简（纯色或渐变）
- [ ] 光照匹配产品材质
- [ ] 旋转速度合理（8-10s 一圈）
- [ ] Higgsfield prompt 不含 banned words
