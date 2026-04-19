# 排错指南 (Troubleshooting)

遇到问题时按症状查表，直接跳到对应章节。

## 快速定位

| 症状 | 章节 |
|------|------|
| Claude Code 启动报 Auth conflict | [A](#a-auth-conflict) |
| Playwright MCP 连不上 / 0 tools | [B](#b-playwright-mcp-连接问题) |
| VS Code 里 MCP 不可用 | [B5](#b5-vs-code-里-mcp-不可用) |
| Higgsfield 渲染 Failed | [C](#c-higgsfield-渲染-failed) |
| Higgsfield NSFW 警告 | [C4](#c4-内容审核误触发) |
| Higgsfield 下载失败 | [D](#d-higgsfield-下载失败) |
| Skill 没被自动调用 | [E](#e-skill-未被自动调用) |
| Skills 路径不对 / 没加载 | [E5](#e5-skills-文件路径错误) |
| Claude 自己写 prompt 不调 skill | [H](#h-claude-自己写-prompt-不调用-skill) |
| Claude 导航到错误 URL | [I](#i-claude-导航到错误-url) |
| 视频质量差（模糊/崩脸/畸变） | [F](#f-视频质量问题) |
| 环境变量 / API Key 问题 | [G](#g-环境变量问题) |

---

## A. Auth Conflict

**症状**：
```
⚠️Auth conflict: Both a token (claude.ai) and an API key (ANTHROPIC_API_KEY) are set.
```

**原因**：`.zshrc` / `.bashrc` 里有 `export ANTHROPIC_API_KEY=...`，跟 Claude Max 订阅的 OAuth token 冲突。

**解决**：
```bash
# 1. 找出哪个文件在 set API key
grep -n "ANTHROPIC" ~/.zshrc ~/.bashrc ~/.zprofile ~/.bash_profile 2>/dev/null

# 2. 注释掉那一行
sed -i '' '/^export ANTHROPIC_/s/^/# /' ~/.zshrc

# 3. 重载 shell
exec zsh

# 4. 验证清空
env | grep ANTHROPIC
# 期望：无输出

# 5. 重启 Claude Code
cd ~/projects/test002 && claude
```

**预期结果**：底部状态栏显示 `Opus 4.x · Claude Max`（不再是 `API Usage Billing`）

---

## B. Playwright MCP 连接问题

**症状**：
- `/mcp` 显示 `playwright ✗ failed` 或 `0 tools`
- 启动时报 `MCP server failed to start`

**排查步骤**：

### B1. Node.js 版本不够
```bash
node --version
# 需要 v18+（推荐 v20+）
```

### B2. npx 找不到包
```bash
# 确认在项目目录
cd ~/projects/test002
# 重装依赖
npm install
# 手动测试 npx 能否跑
npx @playwright/mcp@latest --help
```

### B3. .mcp.json 配置错误
```bash
cat .mcp.json
```
正确格式：
```json
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": ["-y", "@playwright/mcp@latest"],
      "env": {}
    }
  }
}
```

### B4. Chromium 没装
```bash
npx playwright install chromium
```

### B5. Mac 权限弹窗
首次启动 Playwright 时 macOS 可能弹 "允许控制浏览器" 权限框，注意右上角弹窗。

### B5. VS Code 里 MCP 不可用

**症状**：VS Code 里 Claude Code 找不到 Playwright MCP。

**解决**：
1. 确认 `.mcp.json` 存在于项目文件夹根目录
2. **完全退出** VS Code（不是 Reload Window，是 Quit），重新打开
3. 打开项目时会弹出 MCP 通知 → 点 **Allow**
4. 在 Claude Code 对话里输入 `/mcp` 确认 playwright 已列出

---

## C. Higgsfield 渲染 Failed

**症状**：视频提交后状态变为 "Failed"，无法播放。

**排查清单**（按概率排序）：

### C1. Prompt 含 Banned Words（最常见！）
Higgsfield 内容审核会拦截特定词汇。查看 `.claude/skills/_shared/content-filter.md` 完整列表。

**高频中招词**：
- `fire` / `flame` / `burning` → 改用 `warm amber glow` / `luminance`
- `explosion` / `explodes` → 改用 `radial particle scatter`
- `destroy` → 改用 `dissolve` / `transform`
- `violent` → 改用 `dynamic` / `energetic`
- `crack` → 改用 `opens along the edge`

**验证方法**：把 prompt 逐词对照 content-filter.md 的禁用词列表。

### C2. Prompt 过长
Seedance 2.0 对 prompt 长度有上限。如果 prompt 超过 500 词，尝试精简。

### C3. 模型不支持该功能
| 功能 | Seedance 2.0 Standard | Kling 3.0 Exclusive |
|------|----------------------|---------------------|
| Text-to-Video | ✅ | ✅ |
| Image-to-Video | ❌ | ✅ |
| 最高分辨率 | 720p | 1080p |

如果你需要 Image-to-Video（图生视频），**不能用 Seedance 2.0 Standard**，要切到 Kling 3.0 Exclusive。

### C4. 内容审核误触发
某些场景描述（武器、血液、裸露皮肤）即使用了安全替代词也可能被拦截。尝试进一步软化描述。

### C5. 服务端临时问题
等 5 分钟重试。如果持续失败，换一个略有不同的 prompt 再试。

---

## D. Higgsfield 下载失败

**症状**：视频渲染成功（能看到缩略图），但 "Preparing download" 显示 "Failed"。

**解决方案**（按简到繁）：

### D1. 直接去 Assets 页面
```
https://higgsfield.ai/asset/all
```
点击视频缩略图进入详情页，看有没有 Download 按钮。

### D2. 右键视频保存
在视频播放器上右键 → "Save Video As..." / "将视频存储为..."

### D3. DevTools 抓视频 URL
1. `Cmd + Option + I` 打开 DevTools
2. 切到 **Network** 标签（不是 Elements）
3. Filter 框输入 `mp4`
4. 播放视频
5. Network 里出现 `.mp4` 请求 → 右键 → Open in new tab
6. 新标签 `Cmd+S` 保存

### D4. CDN 问题
Higgsfield 的下载 CDN 偶尔抽风。等几小时再试，或换网络环境。

---

## E. Skill 未被自动调用

**症状**：你说了关键词但 Claude 没有调用对应 skill，给了通用回答。

**排查**：

### E1. 确认在项目目录启动
```bash
# Claude Code 必须在 test002 目录启动才能读到 skills
cd ~/projects/test002 && claude
```

### E2. Skill 的 description 不够明确
检查 SKILL.md 的 YAML frontmatter `description` 字段，确保包含足够的触发关键词。

### E3. 多 Skill 触发冲突
如果你的请求同时匹配多个 skill（比如"动漫打斗"同时匹配 anime-mv 和 fight-scenes），明确指定：
```
用 fight-scenes skill 帮我做一个动漫打斗场景
```

### E4. CLAUDE.md 没被读取
检查 Claude Code 启动时是否显示项目路径：
```
~/projects/test002    ← 应该在左下角
```
如果显示 `/Users/xxx`（家目录），说明没在项目目录。

### E5. Skills 文件路径错误

某些安装器会把 skills 放到 `~/Library/Application Support/Claude/skills/`，但 Claude Code 读的是 `~/.claude/skills/`。

**验证**：
```bash
ls ~/.claude/skills/ | head -20
```

应该能看到 `cinematic-video`, `fight-scenes` 等目录。如果没有，拷贝过来：
```bash
cp -r ~/Library/Application\ Support/Claude/skills/* ~/.claude/skills/
```

---

## F. 视频质量问题

| 问题 | 可能原因 | 解决 |
|------|---------|------|
| **人脸崩坏** | 复杂动作 + 没用 Character | 用 Character 功能训练面部 + 图生视频 |
| **画面模糊** | 720p + prompt 过于复杂 | 简化 prompt，或升级到 1080p 模型 |
| **动作不连贯** | 单次生成时间太长(10s) | 拆成 2 个 5s，后期拼接 |
| **色彩跳变** | prompt 含多种色彩描述 | 明确主色调（如 "dominant warm orange palette"） |
| **运镜不执行** | Seedance 对复杂运镜支持有限 | 一次只描述 1 种运镜，不混合 |
| **主体消失** | 场景过于复杂 | 减少背景元素，突出主体 |
| **风格不一致** | 多段视频风格各异 | 所有段使用相同的 seed + 固定风格词 |

---

## G. 环境变量问题

### G1. API Key 写在哪里
```bash
# 所有密钥写到 .env（已在 .gitignore 中排除）
cat ~/projects/test002/.env

# 不要写进 .zshrc / .bashrc（会被 source 到所有 shell）
# 不要截图发给任何人
```

### G2. Lucy / Claude Code 读不到 .env
确认 `.env` 在项目根目录：
```bash
ls -la ~/projects/test002/.env
```

### G3. Key 泄露了怎么办
1. 立刻去对应平台撤销 / 删除旧 Key
2. 生成新 Key
3. 更新 `.env`
4. 检查 git 历史确认没有 commit 过 Key：
```bash
git log --all -p -- .env
# 应该没有输出（.env 在 .gitignore 里）
```

---

## 常见错误速查

| 错误信息 | 原因 | 快速修复 |
|---------|------|---------|
| `API Error: 403 forbidden` | API Key 无效或过期 | 重新获取 Key |
| `Auth conflict` | 多认证源冲突 | 见 §A |
| `SessionStart:startup hook error` | PAI 框架残留 | `mv ~/.claude/settings.json ~/.claude/settings.json.bak` |
| `MCP server failed to start` | Node/npx 问题 | 见 §B |
| `Claude Code has switched from npm to native installer` | 安装方式变更提示 | 忽略，不影响功能 |
| `Request not allowed` | 账号权限或 Key 错误 | 检查 Key + 登录状态 |

---

## H. Claude 自己写 Prompt 不调用 Skill

**症状**：Claude 没有调用专业 skill，而是自己凭空写了一个 prompt。

**解决**：

### H1. 开新会话
Skill 有时在长对话后"忘记"。开一个新会话重试。

### H2. 拆成两步（最稳）
如果 Claude 反复不调 skill，拆成两个独立步骤：

**会话 1**：只生成 prompt
```
/07-ecommerce-ad
帮我生成 3 条 KitKat 广告 prompt，保存到 prompts.txt
```

**会话 2**：只提交到 Higgsfield
```
读取 prompts.txt 里的 prompt，逐条提交到 Higgsfield
```

### H3. 显式指定 Skill 名
```
用 fight-scenes skill（不是你自己写的 prompt）帮我设计一个打斗场景
```

---

## I. Claude 导航到错误 URL

**症状**：Claude 通过 Playwright 打开了错误的 Higgsfield 页面。

**正确 URL**：
```
https://higgsfield.ai/create/video
```

**解决**：在 prompt 中明确指定：
```
导航到 https://higgsfield.ai/create/video 并提交 prompt
```

CLAUDE.md 中已配置了默认 URL，如果仍然导航错误，检查 CLAUDE.md 是否被正确加载（见 §E4）。
