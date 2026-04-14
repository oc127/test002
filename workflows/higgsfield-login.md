# 工作流：Higgsfield 登录 + 状态保存

Playwright MCP 驱动的登录流程模板。**首次跑时需要用户人工扫码/输入**，之后 cookies 保存下来可以复用。

> **⚠️ 重要**：本文件中的选择器（`button[text()="Log in"]`、`input[name="email"]` 等）是**占位符**。真实选择器需要用户第一次用 Playwright 打开页面后通过 `browser_snapshot` 查看 DOM 结构后填入。Higgsfield 可能在 2025 年后改版过。
>
> **目前状态**：Phase 1 仅提供流程骨架；Phase 2 用户注册账号后再填真实选择器。

---

## A. 前置条件

1. Playwright MCP 已在 `.mcp.json` 配置（✅ 已做）
2. 在 Claude Code 里 `/doctor` 显示 `playwright` 已连接
3. Higgsfield 账号（邮箱密码 或 Google SSO）
4. `.env` 里填了 `HIGGSFIELD_EMAIL` / `HIGGSFIELD_PASSWORD`（可选，也可以人工登录）

## B. 登录流程（伪代码）

以下步骤由 Claude 调用 Playwright MCP 工具执行：

### Step 1: 启动浏览器（非 headless，方便扫码）

```
mcp__playwright__browser_navigate(url="https://higgsfield.ai")
mcp__playwright__browser_snapshot()   # 截取 DOM accessibility tree
```

### Step 2: 定位登录按钮

看 snapshot 返回的结构，找到"Log in"/"Sign in"按钮的 ref。

```
mcp__playwright__browser_click(
  element="Login button in top-right navigation",
  ref="<从 snapshot 里找>"
)
```

### Step 3: 选择登录方式

**方式 A：邮箱密码**
```
mcp__playwright__browser_fill_form(fields=[
  { element="Email input", ref="<ref>", value="${HIGGSFIELD_EMAIL}" },
  { element="Password input", ref="<ref>", value="${HIGGSFIELD_PASSWORD}" }
])
mcp__playwright__browser_click(element="Submit button", ref="<ref>")
```

**方式 B：Google SSO（推荐，避免密码泄露）**
```
mcp__playwright__browser_click(element="Continue with Google", ref="<ref>")
# 等待 Google 登录页，此时让用户人工完成
mcp__playwright__browser_wait_for(text="Welcome")
```

### Step 4: 等待登录成功

```
mcp__playwright__browser_wait_for(text="Dashboard")   # 或任何登录后的标志
```

### Step 5: 保存登录状态（重要）

让下次可以跳过登录：

```
# Playwright MCP 默认会保留 session
# 如需显式保存状态到文件：
mcp__playwright__browser_run_code(code=`
  const state = await context.storageState();
  require('fs').writeFileSync('.playwright-state/higgsfield.json', JSON.stringify(state));
`)
```

⚠️ `.playwright-state/` 已在 `.gitignore`，严禁 commit。

## C. 复用会话（第 2 次以后）

```
# 启动时加载已保存的 storage state
mcp__playwright__browser_navigate(
  url="https://higgsfield.ai",
  # 需要 Playwright MCP 支持 storageState 参数，目前需通过 browser_run_code 注入
)

# 检查是否已登录
mcp__playwright__browser_snapshot()
# 如果看到 "Dashboard" 等登录后元素，直接进入渲染流程
# 如果看到 "Log in" 按钮，走 Step 1-5 重新登录
```

## D. 反爬 / 验证码

Higgsfield 可能会有：
- Cloudflare 挑战
- reCAPTCHA（v2 勾选框）
- 手机验证码

**策略**：
- 不要尝试自动绕过（违反 ToS，可能封号）
- 弹出真浏览器让用户人工完成这一步
- 完成后 Claude 继续后续步骤

Claude 的交互提示：
```
⚠️ 检测到验证码/CAPTCHA。请在浏览器窗口里手动完成，完成后告诉我"继续"。
```

## E. 执行视频渲染（登录成功后）

### Step 1: 进入创作页

```
mcp__playwright__browser_click(element="Create / New Project button", ref="<ref>")
```

### Step 2: 选择模式（Text-to-Video / Image-to-Video）

```
mcp__playwright__browser_click(element="Text to Video tab", ref="<ref>")
```

### Step 3: 填 Prompt

```
mcp__playwright__browser_type(
  element="Prompt input textarea",
  ref="<ref>",
  text="${PROMPT}"   # 从 cinematic-video skill 生成的 prompt
)
```

### Step 4: 选设置

- 时长（通常 5s / 10s）
- 宽高比（16:9 / 9:16 / 1:1）
- Motion Preset（Higgsfield 特有）

```
mcp__playwright__browser_select_option(
  element="Duration dropdown",
  ref="<ref>",
  values=["10s"]
)
```

### Step 5: 提交渲染（**警告：会扣积分**）

```
# 提交前最后确认（CLAUDE.md 要求）
# 除非用户明确说"跑吧"，否则停下来问
mcp__playwright__browser_click(element="Generate button", ref="<ref>")
```

### Step 6: 轮询完成 + 下载

```
# 渲染一般需要 30s - 2min
mcp__playwright__browser_wait_for(text="Completed", time=180)

# 下载
mcp__playwright__browser_click(element="Download button", ref="<ref>")
# 检查下载目录
```

## F. 错误处理

| 错误 | 可能原因 | 处理 |
|------|---------|------|
| 页面超时 | 网络慢 / Cloudflare 挑战 | 重试 1 次 + 通知用户 |
| 登录失败 | 密码错 / 需要二次验证 | 暂停让用户接手 |
| 无渲染积分 | 账号余额不足 | 停止 + 通知 |
| 选择器找不到 | 页面改版 | 跑 `browser_snapshot` 看新结构，更新本文件选择器 |
| 渲染超时 | 队列长 | 延长 wait_for 到 10min |

## G. 首次填充选择器的流程

用户第一次跑时，让 Claude 做：

1. 用 Playwright MCP 打开 higgsfield.ai
2. 跑 `browser_snapshot` 看完整 DOM
3. 把"登录按钮"、"邮箱输入框"、"密码输入框"、"登录提交按钮"的 ref/selector 记录
4. 更新本文件的 Step 2-3 为真实选择器

**本文件的占位符应该在 Phase 2 落地后替换成真实选择器。**

## H. 安全约定

- **不要 commit 带真实选择器的版本到公开 repo**（fingerprint 风险）
- **不要在选择器里硬编码账号信息**
- **所有密码走 `.env`**
- **渲染积分消耗前必须二次确认**（CLAUDE.md 硬性要求）

---

## I. 其他平台的类似 workflow

需要做的话，在本目录创建：
- `workflows/runway-login.md`
- `workflows/kling-login.md`
- `workflows/luma-login.md`

流程大同小异，主要是选择器不同。每个平台都参考本文件的"A-G"骨架。
