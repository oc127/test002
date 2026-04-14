# 模型 Adapter — 不同视频模型的 Prompt 格式

同一个创意，翻译成 5 个主流海外模型能吃的格式。**每个模型有自己的语法偏好**，照搬会拉胯。

---

## 通用原则（所有模型）

1. **具体 > 抽象**：`woman in red silk dress` > `beautiful woman`
2. **动作 > 形容词**：`slowly turning` > `graceful`
3. **可视元素 > 情感描述**：`rain drops on glass` > `sad mood`
4. **明确时序**：用 `then`, `while`, `as` 标明动作先后
5. **避免否定**：不要说 "no people"，改说 "empty street"（多数模型对否定识别不稳定）

---

## 1. Higgsfield Seedance 2.0

### 特点
- 专攻电影运镜，有预设的 camera action 库
- 对"Motion Preset"关键词识别度高
- 理解中英双语，但英文更稳

### Prompt 格式
```
[Shot Type] + [Subject + Action] + [Camera Move] + [Lighting] + [Aesthetic / Style Reference]
```

### 官方运镜关键词（优先用这些）
- `push in` / `pull out`
- `tracking shot` / `follow shot`
- `orbit` / `360 rotation`
- `dolly zoom`
- `crane up` / `crane down`
- `handheld`
- `whip pan`

### 示例
```
Medium close-up shot of a woman in a red silk dress standing in a neon-lit alley.
Slow dolly zoom effect as she turns her head toward the camera.
Rain falling, puddles reflecting cyan and magenta neon signs.
Cinematic, shot on Kodak 500T, Blade Runner aesthetic,
shallow depth of field, rim light from behind.
```

### 官方建议
- 长度：80-150 词最佳
- 风格关键词放末尾："cinematic, shot on [胶片], [导演名] style"
- 支持 image-to-video（先出关键帧图，再驱动运动）

### 注意事项
- 不能描述过于复杂的多人互动（模型会"抢戏"）
- 避免特效词堆砌（"explosion, fire, smoke, fog, lightning"全堆会崩）

---

## 2. Runway Gen-3 / Gen-4

### 特点
- 有 **Camera Control 面板**（UI 里选），prompt 写风格和主体为主
- 理解自然语言描述运镜但精度一般
- 对电影术语识别好

### Prompt 格式
```
[Camera Move]. [Subject Description]. [Setting]. [Lighting]. [Style].
```
**每一句用句号分隔**（Gen-3 对句号敏感）。

### 示例
```
Slow push in toward the subject. A woman in a red silk dress stands in a narrow alley, neon signs flickering behind her. Wet cobblestones reflect cyan and magenta lights. Low-key lighting with strong rim light from behind. Shot on anamorphic lens, shallow depth of field, cinematic Blade Runner aesthetic.
```

### Runway 特有关键词
- `shot on 35mm film` / `anamorphic lens`
- `shallow depth of field` / `bokeh`
- `cinematic color grade`
- `realistic skin texture` （修肤色用）
- `detailed facial features` （避免崩脸）

### 限制
- 单次 prompt 建议 ≤ 120 词（截断后影响生成）
- 4 秒 / 10 秒两档，Gen-3 Turbo 更快
- 可用 `--seed` 固定种子（批量同主体时用）

### 最佳实践
- **简洁、分句、每句一个意思**
- 风格参考别堆太多（选 1-2 个导演/电影）

---

## 3. Kling AI (1.6 / 2.0)

### 特点
- 中英文都好，**中文支持甚至更好**（快手出品）
- 对"运动物理"理解强（真实的重力、惯性）
- 人物动作自然度行业领先

### Prompt 格式（推荐中文）
```
[景别] + [主体及其状态] + [动作描述] + [场景氛围] + [运镜] + [风格]
```

### 示例（中文）
```
中近景镜头。一位身穿红色丝绸旗袍的女性站在霓虹灯下的窄巷中。
她缓慢转头看向镜头，丝绸在湿气中微微贴身。
雨水落在积水的石板路上，映出青色和洋红色霓虹倒影。
镜头缓慢推进，浅景深，背景虚化，电影胶片质感，王家卫风格，2.35:1 宽银幕。
```

### 示例（英文）
```
Medium close-up. A woman in a red silk qipao stands in a narrow alley lit by neon.
She slowly turns her head toward the camera, silk clinging to her body in the humid air.
Rain falls on wet stone pavement, reflecting cyan and magenta neon.
Camera slowly pushes in, shallow depth of field, cinematic film grain,
Wong Kar-wai aesthetic, 2.35:1 widescreen.
```

### Kling 特有优势
- **多主体互动更稳**（两人对话、多人群戏）
- **光影过渡自然**（不会突然变色）
- **可以描述"开始-结束"状态**：`she starts with closed eyes, then slowly opens them`

