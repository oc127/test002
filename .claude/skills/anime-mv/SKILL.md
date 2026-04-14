---
name: anime-mv
description: 生成动漫风格视频 prompt。当用户需要"动漫/二次元/新海诚/宫崎骏/京阿尼/赛璐璐/anime style/Ghibli/Makoto Shinkai"的视频时自动调用。覆盖 4 大流派（新海诚光影派、宫崎骏生命派、京阿尼日常派、赛璐璐动作派）、动漫特有视觉元素（光线粒子、天空、情感定格、运动线）、BGM-驱动的节奏设计，并适配海外视频模型。
---

# 动漫风格视频 (Anime MV)

动漫 ≠ 把真实画面加滤镜。它是一套**完全独立的视觉语言**：光是物理上不存在的，天空占画面一半以上，情感用静帧表达而不是动作。

## 调用时机

**强触发词**：
- 动漫 / 二次元 / 番剧 / 动画
- 新海诚 / 宫崎谿 / 京阿尼 / 京都动画
- Makoto Shinkai / Studio Ghibli / Kyoto Animation
- anime / cel-shading / 赛璐璐
- J-pop MV / 日系 MV

**典型请求**：
- "帮我做个新海诚风格的黄昏车站告别"
- "宫崎崎风格的森林少女"
- "京阿尼日常感的校园上学"
- "给 Kling 写一个动漫公路片"

## 4 大动漫流派

选流派 = 选视觉风格 + 叙事节奏。**每个流派不混用**。

### 流派 1: 新海诚派 (Makoto Shinkai Style)

**代表作**：《你的名字》《天气之子》《铃芽之旅》

**视觉特征**：
- **光的粒子化**：阳光穿透、雨滴反光、尘埃漂浮，光本身成为主体
- **天空占比**：天空占画面 50-70%，多云彩、晚霞、星空
- **城市与自然并置**：东京街景 + 细腻自然光
- **高饱和度 + 冷暖对比**：天空蓝到夸张，夕阳橙到炸裂

**节奏**：
- 慢、静、抒情
- 大量"空境"（无人物的场景）
- 情感靠光和风暗示，不靠动作

**Prompt 关键词**：
```
Makoto Shinkai anime style, hyperrealistic lighting,
volumetric god rays, floating dust particles, vibrant sky
dominating 60% of frame, cel-shaded characters against
detailed photorealistic backgrounds, emotional stillness,
"Your Name" aesthetic
```

### 流派 2: 宫崎骏派 (Studio Ghibli Style)

**代表作**：《千与千寻》《天空之城》《龙猫》《哈尔的移动城堡》

**视觉特征**：
- **手绘感**：水彩背景 + 柔和线条 + 颜料质感
- **自然元素统治**：森林、云、风、水、火焰 都有"生命"
- **暖色调**：泥土橙、森林绿、天空蓝，饱和度适中
- **圆润角色**：面部圆润、动作柔软

**节奏**：
- 中速，带呼吸感
- 自然环境大量铺陈
- 强调"生活感"的小动作

**Prompt 关键词**：
```
Studio Ghibli style, hand-painted watercolor backgrounds,
soft organic lines, rounded character design, warm earthy
palette, whimsical atmosphere, natural elements feel alive,
Hayao Miyazaki aesthetic, "Spirited Away" aesthetic
```

### 流派 3: 京阿尼派 (Kyoto Animation Style)

**代表作**：《凉宫春日》《冰菓》《吹响!上低音号》《利兹与青鸟》

**视觉特征**：
- **日常细节**：书包晃动、头发丝、校服褶皱
- **柔和高光**：皮肤、眼睛有微妙反光
- **色彩温和**：低饱和、高明度
- **细腻微表情**：眨眼、颤抖、低头

**节奏**：
- 非常慢，日常流水账
- 一个平凡动作拉长到极致
- 情感用"犹豫的一瞬"表达

**Prompt 关键词**：
```
Kyoto Animation style, meticulous daily life details,
soft pastel palette, subtle highlights on hair and skin,
delicate micro-expressions, school uniform textures,
"Hyouka" aesthetic, slice-of-life calm
```

### 流派 4: 赛璐璐动作派 (Classic Cel-Shaded Action)

**代表作**：《火影忍者》《进击的巨人》《鬼灭之刃》《DEMON SLAYER》

**视觉特征**：
- **强线条**：角色轮廓粗黑线
- **冲击定格**：动作瞬间静止 + 效果线
- **高饱和对比色**：血红、电蓝、火橙
- **速度线 + 特效爆发**

**节奏**：
- 快慢交替：超慢铺垫 + 爆炸高速
- 必须有"定格瞬间"（1-2 帧的大特写）
- 声效节奏驱动

**Prompt 关键词**：
```
Classic cel-shaded anime action, bold black outlines,
dramatic impact frames, speed lines, vibrant saturated colors,
freeze-frame moments, explosive effects, "Demon Slayer" aesthetic
```

---

## 动漫专属的 5 个视觉元素

任何动漫 prompt 都应至少覆盖 2-3 个：

### 1. 光粒子 (Light Particles)
- 阳光中的尘埃、飘落的花瓣、萤火虫、雪花、樱花吹雪
- **Prompt**: `floating light particles, sakura petals drifting, dust motes in sunbeams`

### 2. 天空占比 (Sky Dominance)
- 天空占画面 40-70%，非常规构图
- **Prompt**: `vast sky occupying upper 2/3 of frame, dramatic cloud formations`

