---
name: fight-scenes
description: 生成打斗/动作场景视频 prompt。当用户需要"打斗/格斗/武打/战斗/对战/PK/boss战/action/combat/fight/choreography/武术/拳击/剑斗/空战"时自动调用。覆盖 3 大打斗风格（写实格斗/机甲怪兽/超能力动漫式）、打斗编排 5 要素、动作镜头语言、慢动作策略。内置 Higgsfield 安全词汇，引用 _shared/content-filter.md。
---

# 打斗场景 (Fight Scenes / Action Choreography)

打斗 ≠ 两个人互相打。**好的打斗是一段有节奏的舞蹈**，有预备、有高潮、有呼吸。每一拳都在讲故事。

## 调用时机

**强触发词**：
- 打斗 / 格斗 / 武打 / 战斗 / 对战 / PK
- boss 战 / 决斗 / 对决
- action / combat / fight / choreography
- 武术 / 拳击 / 剑斗 / 空战 / 追击

**典型请求**：
- "帮我做一个骑龙 vs 石像巨人的打斗"
- "John Wick 风格的近身搏斗 5 秒"
- "鬼灭之刃那种华丽的剑术对决"
- "环太平洋机甲 vs 怪兽的大场面"

---

## 打斗编排 5 要素

**每个打斗都必须定义这 5 项**，否则 AI 会给你"两个人站着互相推"。

### 1. Arena（战斗空间）
战斗在哪？空间本身影响战斗方式。
- **狭窄空间**（走廊、电梯）→ 近身肉搏、碰壁、利用环境
- **开阔空间**（广场、天空）→ 远程攻击、速度追击、飞行
- **垂直空间**（楼顶、悬崖）→ 坠落风险、高低差攻击
- **Prompt**: `battle takes place in [空间类型], [环境细节 2-3 个]`

### 2. Rhythm（节奏快慢）
打斗的灵魂。**好打斗 = 快慢交替**，不是全程快或全程慢。
- **蓄力 → 爆发**: 慢动作预备 → 瞬间释放
- **连击 → 喘息**: 3-4 下快攻 → 1 秒停顿
- **追击 → 反转**: 一方追一方逃 → 突然反击
- **Prompt**: `rhythm alternates between rapid exchanges and brief pauses`

### 3. Power Scale（力量层级）
谁强谁弱？力量差决定战斗策略。
| 对局 | 策略 | 视觉 |
|------|------|------|
| 势均力敌 | 技巧对决 | 对称构图 |
| 以小博大 | 速度 vs 力量 | 尺寸对比 |
| 以一敌多 | 灵活走位 | 环绕运镜 |
| Boss 战 | 弱点攻略 | 远全景→微距 |

### 4. Stakes（情感赌注）
打斗为什么重要？没有赌注的打斗是无聊的。
- 保护某人 / 复仇 / 生死存亡 / 证明自己 / 阻止灾难
- **Prompt**: 在打斗前加一个"决意镜头"（特写眼神/握拳）

### 5. Signature Move（招牌动作）
每个角色要有一个**只属于他**的视觉标记。
- Owen 的招牌：双手引燃光剑（luminance blade formation）
- 旺财的招牌：蓝白高温光束（blue-white radiant energy beam）
- 石像的招牌：石剑慢速横扫（massive stone greatsword slow sweep）

---

## 3 种打斗风格

### 风格 1: 写实格斗（John Wick / 谍影重重）

**视觉特征**：
- 手持摄影 + 轻微晃动
- 近距离（中景到特写）
- 快速反应（拳头特写 → 反应切面部）
- 环境互动（用桌子挡、用书砸、用铅笔插）
- 低饱和色调

**节奏**：每 0.5-1 秒一次动作变化

**Prompt 关键词**：
```
Realistic close-quarters combat, handheld camera with subtle shake,
medium to close-up framing, rapid exchanges, environmental interaction,
desaturated color grade, John Wick-style tactical choreography
```

### 风格 2: 机甲 / 怪兽（Pacific Rim / 哥斯拉）

**视觉特征**：
- 巨大尺度感（仰拍为主）
- 慢动作接触瞬间（speed ramp from fast to slow）
- 地面震动效果（碎片弹起、水花溅起）
- 远景→中景快速切换
- 深蓝+橙色对比调色

**节奏**：2-3 秒一次重型动作