### 注意事项
- 中文 prompt ≤ 250 字，英文 ≤ 200 词
- 复杂运镜（如 dolly zoom）有时执行不到位，建议简单运镜 + 好光影
- 竖屏生成质量不如横屏

---

## 4. Luma Dream Machine / Ray 2

### 特点
- **关键帧控制**：可以指定起始帧 + 结束帧图像，模型补中间
- 运镜描述用参数化：`low_angle`, `orbit_left`
- 物理模拟极强（水、烟、布料）

### Prompt 格式（两种模式）

**模式 A：纯文本**
```
[Subject + Setting + Action + Camera + Style]
```

**模式 B：关键帧 + 文本**（推荐）
- 起始帧：上传一张图
- 结束帧：上传另一张图（可选）
- 文本：描述运动过程
  ```
  The subject [动作] while the camera [运动].
  Lighting shifts from [起始] to [结束].
  Style: [cinematic / anime / 3D]
  ```

### 示例
```
A woman in a red silk dress in a neon-lit alley slowly turns toward the camera
as rain intensifies and the camera pushes in.
Light transitions from dim ambient to bright neon-reflected puddles.
Cinematic realism, shallow depth of field, shot on anamorphic lens.
```

### Luma Ray 2 的物理词汇（独特优势）
- `realistic fabric physics`
- `natural hair motion`
- `water splashing realistically`
- `smoke dispersing naturally`

### 注意事项
- Prompt ≤ 100 词（Luma 对长 prompt 不敏感）
- 起始帧质量决定成片质量（先用 Midjourney/Ideogram 出关键帧）
- 不适合宏大场面，擅长中景人物/物体

---

## 5. OpenAI Sora

### 特点
- 理解自然语言描述**最接近人类思维**
- 可以写**像电影剧本**一样的长 prompt
- 物理一致性业界顶尖

### Prompt 格式
```
[一段自然语言的完整描述，像小说/剧本片段]
```

### 示例（长 prompt）
```
A young woman in a red silk qipao stands at the entrance of a narrow Hong Kong
alley in the 1990s. Neon signs in Chinese and English flicker above her, casting
cyan and magenta reflections on the wet cobblestones. A light rain falls.

The camera slowly pushes in from a medium distance to a close-up as she turns
her head to look directly into the lens. Her expression is unreadable —
somewhere between sadness and defiance. Her silk dress catches the rain,
clinging slightly to her shoulder.

The scene is shot on an anamorphic lens with shallow depth of field. Background
neon signs are out of focus, rendered as colorful bokeh. The aesthetic is
reminiscent of Wong Kar-wai's "In the Mood for Love" — nostalgic, melancholic,
richly textured. Shot on Kodak 500T film stock, with visible grain.
```

### Sora 特有能力
- **多场景连续描述**（30-60 秒片段）
- **角色一致性**（同一人物跨镜头）
- **读脚本式输入**

### 注意事项
- Prompt ≤ 500 词（可以很长，但要有逻辑）
- 排队时间长（目前）
- 不支持特定风格参考（迪士尼、皮克斯等受版权限制）

---

## 模型选择决策表

| 需求 | 首选模型 | 原因 |
|------|---------|------|
| 电影级运镜 | Higgsfield Seedance 2.0 | 运镜库专业 |
| 人物动作自然 | Kling 2.0 | 动作流畅，物理强 |
| 抽象艺术/梦境 | Sora | 创造性最强 |
| 物理真实（水、烟、布料） | Luma Ray 2 | 物理模拟顶尖 |
| 电影质感 + 快速迭代 | Runway Gen-3 | 平台工具链完整 |
| 竖屏短视频 | Kling / Runway | 支持好 |
| 图生视频 | Luma / Kling | 关键帧控制强 |
| 长 prompt 复杂场景 | Sora | 语义理解最好 |

---

## 跨模型通用技巧

### 保持同主体跨多镜头
- **Runway**：用 `--seed <数字>` 固定
- **Kling**：上传参考图 + prompt
- **Sora**：一次生成长段，避免拼接
- **Luma**：用相同起始帧
- **Higgsfield**：用 character consistency 功能

### 提升质感的通用词
```
- shot on [film stock]: Kodak 500T / Cinestill 800T / Fuji 16mm
- anamorphic lens / 35mm film
- shallow depth of field / bokeh
- cinematic color grade / teal and orange
- film grain / natural grain
- practical lighting / volumetric light
- golden hour / blue hour
- cinematography by [导演/摄影师名]
```

### 避免使用的词（所有模型）
- `photorealistic`（多数已默认是真实感，加这个反而会僵）
- `amazing / beautiful / stunning`（形容词空词）
- `very, very X`（重复词模型会困惑）
- `not X`（否定性描述识别率低）
