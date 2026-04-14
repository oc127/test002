---
name: cinematic-video
description: 生成电影级 AI 视频 prompt。当用户需要"电影感/史诗感/大片感/剧情向/电影镜头/cinematic"的短视频、预告片、MV、叙事片段时自动调用。覆盖 5 段式叙事框架、运镜语言、光照设计、构图法则，并适配 Higgsfield Seedance 2.0 / Runway Gen-3 / Kling / Luma / Sora 等主流海外视频模型的 prompt 格式。
---

# 电影级视频生成 (Cinematic Video)

把一句朦胧的创意，翻译成电影级 AI 视频模型能精准执行的结构化 prompt。

## 调用时机

**强触发词**（用户说出这些词时直接调用本 skill）：
- 电影感 / 大片感 / 史诗感 / 剧情感 / 质感
- cinematic / filmic / movie-like / epic
- 预告片 / trailer / 短片 / MV
- 电影镜头 / 运镜 / 分镜 / 镜头语言

**典型请求示例**：
- "帮我做一个赛博朋克雨夜追车的 10 秒短片"
- "生成一段末日废土的史诗感开场"
- "我想要王家卫那种慢镜头感觉"
- "给 Runway Gen-3 写一个悬疑氛围的 prompt"

## 工作流

1. **解析创意** → 抽取主题 / 情绪 / 时长 / 目标平台（用户没说就问）
2. **选叙事框架** → 见 [`references/narrative-frameworks.md`](references/narrative-frameworks.md)
3. **设计镜头语言** → 查 [`references/camera-moves.md`](references/camera-moves.md)
4. **配光照方案** → 查 [`references/lighting.md`](references/lighting.md)
5. **定构图** → 查 [`references/composition.md`](references/composition.md)
6. **适配模型格式** → 查 [`references/model-adapters.md`](references/model-adapters.md)
7. **交付 + 解释** → 给 prompt 附一句"为什么这样架构"

## 电影 prompt 的 6 要素 (Six Pillars)

任何电影级 prompt 必须覆盖这 6 个维度，缺一个画面就会"发虚"：

| # | 维度 | 问题 | 示例 |
|---|------|------|------|
| 1 | **主体** (Subject) | 谁/什么是焦点？ | 一个戴机械义肢的女性杀手 |
| 2 | **动作** (Action) | 在做什么，朝哪个方向？ | 慢动作转身掏枪，子弹壳划过镜头 |
| 3 | **场景** (Scene) | 在哪里，氛围什么样？ | 雨夜霓虹巷道，积水反光 |
| 4 | **镜头** (Camera) | 怎么拍？推拉摇移？焦段？ | 手持低角度跟拍，35mm，浅景深 |
| 5 | **光照** (Lighting) | 光从哪来，什么颜色？ | 左侧青色霓虹主光 + 右侧品红补光 |
| 6 | **风格** (Aesthetic) | 胶片感？色调？年代感？ | 柯达 500T 胶片，冷青-洋红色调，1990s 港片质感 |

**缺失检查**：输出前 Claude 必须确认 6 个都填了。任何一项缺失要么从上下文补全，要么主动问用户。

## 2 秒钩子原则

前 2 秒决定观众留存率。电影短视频的开头必须：
- **视觉冲击** > 叙事铺垫（先抓住眼球再讲故事）
- **动态 > 静态**（动作镜头比静止画面钩子率高 3x）
- **反差 > 平铺**（色彩/尺度/速度的对比）

具体 12 种钩子公式见 `ecommerce-video` skill 的 `hook-formulas.md`（两个 skill 共用）。

## 情绪 → 镜头语言 决策树

快速映射：用户说出情绪，Claude 直接查表选运镜和光照。

