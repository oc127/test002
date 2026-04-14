# 工作流：Kling AI（可灵）登录 + 渲染

可灵是快手出品的视频生成平台（国内），对中文 prompt 支持最好，**国内用户推荐首选**。

> **⚠️ 状态**：Phase 1 流程模板。真实选择器待 Phase 2 首次登录后填入。

---

## A. 为什么推荐从 Kling 开始

| 优势 | 说明 |
|------|------|
| **国内注册无门槛** | 手机号即可，不需要科学上网 |
| **中文 prompt 最好** | 快手训练语料中文为主 |
| **真人动作自然** | 快手短视频数据优势 |
| **价格友好** | 试用积分多，对比海外平台便宜 |
| **商业用途清晰** | 中文 TOS，合规易懂 |

缺点：
- 对"电影感"拉胯（那个找 Higgsfield）
- 对极端运镜支持弱
- 水印需要付费会员去除

## B. 前置条件

1. 手机号（国内）
2. Playwright MCP 连接成功（`.mcp.json` 已配置）
3. `.env` 里填 `KLING_ACCESS_KEY` 和 `KLING_SECRET_KEY`（可选，若走 API）

## C. 登录流程

### 方式 1: Web 手动扫码（推荐首次用）

```
# Step 1: 打开 Kling
mcp__playwright__browser_navigate(url="https://klingai.com")

# Step 2: 看结构
mcp__playwright__browser_snapshot()
# 找到"登录"按钮的 ref

# Step 3: 点击登录
mcp__playwright__browser_click(
  element="右上角登录按钮",
  ref="<从 snapshot>"
)

# Step 4: 选微信扫码
mcp__playwright__browser_click(
  element="微信扫码选项",
  ref="<ref>"
)

# Step 5: 让用户扫码
# Claude 暂停等待用户
print("请用微信扫描浏览器里的二维码，完成后说'继续'")

# Step 6: 等待登录成功
mcp__playwright__browser_wait_for(text="AI 创作")
```

### 方式 2: API Token（批量生产推荐）

可灵有官方 API：
- 控制台：https://klingai.com/dev
- 获取 `access_key` + `secret_key`
- 写进 `.env`

API 调用示例（Node.js，放在 `scripts/kling-api.js`）：
```javascript
// 这只是示例代码，实际请参考官方文档
const crypto = require('crypto');
function generateSign(params, secretKey) {
  // Kling 的签名逻辑
  // ...
}

async function textToVideo(prompt) {
  const response = await fetch('https://api.klingai.com/v1/videos/text2video', {
    method: 'POST',
    headers: {
      'Content-Type': 'application/json',
      'Authorization': `Bearer ${process.env.KLING_ACCESS_KEY}`
    },
    body: JSON.stringify({
      prompt: prompt,
      duration: 5,
      aspect_ratio: '9:16'
    })
  });
  return response.json();
}
```

## D. 渲染流程（Web 版）

### Step 1: 进入创作页

```
mcp__playwright__browser_click(element="AI 视频生成", ref="<ref>")
```

### Step 2: 选模式

- 文生视频（Text-to-Video）
- 图生视频（Image-to-Video）—— 推荐用于电商/角色一致性

```
mcp__playwright__browser_click(element="文生视频 tab", ref="<ref>")
```

### Step 3: 填 Prompt（支持中文）

```
mcp__playwright__browser_type(
  element="Prompt 输入框",
  ref="<ref>",
  text="${PROMPT}"  # 直接中文
)
```

### Step 4: 设置参数

- **时长**：5s / 10s
- **模式**：标准 / 高质量（高质量耗 2x 积分）
- **宽高比**：9:16（竖屏）/ 16:9 / 1:1
- **模型版本**：Kling 1.6 Standard / Kling 2.0 Pro

```
mcp__playwright__browser_select_option(
  element="时长下拉",
  ref="<ref>",
  values=["5s"]
)
```

### Step 5: 提交（会扣积分）

**⚠️ CLAUDE.md 硬性要求：扣积分前必须用户明确授权**

```
# 先确认
if not user_approved:
    ask_user("将消耗 N 积分，是否继续？")

mcp__playwright__browser_click(element="生成按钮", ref="<ref>")
```

