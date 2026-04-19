---
name: social-hook
description: 生成社交媒体爆款短视频 prompt。当用户需要"TikTok/抖音/Reels/Shorts/爆款/scroll-stopper/病毒式传播/涨粉/社媒内容/刷屏/hook/viral/scroll-stop/社交媒体/短视频运营"时自动调用。专注 0.5 秒极速钩子设计、竖屏 9:16 构图、平台算法差异化。区别于 ecommerce-video（卖货导向）：social-hook 服务于"涨粉/娱乐/品牌曝光"。
---

# 社媒爆款钩子 (Social Hook / Scroll-Stopper)

社交媒体视频的生死在 **0.5 秒**。用户的拇指划过你的视频只需 0.3 秒——你必须在这 0.3 秒内让拇指停下来。

## 调用时机

**强触发词**：
- TikTok / 抖音 / Reels / Shorts / 小红书视频
- 爆款 / 刷屏 / 病毒式 / 涨粉 / 热门
- scroll-stopper / viral / hook
- 社媒内容 / 短视频运营

**典型请求**：
- "帮我做一个 TikTok 爆款开头"
- "这个产品怎么做成 Reels scroll-stopper"
- "设计一个 3 秒内让人停下来的视频"

**与 ecommerce-video 的边界**：
| | social-hook | ecommerce-video |
|---|---|---|
| **目标** | 涨粉 / 娱乐 / 品牌曝光 | 卖货转化 |
| **CTA** | 关注 / 转发 / 评论 | 购买 / 点链接 |
| **钩子时间** | 0.5 秒 | 2 秒 |
| **内容调性** | 有趣 / 震撼 / 共鸣 | 痛点 / 方案 / 证据 |

---

## 0.5 秒钩子 8 公式

### 1. Motion-First（运动优先）
画面第一帧就有**剧烈运动**，不是静态起手。
- **Prompt**: `The very first frame shows rapid dynamic motion — [具体动作]`
- **例**: 人物跳入画面 / 物体飞向镜头 / 快速 zoom-in

### 2. Color Flash（色彩闪烁）
画面在 0.3 秒内发生一次**颜色剧变**。
- **Prompt**: `Abrupt color temperature shift in the first half-second — from [A色] to [B色]`
- **例**: 全黑→突然亮橙 / 冷蓝→暖金

### 3. Direct Eye Contact（直视镜头）
主体在第一帧**直视镜头**，建立即时连接。
- **Prompt**: `Subject stares directly into camera lens from the very first frame, intense eye contact`
- **例**: 人物从暗处走向镜头并凝视

### 4. Sound-Visual Sync（音画同步）
视觉动作精确配合一个**突然的声效**。
- **Prompt**: `Visual action perfectly synchronized with an abrupt audio cue at frame one`
- **例**: 拍手的瞬间 / 关门声 / bass drop

### 5. Text Overlay Hook（大字弹出）
画面第一帧弹出**一行大字**吸引注意。
- **Prompt**: `Bold text overlay appearing immediately: "[文案]", large sans-serif, centered`
- **例**: "你绝对没见过这个" / "等等，什么？！"

### 6. Curiosity Gap（好奇留白）
只展示事件的**一半**，让人想看完。
- **Prompt**: `Partial reveal — showing the setup but not the result, creating visual curiosity`
- **例**: 手即将按按钮 / 门即将打开 / 正在倒计时

### 7. Pattern Interrupt（打破预期）
用一个**反常规画面**打断用户的滑动惯性。
- **Prompt**: `Unexpected visual that breaks scrolling pattern — [反常内容]`
- **例**: 正常街景中一个人倒着走 / 静态画面中一个元素突然动了

### 8. Scale Shock（尺寸反差）
画面中两个物体的**尺寸差异极端**。
- **Prompt**: `Extreme scale contrast between [小物体] and [大物体] in same frame`
- **例**: 手掌上站着的微型人 / 巨物在城市中穿行

---

## 竖屏 9:16 构图法则

### 视觉重心
- 主体放在画面**上 1/3**（人的眼睛在划手机时先看上半部分）
- **下 1/4 留空**给字幕 / 互动按钮 / 评论区

### 文字安全区
```
┌──────────────┐
│  ← 标题区 →  │  上 15%：标题/钩子文案
│              │
│   主体内容    │  中 60%：核心画面
│              │
│              │
│  ← 字幕区 →  │  下 15%：CTA / 字幕
│  [互动按钮]  │  最下 10%：平台 UI 遮挡区（不放重要内容）
└──────────────┘
```