**Prompt 关键词**：
```
Colossal scale combat between titans, extreme low angle emphasizing
height, speed ramping from motion to slow contact moment, ground
trembling with debris rising, deep blue and warm orange color contrast,
Pacific Rim-scale choreography
```

### 风格 3: 超能力 / 动漫式（鬼灭之刃 / 火影忍者）

**视觉特征**：
- 特效线条（speed lines / energy trails）
- 接触定格帧（freeze frame at the moment of contact）
- 色彩爆发（能力释放时画面色温骤变）
- 远景大全景 → 瞬间切到微距特写
- 高饱和色调

**节奏**：超慢铺垫 → 爆炸性快速 → 定格

**Prompt 关键词**：
```
Anime-style superhuman combat, dynamic energy trails following movement,
freeze-frame at peak contact moment with radial particle scatter,
dramatic color temperature shift during ability release, extreme
contrast between wide establishing shots and sudden macro close-ups
```

---

## 动作镜头词典

| 技巧 | 英文术语 | 效果 | Prompt 写法 |
|------|---------|------|------------|
| 速度渐变 | Speed Ramping | 快→慢→快 | `speed ramps from fast motion to slow contact moment` |
| 接触定格 | Contact Frame | 拳/剑击中瞬间冻结 | `freeze frame at the exact moment of contact` |
| 反应切 | Reaction Cut | 被打者面部反应 | `cut to close-up of opponent's reaction` |
| 一镜到底 | Oner | 不切镜的连续打斗 | `unbroken continuous shot following the action` |
| 快速横摇 | Whip Pan | 极快转场 | `whip pan transition between combatants` |
| 冲击推进 | Crash Zoom | 突然推近 | `sudden crash zoom into the action` |
| 环绕追踪 | Orbit Track | 绕战斗者旋转 | `camera orbits around the fighters during exchange` |
| 主观视角 | POV | 从角色眼睛看 | `first-person POV of the protagonist during combat` |

---

## ⚠️ Higgsfield 安全词汇（打斗是高危区！）

打斗场景是 Higgsfield banned words 触发最密集的领域。**必须逐词检查**。

> 完整替换表见 `_shared/content-filter.md`

### 打斗场景常用的替换

| 你想写的 | Higgsfield 会拦截 | 改成这样写 |
|---------|------------------|-----------|
| The sword impacts the shield | impact | The sword makes contact with the shield |
| Fist smashes into face | smashes | Fist transitions into the opponent's guard |
| Explosion of debris | explosion | Radial particle scatter of debris |
| Fire blast from dragon | fire | Radiant energy projection from the dragon |
| Flames engulf the enemy | flames | Warm amber glow envelops the opponent |
| Shield cracks open | cracks | Shield opens along the edge |
| The titan is destroyed | destroyed | The titan dissolves into particles |
| Violent clash of weapons | violent | Dynamic clash of weapons |
| Building explodes | explodes | Building separates into a dynamic reveal |
| Crushing blow | crushing | Forceful contact |

---

## 慢动作策略

### 何时用慢动作
- ✅ 接触瞬间（拳头碰到脸的那 0.2 秒）
- ✅ 翻身闪避（子弹时间）
- ✅ 招牌动作释放（光剑点亮瞬间）
- ✅ 碎片/粒子/液体飞散
- ❌ 跑步/移动（会显得拖沓）
- ❌ 对话/喊叫

### 视觉效果对比
| 效果 | Prompt 描述 |
|------|------------|
| 微慢（0.7x） | `slightly slow motion, preserving momentum` |
| 经典慢（0.3x） | `dramatic slow motion, details visible in the motion` |
| 子弹时间（0.1x） | `extreme slow motion freeze, every particle visible` |
| 速度渐变 | `speed ramps from real-time to slow motion and back` |

---

## 5 秒打斗片段分镜模板

### 结构 A: 单次交锋（最稳）
```
[0-1s]  预备    双方对峙，微表情特写
[1-3s]  交锋    快速动作 + speed ramp 到慢动作接触
[3-4s]  结果    被击中方的反应 / 后退 / 倒地
[4-5s]  落幕    胜者站姿 / Hero shot
```

### 结构 B: 追击型
```
[0-2s]  追      追击者快速逼近，被追者闪避
[2-3s]  转      被追者突然反击
[3-5s]  锁      反击成功，形势逆转
```

