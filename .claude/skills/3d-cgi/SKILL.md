---
name: 3d-cgi
description: 生成 3D CGI 风格视频 prompt。当用户需要"3D/CGI/产品 CGI/C4D/Blender/Octane/工业渲染/奢侈品 CGI/化妆品 CGI/科技产品动画/抽象 3D"时自动调用。专注产品级 CGI 视觉语言：材质表达、HDRI 光照、产品 reveal 镜头、粒子与流体特效，适配海外视频模型。
---

# 3D CGI 视频 (3D Computer-Generated Imagery)

CGI 的核心竞争力：**在真实世界无法实现的画面**——液态金属变形、产品爆炸重组、纯粹物理的流体与粒子、非现实材质。

## 调用时机

**强触发词**：
- 3D / CGI / C4D / Blender / Octane / Redshift
- 产品动画 / 产品 CGI / 产品 reveal
- 工业渲染 / product viz
- 抽象 3D / 液态金属 / 粒子
- 奢侈品广告 / 科技产品动画

**典型请求**：
- "给这款手表做一个 CGI 广告"
- "液态金属流动形成 Logo"
- "化妆品的产品旋转展示"
- "抽象 3D 几何体爆炸重组"

## CGI 视频的 4 大类型

### 类型 1: Product Reveal（产品揭示）
产品以震撼方式出场。
- **经典手法**：从虚无中组装、液体溅起形成、光粒子凝聚
- **时长**：5-8 秒（揭示瞬间）
- **适用**：发布会开场、电商 Hero shot
- **Prompt 关键词**:
  ```
  Product reveal shot. Liquid metal droplets flow and assemble
  into [产品], studio HDRI lighting, dramatic rim light,
  macro close-up, hyper-realistic CGI render, Octane quality.
  ```

### 类型 2: Product Showcase（产品展示）
全方位旋转/解析展示。
- **经典手法**：360° 旋转、爆炸图、剖面动画
- **时长**：10-30 秒
- **适用**：电商详情页、发布会细节展示
- **Prompt 关键词**:
  ```
  Hero product showcase. [产品] slowly rotating 360 degrees on
  mirrored surface, pure white infinite cyclorama background,
  soft studio HDRI lighting, photoreal CGI.
  ```

### 类型 3: Abstract Motion Design（抽象运动设计）
纯图形、几何、粒子，无实体产品。
- **经典手法**：几何体形变、粒子运动、流体模拟
- **时长**：5-15 秒
- **适用**：品牌 logo reveal、标题序列、ID
- **Prompt 关键词**:
  ```
  Abstract 3D motion design. Geometric shapes morphing and
  multiplying, particle flow, smooth gradient colors, minimal
  studio environment, motion graphics aesthetic.
  ```

### 类型 4: Simulation（物理模拟）
极致物理效果炫技。
- **经典手法**：流体、布料、烟雾、碰撞
- **时长**：5-10 秒
- **适用**：香水、饮料、洗护、食品
- **Prompt 关键词**:
  ```
  Hyper-realistic fluid simulation. Liquid splashes in slow
  motion, viscous droplets, complex fluid dynamics, Houdini-style
  simulation, cinematic lighting.
  ```

---

## 材质描述词典（极其重要）

CGI 质感 = 材质准确度。Prompt 必须**精确描述材质**：

### 金属类
| 材质 | 描述 | 视觉特征 |
|------|------|---------|
| Brushed Metal | 拉丝金属 | 细微纹理反射 |
| Polished Chrome | 镀铬抛光 | 镜面完美反射 |
| Matte Gold | 哑光金 | 温暖柔和反光 |
| Titanium | 钛金属 | 冷灰带蓝调 |
| Liquid Metal | 液态金属 | 流动镜面 |
| Rose Gold | 玫瑰金 | 粉调金色 |

### 玻璃/透明类
| 材质 | 描述 | 视觉特征 |
|------|------|---------|
| Clear Glass | 透明玻璃 | 折射 + 反射 |
| Frosted Glass | 磨砂玻璃 | 散射半透明 |
| Crystal | 水晶 | 强折射彩虹色 |
| Plexiglass | 亚克力 | 边缘彩虹 |

### 液体类
| 材质 | 描述 |
|------|------|
| Water | 透明流动，真实表面张力 |
| Honey | 高粘度、金黄 |
| Mercury | 液态金属、完美反射 |
| Oil | 黑色、反光 |
| Milk | 不透明、白色、流动 |

