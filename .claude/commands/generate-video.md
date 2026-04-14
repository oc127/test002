---
description: 引导式生成视频 prompt（会问风格/时长/主题/目标模型，然后调用对应 skill）
argument-hint: [可选：一句话描述你的视频创意]
---

# 生成视频 Prompt：$ARGUMENTS

你要做一个**引导式问答**，帮用户把一个模糊的创意变成可执行的视频 prompt。

## 工作流

### Step 1: 理解初始创意

- 如果 `$ARGUMENTS` 非空，这是用户的初始创意，基于它展开
- 如果为空，问用户"想做一个什么样的视频？"

### Step 2: 用 AskUserQuestion 问清 4 个关键维度

必问（如果用户创意里没说）：

1. **风格方向**（决定调用哪个 skill）
   - 电影感 / 剧情向 / 史诗感 → 调 `cinematic-video`
   - 电商带货 / 产品广告 → 调 `ecommerce-video`
   - 其他风格 → 检查有没有对应 skill，没有就提示用 `/new-skill` 建

2. **时长 + 平台**
   - 抖音/TikTok 15s 竖屏
   - YouTube 30s 横屏
   - 电商信息流 6s
   - 电影级短片 10-15s
   - MV 30-60s

3. **目标视频模型**（决定 adapter 格式）
   - Higgsfield Seedance 2.0
   - Runway Gen-3 / Gen-4
   - Kling AI
   - Luma Dream Machine / Ray 2
   - Sora
   - 全部（生成多种格式，用户挑）

4. **情绪基调**（决定运镜和光照）
   - 紧张 / 浪漫 / 史诗 / 日常 / 悬疑 / 冰冷 / 赛博 / 末日
   - 或"我希望观众看完感觉是 ___"

### Step 3: 调用对应 Skill

根据风格方向自动调用：
- `cinematic-video` → 查 references 下全部 5 个文件
- `ecommerce-video` → 查 references 下 3 个文件
- 其他 skill → 按 skill 内部逻辑

### Step 4: 按 Skill 定义的输出格式返回

遵循对应 skill 的"输出规范"章节。关键是：
- 6 要素清单
- 分镜（如果超过 10 秒）
- Prompt（按目标模型分开）
- 架构说明

### Step 5: 提供下一步选项

输出 prompt 后，询问用户：
1. 要不要 A/B 版本？（换钩子、换运镜、换风格）
2. 要不要保存到 `prompts/` 目录做版本管理？
3. 如果有账号 + Playwright MCP 可用，要不要自动去渲染？

## 示例对话流

```
用户: /generate-video 赛博朋克雨夜追车

你: 好，赛博朋克雨夜追车——这是很经典的场景。在开始之前我确认 4 件事：

[AskUserQuestion]
1. 风格方向？[电影感 | 带货 | 抽象艺术]
2. 时长 + 平台？[抖音 15s | YouTube 30s | 短片 10s]
3. 目标模型？[Higgsfield | Runway | Kling | Sora | 全部都要]
4. 情绪基调？[紧张刺激 | 史诗壮阔 | 酷炫性冷淡]

用户: 电影感 | 短片 10s | Runway + Kling | 紧张刺激

你: [调用 cinematic-video skill，填充 6 要素]

## 🎬 赛博朋克雨夜追车

**核心概念**：一辆改装摩托在霓虹雨夜巷道追击执法飞船

**6 要素**
- 主体: 头戴机械义眼头盔的女骑手，穿反光战术服
- 动作: 高速漂移过弯，火花从车身飞溅
- 场景: 狭窄霓虹招牌挂满的巷道，地面积水反光
- 镜头: 低角度跟拍 + 短暂 dolly zoom，35mm
- 光照: 青色主光 + 品红点缀 + 雨水反光
- 风格: Blade Runner 2049 + Cinestill 800T 胶片感

**分镜**
[0-2s] Hook: 头盔面罩特写，霓虹在面罩上流动
[2-5s] Setup: 拉远，骑手启动引擎，摩托喷火
[5-8s] Rising: 低角度跟拍漂移过弯，火花飞
[8-10s] Climax: 执法飞船的追光打来，骑手加速消失在巷口

**Prompt**

— Runway Gen-3 —
<...>

— Kling —
<...>

**架构说明**
[...]

---

接下来：
1. 想要备选版（换个钩子/运镜/光照）？
2. 保存到 prompts/cyberpunk-chase.md？
3. （如果配置了 Playwright）自动打开 Runway 去跑渲染？
```

## 注意事项

- **别问太多问题**：4 个关键维度已经够了，别变成 20 个问题的烦人表单
- **能推断就推断**：用户说"赛博朋克"，情绪基调就默认"紧张+酷"，不用每次问
- **给用户跳过权**：用户说"你全部替我决定"时，就用最常见组合快速出