### Step 6: 轮询完成

Kling 一般 30s-2min：

```
mcp__playwright__browser_wait_for(text="生成完成", time=180)
```

### Step 7: 下载

```
mcp__playwright__browser_click(element="下载按钮", ref="<ref>")
```

## E. 图生视频（角色一致性神器）

做电商系列素材时，想要"同一个主播形象"的多条视频：

### Step 1: 准备参考图

- 用 Midjourney / Ideogram / 真人照片
- 一张清晰的正面照，展示主体外观

### Step 2: 上传

```
mcp__playwright__browser_file_upload(
  element="上传首帧图",
  ref="<ref>",
  paths=["./assets/references/主播形象.jpg"]
)
```

### Step 3: Prompt 描述动作

关键：**不要再描述外观**，只描述"怎么动"。

```
一位女生对着镜头微笑挥手，温暖日光，自然 vlog 风格。
```

### Step 4: 正常提交

## F. Kling 独特功能

### 1. Motion Brush（运动画笔）
在图生视频模式下，可以**手动划定"哪部分会动，哪部分静止"**：
- 圈出"头发" → AI 让头发飘动
- 圈出"手" → AI 让手挥动
- 其他部分保持静止

Playwright 操作复杂，建议人工先示范一次让 Claude 记录步骤。

### 2. Lip Sync（对口型）
上传音频 + 人物图 → 生成口型同步视频。
- 适用：AI 主播、虚拟人带货
- 位置：视频编辑页 → Lip Sync Tab

### 3. Extend（延长）
5 秒视频不够？可以"接力"生成下 5 秒：
```
mcp__playwright__browser_click(element="延长生成", ref="<ref>")
```

## G. 错误 / 常见问题

| 问题 | 原因 | 解决 |
|------|------|------|
| 内容审核不通过 | 涉及敏感词 | 改 prompt，避免敏感主题 |
| 生成结果与 prompt 不符 | Prompt 含义模糊 | 换更具体描述 |
| 人物面部崩坏 | 模型短板 | 用图生视频 + 高质量参考图 |
| 运镜不执行 | 复杂运镜超能力 | 拆成多段或简化运镜 |
| 积分不够 | 账号余额 | 充值 / 升级会员 |

## H. 成本参考（2025）

| 模式 | 积分 / 5秒 | 积分 / 10秒 |
|------|-----------|------------|
| Kling 1.6 Standard | 10 | 20 |
| Kling 1.6 Pro | 30 | 60 |
| Kling 2.0 Master | 50 | 100 |

**新用户送试用积分**，可以先免费跑几条熟悉流程。

## I. 首次填充真实选择器

用户首次跑时，让 Claude:

1. 打开 klingai.com
2. 跑 `browser_snapshot`
3. 识别关键元素的 ref：
   - 登录按钮
   - 微信扫码按钮
   - 创作入口
   - Prompt 输入框
   - 时长下拉
   - 生成按钮
   - 下载按钮
4. 更新本文件的"<ref>"占位

## J. 合规与伦理

- ❌ 不要用于生成含有版权 IP 的内容（迪士尼、漫威）
- ❌ 不要用真人脸做换脸
- ❌ 不要用于生成误导性新闻
- ✅ 自用创作、合规商用、学习研究都可以
- ✅ 商用视频建议购买 Pro 版去水印

## K. 和其他模型协作

Kling 可以和其他模型混搭：

1. **Midjourney 出关键帧 → Kling 图生视频**：最稳的商业流程
2. **Kling 出 5s 片段 → Runway 延长**：接力生成
3. **Kling 生成 Performance 镜头 → Runway 生成 Conceptual 镜头** → 后期剪辑

---

## 🇨🇳 为什么用户优先跑 Kling

Phase 1 你只有 Claude Code + Playwright MCP。 Phase 2 真要跑起来，**Kling 是门槛最低的**：
- 手机号注册，5 分钟搞定
- 新用户免费积分够跑 10 条
- 中文提示词直接用，不需要翻译

**推荐先注册 Kling，跑通一条短视频作为 MVP 验证，再考虑其他平台。**