### 结构 C: Boss 战高潮（适合旺财 vs 石像）
```
[0-1s]  冲刺    主角冲向 Boss，camera 跟拍
[1-3s]  弱点    瞄准并攻击 Boss 弱点（胸口符文水晶）
[3-4s]  崩解    Boss 开始瓦解，粒子飞散
[4-5s]  余震    主角落地，碎片漂浮定格
```

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Dynamic combat sequence. @owen in luminance warrior form leaps from
the back of a colossal ember-scaled dragon (Wangcai). He forms a
radiant energy blade mid-air. Speed ramps to slow motion as he
makes contact with the stone titan's chest crystal. The crystal
separates cleanly, golden particles scattering outward in a radial
pattern. The titan begins to dissolve, segments opening along
visible seams. Camera performs a 180-degree orbit during the
slow-motion moment. Warm amber glow emanates from the
disintegrating form. IMAX anamorphic cinematography.
```

### Kling（中文）
```
动态战斗场景。Owen 身穿火焰战士铠甲从巨型火龙旺财背上跃起，
空中凝聚出一把光剑。慢动作推进到他的剑刺穿石像巨人胸口的
紫色符文水晶的瞬间。水晶碎裂，金色粒子四散飞溅。石像开始
崩解倒塌。相机在慢动作瞬间做 180 度环绕。IMAX 电影级运镜。
```

### Runway Gen-3
```
Epic combat scene. A warrior in ember-glowing armor leaps from a
massive Western dragon and strikes a colossal stone titan's chest
crystal with a luminous energy blade. Speed ramps to extreme slow
motion at the moment of contact. The crystal shatters outward in
golden particle scatter. The titan begins crumbling, chunks
separating and floating. 180-degree orbital camera during the
slow-motion strike. Cinematic anamorphic lens, warm orange versus
cold purple color contrast.
```

### Luma Ray 2
```
Starting frame: [warrior mid-leap toward stone titan]
Motion: Speed ramp from fast to extreme slow at crystal contact.
Golden particles scatter radially. Titan crumbles in slow motion.
Camera: 180° orbit during slow motion.
Style: IMAX cinematic, warm vs cool contrast.
```

### Sora
```
A 5-second combat sequence in Pacific Rim meets Dune aesthetic.
A fire-armored warrior riding a massive Western dragon engages
a 20-story ancient stone titan in aerial combat. The warrior
leaps from the dragon's back, forming a blade of pure radiant
energy mid-air. Time slows dramatically as the blade pierces
the titan's exposed chest crystal. The crystal fractures in
slow motion, releasing golden particle streams outward.
The stone titan begins to dissolve from the point of contact,
segments separating and floating apart. Camera performs a
dramatic 180-degree orbit around the frozen moment of contact.
Color palette: warm amber and gold versus cold violet and granite.
Anamorphic widescreen, IMAX-scale cinematography.
```

---

## 避坑

1. ❌ **堆太多动作**（5 秒最多 1-2 个核心动作）→ 多了全糊
2. ❌ **两个角色同时复杂动作**（AI 对多主体互动不稳）→ 一次聚焦一方
3. ❌ **用 Banned Words**（打斗 prompt 最容易中招）→ 每次生成前过 content-filter
4. ❌ **忽略速度渐变**（全程匀速的打斗像机器人）→ 必须有快慢对比
5. ❌ **不设战斗空间**（没有环境的打斗像绿幕棚拍）→ 先描述 Arena
6. ❌ **要求精确的打斗编排**（AI 不能精确到"左拳打右脸"）→ 描述整体动态和情绪

## 输出规范

```
## ⚔️ [标题]（[风格]打斗）

**风格**: [写实 / 机甲 / 超能力]
**Arena**: [战斗空间]
**Power Scale**: [对局类型]
**Stakes**: [情感赌注]

**分镜**
[0-Xs] ...
[X-Ys] ...

**Prompt**（按模型）

— Higgsfield Seedance 2.0（⚠️ 已过 content-filter）—
<prompt>

— Kling —
<中文 prompt>

**编排说明**
一段中文说明为什么选这个节奏和运镜
```

## 质量自检

- [ ] 5 要素全部定义（Arena/Rhythm/Power Scale/Stakes/Signature Move）
- [ ] 有快慢节奏对比（不是匀速）
- [ ] 5 秒内核心动作不超过 2 个
- [ ] 单个镜头聚焦单个角色的动作
- [ ] Higgsfield prompt 不含任何 banned word
- [ ] 有明确的 "接触瞬间" 慢动作设计
