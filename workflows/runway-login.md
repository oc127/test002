# 工作流：Runway 登录 + 渲染

Runway 是海外 AI 视频代表之一，工具链完整（生成/延长/编辑/导出一条龙）。电商类商业使用最成熟。

> **⚠️ 状态**：Phase 1 流程模板。真实选择器待 Phase 2 首次登录后填入。

---

## A. 优势

| 优势 | 说明 |
|------|------|
| **工具链最完整** | 生成 + 延长 + 蒙版 + 绿幕 + 运动控制 |
| **Camera Control** | UI 可视化运镜控制，不全靠 prompt |
| **电商质感好** | 默认就是商业感 |
| **图生视频稳** | 角色一致性可控 |
| **有 API** | 批量生产可编程调用 |

缺点：
- 中文支持一般，英文为主
- 海外服务，国内需科学上网
- 价格相对较高

## B. 前置条件

1. Runway 账号（需邮箱注册，推荐用 Gmail）
2. **信用卡**（Runway 只支持国际信用卡订阅）
3. 科学上网环境（国内访问）
4. `.env` 里填 `RUNWAY_EMAIL` / `RUNWAY_PASSWORD` 或 `RUNWAY_API_KEY`

## C. 登录流程（Web）

### Step 1: 打开 Runway

```
mcp__playwright__browser_navigate(url="https://runwayml.com")
mcp__playwright__browser_snapshot()
```

### Step 2: 点击登录

```
mcp__playwright__browser_click(
  element="Log in / Sign in button",
  ref="<ref>"
)
```

### Step 3: 选择方式

**推荐 Google SSO**（避免密码泄露）：

```
mcp__playwright__browser_click(
  element="Continue with Google",
  ref="<ref>"
)
# 等待 Google 登录页
# 用户手动完成（或自动填邮箱密码）
mcp__playwright__browser_wait_for(text="Dashboard")
```

**或邮箱密码**：

```
mcp__playwright__browser_fill_form(fields=[
  { element="Email", ref="<ref>", value="${RUNWAY_EMAIL}" },
  { element="Password", ref="<ref>", value="${RUNWAY_PASSWORD}" }
])
mcp__playwright__browser_click(element="Log in submit", ref="<ref>")
```

### Step 4: 保存 storage state

Runway cookies 有效期长，保存后可复用数天：

```
mcp__playwright__browser_run_code(code=`
  const state = await context.storageState();
  require('fs').writeFileSync('.playwright-state/runway.json', JSON.stringify(state));
`)
```

## D. 渲染流程

### Step 1: 进入创作页

```
mcp__playwright__browser_click(element="Generate / Create", ref="<ref>")
```

### Step 2: 选择模型

- **Gen-3 Alpha**：基础，成本低
- **Gen-3 Alpha Turbo**：更快，略弱
- **Gen-4**：最新，最好，成本高

```
mcp__playwright__browser_click(element="Gen-3 Alpha", ref="<ref>")
```

### Step 3: 选模式

- **Text to Video**
- **Image to Video**（推荐：更可控）
- **Video to Video**（改编现有视频）

### Step 4: 输入 Prompt

```
mcp__playwright__browser_type(
  element="Prompt textarea",
  ref="<ref>",
  text="${PROMPT}"
)
```

### Step 5: Camera Control（Runway 独家）

Runway 有**可视化运镜面板**，不需要在 prompt 里写运镜：

```
# 打开 Camera Control
mcp__playwright__browser_click(element="Camera Control icon", ref="<ref>")

# 选运镜类型
mcp__playwright__browser_click(element="Dolly Zoom option", ref="<ref>")

# 调强度（slider 0-10）
mcp__playwright__browser_click(
  element="Intensity slider",
  ref="<ref>"
)
# 或 type 数值
```

支持的运镜：
- Horizontal（左右）
- Vertical（上下）
- Pan（摇）
- Tilt（摇）
- Roll（翻滚）
- Zoom（变焦）

### Step 6: 设置参数

- **Duration**：5s / 10s
- **Aspect Ratio**：16:9 / 9:16 / 1:1 / 4:3
- **Seed**：随机或固定（保持系列一致性用）

```
mcp__playwright__browser_click(element="Duration 10s", ref="<ref>")
```

### Step 7: Generate（扣积分）

```
# 确认积分消耗
if not user_approved:
    ask_user("Runway Gen-3 10s 消耗约 100 credits，是否继续？")

mcp__playwright__browser_click(element="Generate", ref="<ref>")
```

### Step 8: 等待完成

Runway 一般 1-3 分钟：

```
mcp__playwright__browser_wait_for(text="Complete", time=300)
```

### Step 9: 下载

