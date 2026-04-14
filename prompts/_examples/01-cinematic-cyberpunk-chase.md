---
id: cinematic-cyberpunk-chase-001
skill: cinematic-video
model: runway-gen3
duration: 10
aspect_ratio: 16:9
seed: 12345
created: 2026-04-14
tags: [cinematic, cyberpunk, action, night, rain]
status: draft
---

# 赛博朋克雨夜追车 (Cyberpunk Rain Alley Chase)

**核心概念**: 一位女骑手驾驶改装摩托穿越霓虹雨夜的狭窄巷道，漂移瞬间火花飞溅

## 6 要素

- **主体**: 戴机械义眼头盔的女骑手，身穿黑色反光战术服
- **动作**: 高速漂移过弯，车身倾斜 45°，火花从后轮飞溅
- **场景**: 狭窄的巷道两侧挂满霓虹招牌，地面湿漉漉积水
- **镜头**: 低角度跟拍 + 短暂 dolly zoom，35mm 焦段，浅景深
- **光照**: 青色主光源（左侧霓虹） + 品红补光（右侧招牌） + 雨水反光勾边
- **风格**: Blade Runner 2049 美学，Cinestill 800T 胶片感，2.35:1 宽银幕

## 分镜

```
[0-2s]   Hook     头盔面罩特写，霓虹在面罩反光条上流动，呼吸声
[2-5s]   Setup    拉远到全景，骑手启动摩托，排气管喷火，巷道景深展开
[5-8s]   Rising   低角度跟拍 + 轻微 dolly zoom，漂移过弯瞬间
[8-10s]  Climax   慢动作火花飞溅特写 + 执法飞船追光从后方打来
```

## Prompts

### Runway Gen-3（推荐）

```
Slow tracking shot at low angle following a female motorcycle rider
wearing a black reflective tactical suit and a helmet with mechanical
visor glowing cyan. She drifts a modified bike through a narrow
neon-lit alley, rear tire sparks flying as the bike leans 45 degrees.
Wet pavement reflects cyan and magenta neon signs. Rain falls.
Shallow depth of field. Shot on Cinestill 800T film, 2.35:1
anamorphic widescreen, Blade Runner 2049 cinematography.
```

### Kling（中文）

```
低角度跟拍。一位戴着机械面罩头盔的女骑手，穿黑色反光战术服，
骑着改装摩托车在狭窄的霓虹招牌巷道中高速漂移。摩托倾斜 45 度，
后轮激起火花，溅起路面积水。青色与品红色霓虹光反射在湿漉漉的
地面上。相机跟随漂移轨迹，短暂变焦推拉产生眩晕感。浅景深，
电影胶片质感，《银翼杀手 2049》风格。
```

### Higgsfield Seedance 2.0

```
Cinematic low-angle tracking shot. Female rider in reflective tactical
suit and cyber visor helmet drifts a motorcycle through a neon-lit
rain-soaked alley. Sparks fly from rear tire. Cyan and magenta neon
reflections on wet pavement. Brief dolly zoom effect. Shot on
anamorphic lens, shallow depth of field. Blade Runner aesthetic,
Cinestill 800T film grain.
```

## Notes

- 第一版重点在"漂移瞬间"。如果模型动作生成不稳，改成"直线冲刺"更容易。
- Seed 12345 是随机起点，如果要做批次统一风格，保持同 seed。
- 可尝试的变体：
  - **v2**: 换成午夜地下停车场（减少霓虹）
  - **v3**: POV 视角（从骑手头盔视角看）
  - **v4**: 加伙伴（另一辆摩托在前方）

## Render History

- _待用户有 Runway 账号后回填_
