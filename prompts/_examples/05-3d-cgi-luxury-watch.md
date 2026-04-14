---
id: 3d-cgi-luxury-watch-001
skill: 3d-cgi
model: runway-gen3
duration: 8
aspect_ratio: 16:9
created: 2026-04-14
tags: [3d-cgi, luxury, watch, product, hero]
status: draft
---

# 奢侈腕表 CGI - Hero Product Showcase

**类型**: Product Showcase + Reveal

## 产品设计

- **案例**: 一款虚构的瑞士机械腕表 "Chronos Aether"
- **材质构成**:
  - 表壳：拉丝钛合金 (brushed titanium)
  - 表圈：抛光玫瑰金 (polished rose gold)
  - 表盘：哑光深蓝琺琅 (matte navy enamel)
  - 蓝宝石水晶磨砂 (frosted sapphire crystal)
  - 表带：棕色短吻鳄皮 (brown alligator leather)

## 环境与光照

- **HDRI**: Dark Showroom（暗色展厅）
- **主光**: 顶部柔光箱（softbox），45° 下打
- **轮廓光**: 从后方冷白色 LED 条勾边
- **补光**: 前方极低强度环境光，保留阴影

## 运动

- 相机慢速 **Slow Orbit** 45° 环绕 + 末尾 **Push-In** 到表盘特写

## 特效

- 轻微浮动尘埃粒子（catching the rim light）
- 镜面地板完美反射

## 分镜

```
[0-3s]   Reveal    腕表从黑暗中缓慢转动露出（表冠朝观众）
[3-6s]   Showcase  相机 45° 环绕，展示表壳侧面工艺
[6-8s]   Push-In   快速推进到表盘特写，展示机芯细节
```

## Prompts

### Runway Gen-3（首选）

```
Hero product showcase shot of a luxury mechanical watch. The watch
features a brushed titanium case with polished rose gold bezel,
a matte navy blue enamel dial, frosted sapphire crystal, and
dark brown alligator leather strap. Dark showroom HDRI environment,
pure black background. Key light: overhead softbox at 45 degrees.
Cool white LED rim light from behind. Camera performs a slow 45
degree orbit around the watch, then pushes in to extreme macro of
the dial. The watch rests on a polished black mirrored floor creating
a perfect reflection. Dust motes floating in the air catch the rim
light. Hyper-realistic CGI, Octane render quality, luxury campaign
aesthetic reminiscent of Patek Philippe advertising.
```

### Luma Ray 2（图生视频模式）

**前置**：先用 Midjourney / Ideogram 生成腕表静态图作为起始帧。

```
Starting frame: [uploaded watch still image on mirrored black surface]

Motion: The watch slowly rotates 45 degrees clockwise as the camera
orbits in sync. In the final 2 seconds, camera pushes in rapidly
to an extreme macro close-up of the dial, revealing subtle texture
of the enamel surface.

Physics: Subtle reflections updating on the titanium case and chrome
bezel as angles change. Dust particles drift lazily through rim
light.

Style: Octane render quality, photoreal CGI, luxury watch commercial.
```

### Higgsfield Seedance 2.0

```
Cinematic 3D CGI product shot. A luxury mechanical watch with
brushed titanium case, polished rose gold bezel, matte navy dial.
Camera performs a smooth 45-degree arc around the watch. Dark
showroom HDRI, strong rim light from behind, softbox key from above.
Mirrored black floor reflecting the watch. Slow dolly push-in to
dial close-up at the end. Ultra-realistic CGI, Rolex-campaign
aesthetic.
```

## 后期建议

- **调色**：阴影稍微加蓝（高冷感）
- **加 logo**：最后 1 秒品牌 logo 淡入
- **音效**：机械齿轮声、金属撞击声
- **字幕**：产品型号 + 品牌名

## 变体

### v2 白色场景版
```
改成 Pure white infinite cyclorama, 柔和均匀光, 适合电商详情页。
```

### v3 自然光版
```
改成 Window light with warm golden glow, 桌面场景, 更生活化, 
适合社媒。
```

### v4 爆炸图版
```
The watch slowly separates into its component parts—case, movement,
dial, hands, crown, strap—all floating in space, revealing the
internal mechanism. Exploded view aesthetic.
```

### v5 液态金属形成版
```
Liquid titanium droplets flow and merge mid-air, solidifying into
the final watch form. Dramatic reveal from pure chaos to precision.
```

## 后期工作流程

1. Runway 生成 4 个候选
2. 选最好的 1 个在 Luma 做高清化
3. 导入 After Effects 加 Logo 和字幕
4. DaVinci Resolve 调色
5. 导出 1080p (Instagram) + 4K (YouTube)

## Render History

- _待用户有账号后回填_
