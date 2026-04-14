---
id: ecommerce-coffee-maker-batch
skill: ecommerce-video
model: multiple
duration: 15
aspect_ratio: 9:16
created: 2026-04-14
tags: [ecommerce, product-ad, coffee, batch, tiktok]
status: draft
---

# 智能咖啡机 - 5 条 A/B 测试 prompt 批次

**产品**: 一键出品智能家用咖啡机
**目标用户**: 都市职场人，追求效率
**核心卖点**: 15 秒出一杯精品咖啡
**平台**: TikTok / 抖音（9:16 竖屏）
**策略**: 5 种不同钩子投放 A/B，找转化最高的

---

## 变体 1: 痛点钩子

**钩子类型**: Pain Point

```markdown
[0-2s]   钩子    办公室凌乱桌面，疲惫脸色的年轻人揉眼睛
[2-5s]   痛点    打开咖啡店 app，显示"排队 20 人"，叹气
[5-9s]   方案    咖啡机登场：按一下按钮
[9-13s]  证据    15 秒倒计时，浓缩咖啡流出
[13-15s] CTA     "点击购买链接"
```

**Runway Gen-3 Prompt (for [5-9s] 方案段)**:
```
Vertical 9:16 format. Close-up of a smart coffee machine on a
modern kitchen counter. A hand reaches out and presses the single
button on top. The machine begins to brew immediately, steam rising.
Clean minimalist kitchen lighting, morning natural light.
```

---

## 变体 2: ASMR 钩子

**钩子类型**: ASMR / Sensory

```markdown
[0-2s]   钩子    超微距慢动作：咖啡油脂层浮现在白瓷杯中
[2-5s]   细节    深棕色咖啡液缓慢滴落，拉丝效果
[5-9s]   产品    咖啡机在画面中心，纯白背景
[9-13s]  场景    女生在办公室喝一口，满足表情
[13-15s] CTA     品牌 + 字幕
```

**Kling Prompt (for [0-2s])**:
```
竖屏 9:16。超微距慢动作镜头。深棕色浓缩咖啡从咖啡机口缓慢滴落
入白色瓷杯，金黄色油脂层（crema）逐渐形成并旋转。纯白背景，
顶部柔光，极致质感，ASMR 视觉。
```

---

## 变体 3: UGC 钩子

**钩子类型**: UGC / Real Person

```markdown
[0-2s]   钩子    女生手持手机对镜头：姐妹！救了我的早晨！
[2-5s]   痛点    回放她之前早上排咖啡店 30 分钟的画面
[5-9s]   方案    现在的早晨：按一下咖啡机，15 秒搞定
[9-13s]  证据    端着咖啡出门，早到 20 分钟
[13-15s] CTA     评论区链接
```

**Kling Prompt (for [0-2s])**:
```
竖屏手持自拍视频。一位年轻女生坐在床上，头发略乱，手持手机对着
镜头说话，表情兴奋。自然晨光从窗户照入，卧室背景略虚化，
手机自拍视频质感，真实 vlog 风格。
```

---

## 变体 4: 前后对比

**钩子类型**: Before/After

```markdown
[0-2s]   钩子    分屏：左边手冲咖啡复杂步骤，右边按一下按钮
[2-5s]   痛点    左边持续进行，右边已经在喝了
[5-9s]   方案    镜头切到咖啡机完整展示
[9-13s]  证据    同一个人早晨时间对比：节省 10 分钟
[13-15s] CTA     Logo + 链接
```

**Runway Gen-3 Prompt**:
```
Vertical 9:16 split screen. Left side: a person making pour-over
coffee, complex steps, multiple tools, minutes passing. Right side:
same person presses one button on a smart coffee machine, coffee
ready in 15 seconds. Identical lighting on both sides, direct visual
comparison. Clean minimalist kitchen.
```

---

## 变体 5: Hero 产品镜头

**钩子类型**: Hero Product (电影感)

```markdown
[0-2s]   钩子    CGI：咖啡机从黑暗中浮现，聚光灯打下
[2-5s]   细节    360° 环绕，展示产品每个角度
[5-9s]   材质    特写按钮质感、金属拉丝、玻璃容器
[9-13s]  场景    产品在现代厨房，金属光泽
[13-15s] CTA     品牌标志淡入
```

**Higgsfield Seedance 2.0 Prompt**:
```
Cinematic hero product shot. A premium smart coffee machine slowly
emerges from darkness into a single overhead spotlight. Brushed
metal body with polished chrome accents catch the light. Camera
orbits 360 degrees around the product against a pure black
background. Luxury appliance aesthetic, Apple keynote style.
Vertical 9:16 format.
```

---

## 批量渲染策略

如果要一次性跑这 5 条：
1. 所有 prompt 存为单独文件在 `prompts/ecommerce-coffee-batch/`
2. 用同一个 seed 确保主播形象一致（变体 1、3、4）
3. 按 `workflows/batch-render.md` 流程批量提交
4. 上线后 A/B 测试 3-7 天，看哪个 CTR 最高

## 测试指标

- **CTR**（点击率）：哪个钩子让人点进详情页
- **CVR**（转化率）：哪个视频让人下单
- **完播率**：哪个视频没被滑走
- **ROI**：单次投放的 ROAS

## Render History

- _待用户有账号后回填_