### Thumb Zone（拇指热区）
用户右手持手机时，拇指自然停留在画面**右下 1/4**。把最吸引人的视觉元素或动作放在这里。

---

## 结尾 CTA 类型映射

| 目标 | CTA 类型 | 视觉设计 |
|------|---------|---------|
| **涨粉** | "关注我看更多" | 手指指向关注按钮方向 |
| **互动** | "评论区告诉我" | 文字弹出 + 箭头指向评论区 |
| **引流** | "点击链接" | 手指向下滑动暗示 |
| **转发** | "转给你的朋友" | 分享图标动画 |
| **收藏** | "先收藏" | 收藏图标高亮 |

---

## 平台差异速查表

| 维度 | TikTok | Instagram Reels | YouTube Shorts |
|------|--------|----------------|----------------|
| **黄金时长** | 15-30s | 7-15s | 30-60s |
| **算法偏好** | 完播率 > 一切 | 互动率（赞/评/转） | 点击率 + 观看时长 |
| **内容偏好** | 趋势/挑战/音乐 | 美学/生活方式 | 教程/知识 |
| **钩子要求** | 0.3s（最严格） | 0.5s | 1s（最宽松） |
| **文字** | 必须大字幕 | 可选 | 推荐 |
| **音乐** | 极重要（用热歌） | 重要 | 不太重要 |
| **Ratio** | 9:16 | 9:16 | 9:16 |

---

## 模型适配

### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

```
Vertical 9:16 social media scroll-stopper. The very first frame
shows a sudden dynamic motion — a hand reaches toward the camera
revealing a glowing product. Abrupt warm-to-cool color shift in
the first half-second. Subject makes direct eye contact with the
camera. Bold text overlay: "Wait for it..." centered in upper
third. Quick cuts every 0.5 seconds. Final frame: product hero
shot with subtle ambient luminance. Energetic, bold pacing
optimized for TikTok scroll behavior.
```

### Kling（中文）
```
竖屏 9:16 社交媒体爆款视频。第一帧就有快速运动——一只手伸向
镜头展示发光的产品。0.5 秒内色温从暖色突变到冷色。主体直视
镜头。画面上方 1/3 弹出大字："等一下..."。每 0.5 秒快切一次。
最后一帧：产品英雄镜头 + 柔和环境光。节奏感强，TikTok 风格。
```

### Runway Gen-3
```
Vertical 9:16 viral social media hook. Opening frame: immediate
kinetic motion, hand swiping toward camera with a glowing object.
Color temperature shifts abruptly from cool blue to warm amber.
Direct eye contact established. Text overlay "Wait for it..."
in bold sans-serif, upper third. Rapid 0.5s cuts. Final hero
shot with soft rim light. Optimized for Reels engagement.
```

---

## 避坑

1. ❌ **前 0.5 秒是静态画面** → 直接被划走，第一帧必须有运动或冲击
2. ❌ **横屏 16:9 用在社媒** → 所有平台都是 9:16，横屏 = 上下大黑边 = 死
3. ❌ **堆太多信息** → 社媒视频一个核心信息就够，多了记不住
4. ❌ **忽略平台差异** → TikTok 要音乐/趋势，Reels 要美学，Shorts 要知识
5. ❌ **没有 CTA** → 不告诉观众"接下来做什么"等于浪费流量

## 输出规范

```
## 🔥 [标题]（[平台] Scroll-Stopper）

**目标平台**: [TikTok / Reels / Shorts]
**目标**: [涨粉 / 互动 / 引流]
**钩子公式**: [8 公式中选 1-2 个]
**时长**: [Xs]

**分镜**
[0-0.5s] HOOK: ...
[0.5-Xs] BODY: ...
[最后 1s] CTA: ...

**Prompt**（按模型）

— Higgsfield（⚠️ 已过 content-filter）—
<prompt>

— Kling —
<中文 prompt>
```

## 质量自检

- [ ] 0.5 秒内有运动/冲击/色变/文字（至少一个钩子公式）
- [ ] 9:16 竖屏
- [ ] 主体在上 1/3
- [ ] 下 10% 没有重要内容（平台 UI 遮挡区）
- [ ] 有明确 CTA
- [ ] 时长适配目标平台
- [ ] Higgsfield prompt 不含 banned words