```
mcp__playwright__browser_click(element="Download MP4", ref="<ref>")
```

## E. API 调用（批量生产推荐）

Runway 提供官方 API：
- 文档：https://docs.dev.runwayml.com
- 需 Enterprise / Pro 订阅

示例代码（`scripts/runway-api.js`）：

```javascript
// 注意：请以官方最新文档为准
async function textToVideo(prompt, options = {}) {
  const response = await fetch('https://api.dev.runwayml.com/v1/image_to_video', {
    method: 'POST',
    headers: {
      'Authorization': `Bearer ${process.env.RUNWAY_API_KEY}`,
      'Content-Type': 'application/json',
      'X-Runway-Version': '2024-11-06'
    },
    body: JSON.stringify({
      model: 'gen3a_turbo',
      promptText: prompt,
      promptImage: options.image,  // 图生视频
      duration: options.duration || 10,
      seed: options.seed,
      ratio: options.aspectRatio || '16:9'
    })
  });
  const { id } = await response.json();
  
  // 轮询状态
  while (true) {
    const status = await fetch(`https://api.dev.runwayml.com/v1/tasks/${id}`, {
      headers: { 'Authorization': `Bearer ${process.env.RUNWAY_API_KEY}` }
    }).then(r => r.json());
    
    if (status.status === 'SUCCEEDED') {
      return status.output[0];  // 视频 URL
    }
    if (status.status === 'FAILED') {
      throw new Error('Generation failed');
    }
    await new Promise(r => setTimeout(r, 10000));  // 10s 轮询
  }
}
```

## F. Runway 独家功能

### 1. Keyframes（多关键帧）
Gen-3 支持：起始帧 + 结束帧 → AI 补中间。

**流程**：
1. 上传起始图（Image 1）
2. 上传结束图（Image 2）
3. Prompt 描述转场过程

### 2. Video to Video（风格迁移）
上传一段视频 → 改风格（赛博朋克、油画、动漫）。

**流程**：
1. 上传原视频
2. 选目标风格 prompt
3. 指定保留程度（0-100%）

### 3. Motion Brush（运动笔刷）
图生视频时，**画笔圈定"哪里动，哪里静"**。

### 4. Green Screen（绿幕扣像）
自动抠主体，便于合成。

### 5. Lip Sync
上传音频 + 人物视频，对口型。

## G. 最佳实践

### 获得好结果的 10 个原则

1. **简洁 prompt**：Runway 偏好 ≤ 120 词
2. **用 Camera Control 代替 prompt 里的运镜**：UI 可控 > 文字描述
3. **具体动作**：`slowly turns head` > `moves`
4. **避免多主体**：一次最多 1-2 人
5. **先图生再文生**：用 Midjourney 先出关键帧
6. **用 seed**：需要同主体多镜头时
7. **先用 Turbo 试**：便宜快，定稿再用 Alpha
8. **分句用句号**：Runway 对句号敏感
9. **避免否定词**：不说 "no X"，说 "empty X"
10. **保留风格词**：`cinematic`、`35mm film`、`bokeh` 很有效

## H. 成本参考（2025）

| 订阅 | 月费 | 月 credits | 适用 |
|------|------|-----------|------|
| Free | $0 | 125 | 试用 |
| Standard | $15 | 625 | 个人 |
| Pro | $35 | 2250 | 小团队 |
| Unlimited | $95 | 无限 | 高频生产 |
| Enterprise | 联系 | 定制 | 企业 |

**Gen-3 Alpha 10 秒 ≈ 100 credits**。
Standard 订阅 625 credits = 约 60 条 10 秒视频。

## I. 常见问题

| 问题 | 原因 | 解决 |
|------|------|------|
| 人脸崩坏 | Gen-3 弱项 | 用 Gen-4 + 图生视频 |
| 动作不连贯 | 复杂动作 | 拆分成多个 5s 生成再拼接 |
| 颜色跳变 | Prompt 含多颜色描述 | 明确主色调 |
| 积分耗尽 | 订阅不够 | 升级或攒着用 |
| 下载失败 | 网络问题 | 右键视频手动下载 |

## J. 和其他模型协作

推荐流程：
1. **Midjourney** → 出关键帧
2. **Runway Gen-3** → 图生视频（角色一致）
3. **Kling Motion Brush** → 精修局部动作
4. **DaVinci Resolve** → 后期剪辑 + 调色

---

## 🇺🇸 推荐使用场景

**国内用户**：优先跑 Kling（workflows/kling-login.md），Runway 作为质量进阶。

**海外业务 / 需要电影质感**：从 Runway 起步，工具链最省心。

**超高频生产 / 自动化**：Runway API + 自建批量脚本。