### 3. 情感定格 (Emotional Still)
- 角色停下来凝视某物 1-2 秒
- **Prompt**: `character pauses, gazing at [目标], silent emotional beat`

### 4. 发丝/服饰动态 (Hair/Clothing Dynamics)
- 头发被风吹起、裙摆飞扬、围巾飘动
- **Prompt**: `hair flowing in the wind, clothing fabric dynamic motion`

### 5. 眼部高光 (Eye Highlights)
- 瞳孔反射星光、泪水、灯光
- **Prompt**: `detailed eye highlights reflecting [反射内容]`

---

## 动漫 MV 的 3 段式结构（15-60 秒）

```
[前段 30%]  日常 / 铺垫  →  慢速、大量空境、角色日常
[中段 50%]  转折 / 冲突  →  速度对比（慢→快）、情绪爆发
[尾段 20%]  高潮 / 余韵  →  定格 + 天空 + 留白
```

**关键**：动漫 MV 最忌"信息量匀速"，必须有**节奏起伏**（快慢、远近、明暗对比）。

---

## 情绪 → 流派 映射

| 情绪目标 | 流派 | 关键词 |
|---------|------|--------|
| 青春、初恋 | 新海诚 | 黄昏、站台、校服、远距离凝视 |
| 冒险、奇幻 | 宫崎骏 | 森林、飞行、未知生物、风 |
| 日常、治愈 | 京阿尼 | 教室、文化祭、小动作 |
| 热血、打斗 | 赛璐璐 | 冲击、特效、吼叫、决心 |
| 孤独、离别 | 新海诚 | 雨、电车、背影、单人 |
| 亲情、家庭 | 宫崎崎 | 餐桌、田园、温馨配色 |
| 校园爱恋 | 京阿尼 | 社团活动、走廊偶遇 |
| 超能力、异世界 | 赛璐璐 | 能力觉醒、战斗展开 |

---

## 模型适配

### Kling（最推荐，支持日系审美好）
中文 prompt 直接描述流派：
```
新海诚风格动漫。黄昏时分东京的电车站台，少女站在月台边缘，
长发被风吹起，夕阳把天空染成粉橙色。飞舞的樱花花瓣，
阳光穿透云层形成可见光柱。相机缓慢推进，浅景深。
```

### Runway Gen-3
英文 + 明确流派参考：
```
Makoto Shinkai anime style. Dusk at a Tokyo train station.
A high school girl in uniform stands at the platform's edge,
long hair flowing in the breeze. Sky painted in pink and orange,
dramatic clouds, volumetric god rays. Sakura petals drift through
air. Camera slowly pushes in. Cel-shaded character, hyperrealistic
background, "Your Name" aesthetic.
```

### Higgsfield Seedance 2.0
```
Anime sequence in Makoto Shinkai style. [Subject] [Action] at
[location]. Vibrant sky dominating the frame. Light particles
floating. Slow cinematic camera move. Cel-shaded anime aesthetic.
```

### Luma Ray 2
图生视频特别适合动漫——先用 Midjourney / NovelAI / Ideogram 出关键帧：
```
Starting frame: [anime key visual]
Camera: slow pan, wind effect
Motion: hair and clothing flow, clouds drift across sky
Style: Makoto Shinkai anime
```

### Sora
长剧本风格：
```
An anime sequence in the style of Makoto Shinkai's "Your Name".
The scene opens with a high school girl in a navy sailor uniform
standing on a train platform at sunset. The sky dominates the top
60% of the frame, painted in vibrant oranges and pinks with
layered clouds. Dust particles and sakura petals float through
volumetric god rays. Her long black hair flows gently in the
evening breeze. The camera slowly pushes in from a medium wide
shot to a close-up of her face, which shows a quiet, bittersweet
longing. Cel-shaded characters against hyperrealistic
watercolor-painted backgrounds.
```

---

## 动漫视频的 5 个禁忌

1. ❌ **堆砌真实摄影术语**（"35mm film grain"）→ 破坏二次元感
2. ❌ **描述真人肤色细节**（"realistic skin pores"）→ 让角色变成 3D
3. ❌ **要求多角色复杂互动**（多人打斗）→ 动漫 AI 视频会崩
4. ❌ **混用不同流派**（"新海诚+宫崎骏"）→ 结果既不像那个也不像这个
5. ❌ **省略天空**（只拍角色正面大头）→ 失去动漫经典构图

## 输出规范

```
## 🌸 [标题]（[流派]风格）

**核心概念**: ...

**流派**: [新海诚 / 宫崎骏 / 京阿尼 / 赛璐璐]

**视觉元素** (至少选 3 个)
- [ ] 光粒子
- [ ] 天空占比
- [ ] 情感定格
- [ ] 发丝/服饰动态
- [ ] 眼部高光

**3 段式分镜**
[前段] ...
[中段] ...
[尾段] ...

**Prompt**（按模型）

— Kling（推荐）—
<中文 prompt>

— Runway Gen-3 —
<英文 prompt>

**选型理由**
一段中文说明为什么选这个流派和这些元素
```

## 质量自检

- [ ] 流派明确且只选一个
- [ ] 至少 3 个动漫专属视觉元素
- [ ] 有情感定格瞬间
- [ ] 天空/环境占比合理
- [ ] 节奏有快慢对比
