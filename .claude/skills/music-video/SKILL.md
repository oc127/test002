---
name: music-video
description: 生成音乐视频 MV 的 prompt。当用户需要"MV/音乐视频/music video/节奏感视频/嘻哈 MV/电子 MV/流行 MV/摇滚 MV/vibe MV"时自动调用。覆盖 7 大音乐流派的视觉语言（嘻哈、流行、电子、摇滚、R&B、独立、金属），节奏剪辑逻辑（cut on beat / beat drop），以及适配各视频模型的 prompt 格式。
---

# 音乐视频 (Music Video / MV)

MV 的本质：**视觉节奏匹配听觉节奏**。不是"给歌配画面"，而是"画面本身有节奏"。

## 调用时机

**强触发词**：
- MV / 音乐视频 / music video
- 嘻哈 MV / 摇滚 MV / 电子 MV / 流行 MV
- 节奏感 / vibe / 氛围感
- beat drop / 节奏卡点
- hip-hop / pop / rock / R&B / EDM / indie / metal

**典型请求**：
- "帮我做一个嘻哈 vibe 的 30 秒 MV"
- "电子音乐 beat drop 瞬间的视觉"
- "Billie Eilish 风格的 MV 镜头"

## MV 的三大内容类型

一个 MV 通常由这三种镜头混剪：

### 1. Performance 表演镜头
歌手/乐手正在唱/演奏。
- **作用**：建立"谁在表演"
- **占比**：40-60%
- **拍法**：特写嘴型、手部演奏、舞台光

### 2. Narrative 叙事镜头
有故事情节的片段。
- **作用**：传达歌词主题
- **占比**：20-40%
- **拍法**：按剧本拍，可以无歌手

### 3. Conceptual 概念镜头
抽象/超现实画面（不是真实场景）。
- **作用**：视觉记忆点、创意爆发
- **占比**：10-30%
- **例子**：漂浮的物体、超现实场景、几何图形

**好 MV 的秘诀**：三种镜头**穿插剪辑**，每 1-2 秒切换一种。

---

## 7 大音乐流派的视觉语言

### 1. Hip-Hop / Rap
- **关键元素**：街头、车、金链子、大额现金、品牌 logo、跳舞
- **色调**：高对比、霓虹或纯黑金
- **镜头**：鱼眼（舞动）、dolly zoom（炫耀）、低角度仰拍
- **节奏**：打击感强，beat drop 配大场景切换
- **Prompt 关键词**: `hip-hop music video aesthetic, urban streets, gold chains, low angle hero shots, Travis Scott-style distortion`

### 2. Pop / 流行
- **关键元素**：高饱和、干净场景、偶像单人特写
- **色调**：粉紫蓝绿等糖果色
- **镜头**：环绕、多机位、漂亮慢镜
- **节奏**：整齐切分，副歌时色彩爆炸
- **Prompt 关键词**: `pop music video, candy-colored palette, K-pop style, polished cinematography, Ariana Grande aesthetic`

### 3. 电子 / EDM
- **关键元素**：霓虹、激光、大场地、舞动人群
- **色调**：青洋红、冷蓝紫、频闪
- **镜头**：快速剪切、上帝视角、鱼眼、whip pan
- **节奏**：**build-up 缓慢累积** + **drop 瞬间爆炸** 是视觉焦点
- **Prompt 关键词**: `EDM music video, laser light show, strobing neon, dance crowd, beat drop energy, Daft Punk futuristic aesthetic`

### 4. Rock / 摇滚
- **关键元素**：乐器、舞台、人群、汗水
- **色调**：低饱和 / 单色、暖色灯光
- **镜头**：手持粗粝、特写吉他手指、鼓手背面
- **节奏**：跟吉他 riff 剪辑
- **Prompt 关键词**: `rock music video, gritty stage lighting, handheld raw footage, sweat and guitar close-ups, 70s rock aesthetic`

### 5. R&B / Soul
- **关键元素**：亲密场景、浴室、卧室、慢动作
- **色调**：暖棕、紫色、烟熏感
- **镜头**：特写唇部、环绕、浅景深
- **节奏**：慢、性感、呼吸感
- **Prompt 关键词**: `R&B music video, intimate moody lighting, smoky atmosphere, slow motion close-ups, The Weeknd aesthetic`

### 6. Indie / 独立
- **关键元素**：自然、复古、生活流
- **色调**：复古胶片感、柔和
- **镜头**：不修饰、vlog 感、自然光
- **节奏**：不规则、跟情感走
- **Prompt 关键词**: `indie music video, 16mm film aesthetic, natural daylight, vintage color grade, Lana Del Rey dreamy nostalgia`

### 7. Metal / 金属
- **关键元素**：舞台烟雾、血、破坏、动物
- **色调**：黑红、极端对比
- **镜头**：冲击、极端角度、慢动作暴力美学
- **节奏**：重击鼓点 = 极快切换
- **Prompt 关键词**: `metal music video, dark theatrical stage, red and black lighting, slow-motion destruction, intense close-ups`

---

## 节奏驱动的剪辑逻辑

MV 的核心是"**画面变化 = 音乐变化**"。

### BPM 与切镜频率对应表

| BPM | 类型 | 建议切镜频率 |
|-----|------|------------|
| 60-80 | Ballad / Ambient | 每 4-8 秒切一次 |
| 80-100 | R&B / Soft Pop | 每 2-4 秒 |
| 100-120 | Pop / Rock | 每 1-2 秒 |
| 120-140 | Dance / House | 每 0.5-1 秒 |
| 140-180 | EDM / Drum&Bass | 每 0.25-0.5 秒（单拍切） |