### 有机类
| 材质 | 描述 |
|------|------|
| Soft Silicone | 半透明、有弹性 |
| Ceramic | 哑光陶瓷、冷 |
| Velvet | 天鹅绒、绒毛反光 |
| Leather | 皮革、纹理 |

**Prompt 写法示例**：
```
The product is made of brushed titanium with polished chrome accents,
a frosted glass dial, and liquid gold second hand. Hyper-detailed
material rendering, physically-based shading (PBR).
```

---

## HDRI 光照（CGI 的核心）

**HDRI = 高动态范围环境光**。3D 场景的光源来自 HDRI 贴图。描述 HDRI 就是描述光环境：

### 常用 HDRI 描述

| HDRI 类型 | 描述 | 适用 |
|----------|------|------|
| **Studio Pure White** | 无限白色环境，顶部柔光 | 产品摄影、电商 |
| **Studio Neutral Gray** | 灰色工作室 | 汽车、科技 |
| **Golden Hour Sky** | 夕阳天空 HDRI | 奢侈品、情感广告 |
| **Urban Rooftop** | 城市屋顶 | 科技、潮牌 |
| **Sci-fi Studio** | 未来感 LED 环境 | 科技、游戏 |
| **Dark Showroom** | 暗调展厅 | 高端车、珠宝 |

**Prompt 写法**：
```
Lit by a studio HDRI with soft overhead lighting and subtle
rim light from behind. Reflections of the HDRI environment
visible on polished surfaces.
```

### 光的 3 要素（CGI 必写）
1. **Key Light 主光**：方向 + 硬度
2. **Rim Light 轮廓光**：从背后勾勒
3. **Fill Light 补光**：降低阴影对比

---

## CGI 经典镜头运动

### 1. Slow Orbit（慢速环绕）
- 产品在中心，相机绕一周
- 最稳的 CGI 手法
- **Prompt**: `slow smooth orbit around the product, 45-degree elevation`

### 2. Push-In to Macro（推近到微距）
- 从全景推到极近特写
- 展示细节的经典手法
- **Prompt**: `camera slowly pushes in from product wide shot to extreme macro detail`

### 3. Dolly Reveal（滑动揭示）
- 相机从旁边滑过，揭示产品
- 科技感强
- **Prompt**: `dolly slide revealing the product from behind an obstruction`

### 4. Fly-Around（飞越）
- 在产品周围做复杂 3D 运动
- 展示全方位
- **Prompt**: `camera flies around the product in a complex 3D path, showing multiple angles`

### 5. Freeze + Rotate World（时间冻结）
- 主体静止，世界绕它转
- 科技感、游戏感
- **Prompt**: `product frozen in mid-air while the background environment rotates around it`

---

## CGI 场景环境选择

### 1. Infinite Cyclorama 无限背景
最经典：白色或黑色无缝背景。
```
Pure white infinite cyclorama, product floating in center,
slight shadow underneath, softbox key light.
```

### 2. Mirrored Floor 镜面地板
高端奢侈品常用。
```
Polished black mirrored floor creating perfect reflection,
minimal studio environment.
```

### 3. Abstract Geometric 抽象几何
品牌 ID 常用。
```
Floating geometric shapes in pastel colors, minimalist abstract
environment, gradient background.
```

### 4. Sci-fi Tech 科技未来
3C 产品常用。
```
Sci-fi holographic environment, glowing circuit patterns, particles
floating, dark blue and cyan palette.
```

### 5. Natural + Studio Hybrid 自然+棚拍
混合感：产品在室内但像室外光。
```
Studio environment with a window light suggesting natural sunlight,
soft shadows, warm golden glow.
```

---

## 粒子与特效

CGI 独有的视觉武器：

| 效果 | 适用 | Prompt |
|------|------|--------|
| **Particle Burst** | Drop、揭示 | `particle burst emanating outward, glowing embers` |
| **Smoke Flow** | 神秘、优雅 | `volumetric smoke flowing in slow motion` |
| **Light Trails** | 科技、速度 | `light trails following the motion path` |
| **Dust Motes** | 气氛、质感 | `floating dust motes catching light` |
| **Energy Rings** | 未来感 | `expanding energy rings pulsing outward` |
| **Liquid Splash** | 饮料、清洁 | `slow motion liquid splash forming a crown shape` |

---

## 品类 → CGI 类型 映射