| 情绪基调 | 推荐运镜 | 推荐光照 | 色调 | 焦段 |
|---|---|---|---|---|
| 紧张 / 悬疑 | 手持跟拍、crash zoom、dutch angle | 硬光 + 大阴影 | 冷青蓝 | 35mm / 长焦压缩 |
| 史诗 / 宏大 | 航拍、dolly out 拉远、升降镜头 | 黄金时刻 + 逆光 | 橙金 / 暖调 | 广角 16-24mm |
| 浪漫 / 唯美 | 慢推、环绕、升格慢动作 | 柔光 + 黄金时刻 | 粉金 / 暖调 | 85mm 浅景深 |
| 冰冷 / 孤独 | 长焦压缩、固定镜头、极缓慢推 | 单一硬光源 + 冷色 | 蓝灰 | 长焦 85-135mm |
| 混乱 / 疯狂 | whip pan、快速剪切、手持晃动 | 霓虹混色 / 频闪 | 洋红青碰撞 | 鱼眼 / 广角畸变 |
| 怀旧 / 伤感 | 固定镜头、缓慢摇镜 | 窗光 + 丁达尔光 | 棕黄褪色 | 50mm 标准 |
| 赛博朋克 | dolly zoom、低角度仰拍 | 霓虹多光源 | 青-洋红双色 | 24mm 广角 |
| 末日废土 | 低饱和航拍、手持跟拍 | 硬顶光 + 扬尘 | 棕土色 / 低饱和 | 广角 24-35mm |

## 5 段式叙事框架（10-60 秒短片通用）

见 [`references/narrative-frameworks.md`](references/narrative-frameworks.md) 详解。简版：

```
[0-2s]  Hook 钩子      → 视觉冲击 / 反差 / 悬念
[2-5s]  Setup 建立     → 交代角色、场景、核心冲突
[5-8s]  Rising 推进    → 情绪升级、镜头加速
[8-12s] Climax 高潮    → 最强画面、情绪顶点
[12-15s] Payoff 收尾   → 留白 / 余韵 / 下一幕暗示
```

## 关键约束（硬性）

- **不要堆砌形容词**：AI 视频模型对形容词不敏感，对具体动作+具体视觉元素敏感。"美丽的女孩"→"穿红色丝绸旗袍的女人，发梢被风吹起"
- **运镜只选 1-2 个**：多了模型会懵。10 秒短片最多 2 次运镜切换
- **时间锚点具体**：用"[0-2s]"标注，不用"刚开始"
- **色彩用具体参考**：不说"复古色调"，说"柯达 Gold 200 胶片色"或"WongKarWai-style teal and orange"
- **控制 prompt 长度**：Runway 建议 ≤ 120 词，Kling ≤ 250 字，Sora ≤ 500 词

## 输出规范

每次返回给用户的内容结构：

```
## 🎬 [作品名或主题]

**核心概念**：一句话描述

**6 要素**
- 主体: ...
- 动作: ...
- 场景: ...
- 镜头: ...
- 光照: ...
- 风格: ...

**分镜**（如果超过 10 秒）
[0-2s] ...
[2-5s] ...
...

**Prompt（按目标模型）**

— Higgsfield Seedance 2.0 —
<prompt 英文>

— Runway Gen-3 —
<prompt 英文>

— Kling —
<prompt 英文>

**架构说明**（为什么这样设计）
一小段中文解释核心决策点
```

## 参考文件

- [`references/narrative-frameworks.md`](references/narrative-frameworks.md) — 5 段式 / 三幕式 / 2 秒钩子
- [`references/camera-moves.md`](references/camera-moves.md) — 20+ 运镜词典（中英 + 适用场景）
- [`references/lighting.md`](references/lighting.md) — 光照方案库
- [`references/composition.md`](references/composition.md) — 构图法则
- [`references/model-adapters.md`](references/model-adapters.md) — 5 个模型的 prompt 格式

## 质量自检

输出前确认：
- [ ] 6 要素全部明确（缺的已问用户或从上下文补全）
- [ ] 运镜 ≤ 2 个
- [ ] 时间锚点具体到秒
- [ ] 色彩有具体参考（胶片型号 / 导演风格 / 色卡）
- [ ] prompt 长度符合目标模型上限
- [ ] 附了架构说明