> AI 视频模型生成的是单片段（5-10 秒），**剪辑节奏在后期完成**，prompt 只负责"每段的视觉浓度"。

### Beat Drop 视觉策略

EDM/Hip-Hop/Pop 的 "Drop" 是视觉最重要时刻：

- **Build-up 铺垫段**：单调画面、色调收敛、慢镜头
- **Drop 爆发段**：色彩爆炸、快速切换、特效炸裂
- **Prompt 写法**（drop 瞬间）：
  ```
  Explosive visual moment: colors burst, multiple elements
  rapidly multiply, particles explode outward, strobing lights,
  extreme energy, beat drop visual climax.
  ```

### Call & Response 切镜

副歌 vs 主歌用不同视觉语言：
- **主歌**：单一场景、稳定镜头
- **副歌**：多场景快速切换、更多运动

---

## MV 的经典镜头库

### 1. Performance 镜头（表演类）
- **嘴部特写**：口型与歌词同步
- **Walking Towards Camera**：歌手朝镜头走来（King/Queen shot）
- **环绕旋转**：歌手中心 360° 环绕
- **低角度仰拍**：英雄感
- **手部演奏特写**：吉他/钢琴

### 2. Narrative 镜头（叙事类）
- **Breakup Scene**：雨中分手经典画面
- **Party Scene**：人群、红酒、慢动作
- **Driving Scene**：车内、窗外流光
- **Bedroom Intimate**：床上、纱帘、柔光

### 3. Conceptual 镜头（概念类）
- **漂浮**：主体漂浮在空中/水中
- **复制/分身**：同一人物多个副本
- **反重力**：物体逆向掉落
- **变形**：液体/烟雾形成主体
- **几何循环**：图案无限重复

---

## 10 秒 MV 片段的分镜策略

### 结构 A：Performance + Concept（最稳）
```
[0-3s] 歌手表演特写（嘴型/脸）
[3-6s] 概念镜头（超现实画面）
[6-9s] 歌手全身 + 环绕
[9-10s] Beat drop 视觉爆发
```

### 结构 B：Narrative + Performance
```
[0-2s] 故事场景（无歌手）
[2-5s] 歌手切入唱
[5-8s] 故事推进 + 歌手插入
[8-10s] 高潮定格
```

### 结构 C：Full Concept（艺术向）
```
[0-5s] 建立超现实场景
[5-10s] 场景变化 / 主体变形
```

---

## 模型适配

### Kling（推荐 performance 类）
对人物口型、手部演奏的刻画很好：
```
一位戴帽子的说唱歌手，胸前金链子，在霓虹灯下对着镜头说唱。
低角度仰拍，镜头缓慢推进。夜晚街头背景虚化，多色霓虹。
hip-hop MV 风格，节奏感强。
```

### Runway Gen-3（推荐 concept 类）
对抽象场景、特效的生成好：
```
Concept music video shot. A figure floating upside down in mid-air,
gravity reversed. Particle explosion expanding outward in slow motion.
Vibrant magenta and cyan duotone. EDM music video aesthetic, beat drop moment.
```

### Higgsfield Seedance 2.0（推荐复杂运镜）
```
Performance music video shot. Singer in center frame, camera orbits
360 degrees around them. Stage lighting from above, rim light from behind.
R&B aesthetic, slow-motion fabric flow.
```

### Luma Ray 2（推荐特效物理）
```
[Starting frame: singer with fabric backdrop]
Camera slow orbit. Fabric billows in slow motion, catching light rays.
Dust particles float upward. Dreamlike R&B music video atmosphere.
```

### Sora（推荐长剧本叙事 MV）
```
A 30-second music video in the style of [艺人名] from [年代]. The video opens
with [叙事片段], transitions to [表演片段], climaxes at [概念画面]...
```

---

## 避坑

1. ❌ **不要让 AI 模型生成真实歌词口型** — 基本会出戏
   ✅ 让唇语"大致对得上"就好，后期配音对时
2. ❌ **不要堆多个歌手** — AI 对多人物互动不稳
   ✅ 一个镜头一个主角
3. ❌ **不要期望精确的节奏卡点** — 5-10 秒片段没办法精确到帧
   ✅ 在剪辑端卡点（After Effects / DaVinci / Premiere）
4. ❌ **别用版权明星名字做 prompt**（部分模型会拒）
   ✅ 用"风格参考"："in the style of [流派]"而不是"看起来像周杰伦"

## 输出规范

```
## 🎵 [标题]（[流派] MV）

**风格**: [流派]
**BPM 参考**: [数字]
**镜头构成**: Performance [%] + Narrative [%] + Conceptual [%]

**分镜**
[0-3s] Performance: ...
[3-6s] Conceptual: ...
[6-10s] Narrative + Performance: ...

**Prompt**（按模型）

— Kling（推荐 performance）—
<中文 prompt>

— Runway（推荐 conceptual）—
<英文 prompt>

**剪辑建议**
后期需要：cut on beat，drop 处颜色爆发
```

## 质量自检

- [ ] 三种镜头类型至少有 2 种
- [ ] 流派视觉元素明确
- [ ] BPM 和切镜频率匹配
- [ ] Drop 瞬间有视觉爆发设计（如有）
- [ ] 单人主体（避免多人群像）