| 品类 | 推荐类型 | 关键视觉 |
|------|---------|---------|
| 智能手机 | Product Reveal + Showcase | 金属玻璃、HUD 投影 |
| 腕表 | Showcase + Macro | 机芯、材质细节 |
| 汽车 | Fly-around + Sci-fi Tech | 流线、轮毂特写 |
| 香水 | Simulation + Showcase | 液体、雾化 |
| 化妆品 | Simulation + Macro | 质地、涂抹 |
| 珠宝 | Macro + Mirrored Floor | 折射、高光 |
| 科技配件 | Sci-fi Tech | 电路、发光 |
| 家居产品 | Showcase + 自然光 | 材质、场景融合 |
| 品牌 Logo | Abstract Motion | 形变、粒子 |

---

## 模型适配（CGI 专属要点）

### Runway Gen-3（推荐，CGI 质感稳）
```
3D CGI product animation. A [产品 w/ 材质描述] slowly rotates
in a pure white infinite studio. Soft HDRI lighting, subtle rim
light, ground shadow. Physically-based rendering, hyper-realistic
CGI quality. Camera slowly orbits 45 degrees.
```

### Luma Ray 2（推荐，物理模拟好）
上传产品关键帧图 + 描述运动：
```
Starting frame: [product still image]
Motion: product slowly rotates 360 degrees on reflective surface.
Particle effects: soft light particles floating around the product.
Physics: realistic reflections and refractions updating in real-time.
Style: Octane render quality, photoreal CGI.
```

### Higgsfield Seedance 2.0（复杂运镜适合）
```
Cinematic CGI product shot of [产品]. Camera performs a smooth
arc around the product. Liquid metal details flow across the
surface. Studio HDRI lighting with strong rim light.
```

### Sora（推荐复杂长序列）
长剧本适合做"从零到产品"的 reveal 序列。

### Kling
对 CGI 类支持相对一般，偏实拍风格。**CGI 任务优先 Runway / Luma。**

---

## CGI Prompt 黄金公式

```
[镜头类型] + [产品名] + [核心材质] + [HDRI 环境] + [运动] + [特效] + [风格参考]
```

### 例：奢侈腕表 CGI
```
Hero product showcase shot. A luxury mechanical watch with a
brushed titanium case, polished chrome bezel, frosted sapphire
crystal, and rose gold hour markers. Dark showroom HDRI with a
single overhead softbox, subtle rim light from behind. The watch
slowly rotates 360 degrees on a black mirrored floor, casting
a perfect reflection. Dust motes floating in the air catch the
rim light. Hyper-realistic CGI, Octane render quality,
Rolex-campaign aesthetic.
```

### 例：化妆品液体溅起
```
Extreme macro slow-motion CGI. A droplet of iridescent serum
splashes onto a ceramic surface, forming a perfect crown of
liquid in mid-air. Subsurface scattering visible in the fluid.
Pure white cyclorama background. Strong key light from 45
degrees, rim light from behind. Houdini-quality fluid simulation,
cosmetic commercial aesthetic.
```

---

## 避坑

1. ❌ **只说"3D"不说具体材质** → 模型给你塑料玩具
2. ❌ **"看起来像 Pixar"** → 多数模型拒绝，改写具体视觉特征
3. ❌ **要求"完全真实"的运动物理** → 目前 AI 视频物理还不稳，只选 Luma 做物理
4. ❌ **一次堆多个特效**（粒子+烟雾+流体+光线） → 全糊成一团
5. ❌ **忽略反射** → CGI 质感 50% 来自反射

## 输出规范

```
## 💎 [产品名] CGI

**类型**: [Reveal / Showcase / Abstract / Simulation]
**材质构成**: ...
**HDRI 环境**: ...
**运动**: ...
**特效**: ...

**Prompt**（按模型）

— Runway Gen-3（首选）—
<prompt>

— Luma Ray 2（图生视频）—
<prompt>

— Higgsfield Seedance 2.0 —
<prompt>

**后期建议**
[如需要：色彩校正 / 加品牌 Logo / 合成背景]
```

## 质量自检

- [ ] 材质描述精确（不止"金属"，要"拉丝钛合金"）
- [ ] HDRI 光照明确
- [ ] 运动简单（1 个运镜 + 1 个特效）
- [ ] 环境选对（cyclorama / mirrored / sci-fi）
- [ ] 选对模型（Runway/Luma 优先）
