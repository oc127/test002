# Claude Code Project Memory

这是一个 **"Claude Code + Playwright MCP + 领域 Skills"** 架构的工程骨架，用来把 Claude 从"聊天助手"变成"专业领域自动化工作室"。

当前主要领域：**AI 视频生成**（Higgsfield Seedance 2.0 等），架构本身可迁移到电商、设计、数据采集等其他领域。

## ⚠️ CONTENT FILTER — 生成 Higgsfield Prompt 前必读

Higgsfield 的内容审核会拦截以下词汇（即使在完全无害的上下文中）。**生成 Higgsfield prompt 前必须逐词扫描并替换**：

| 禁用词 | 安全替代词 |
|--------|----------|
| explosion, explodes, exploding | radial particle scatter, dynamic reveal |
| burst, bursts | radiates outward, fans out, expands |
| smashes, crashes, slams | transitions into, resolves into |
| snap, snaps | separates, divides, parts cleanly |
| break, breaks, broken | separates, opens, reveals |
| crack, cracks | opens along the edge, parts at the seam |
| shatter, shards | separates cleanly, dissolves |
| pull-apart, tear, rip | gentle separation, parts along the seam |
| impact, collision | transition, shift, contact |
| blows up, detonates | transforms, morphs, reveals |
| crush, crushed | press, compress, flatten smoothly |
| fire, flame, burning, ignite | warm amber glow, luminance, warm light |
| destroy, obliterate | dissolve, transform, fade out |
| violent, aggressive | dynamic, energetic, bold |
| naked, bare, exposed, raw | clean, minimal, natural, uncoated |

**强制规则**：替换时只改禁用词本身，不碰 prompt 其他任何内容。完整替换表和语境指南见 `.claude/skills/_shared/content-filter.md`。此规则仅对 Higgsfield 生效，Kling/Runway/Luma/Sora 保留原词。

## 默认工作流

**先 Skill 再 Playwright**，分两步：

**Step 1 — 调用 Skill 生成 Prompt**：
1. 根据用户需求调用对应 skill
2. 获取完整 prompt 输出
3. 过 content filter（替换 banned words）
4. 展示最终 prompt 给用户确认

**Step 2 — 通过 Playwright 提交**（仅在 Step 1 完成后）：
1. 导航到 Higgsfield 创作页
2. 把 prompt **原样逐字** 填入输入框（不删减、不合并段落、不改格式）
3. 设置参数（默认：Seedance 2.0, 9:16, 8s, 1 variation）
4. 点 Generate → 等 1 分钟 → 截图确认

## Generation Mode（批量生成循环）

假设 Higgsfield 已登录、素材已上传。对每个 variation 执行：

1. Navigate to `https://higgsfield.ai/create/video`
2. 点击 prompt 输入框，清空，逐字输入 prompt
3. 点 Generate
4. 报告："Variation [X] submitted — waiting 1 minute..."
5. 等 1 分钟
6. 截图——如果 loading spinner 仍在转，再等 1 分钟
7. 报告："✓ Variation [X] done — moving to next"
8. 重复下一个 variation

## Playwright MCP 规则

**只用这 5 个工具**，不用 browser-use skill，不跑 Python：
- `browser_navigate`
- `browser_click`
- `browser_type`
- `browser_screenshot`
- `browser_upload_file`

如果弹出 promo modal 或 cookie banner，先关掉再操作。
Higgsfield URL: `https://higgsfield.ai/create/video`

## Prompt Engineering

使用 skill 输出的完整 prompt——保留所有结构、长度、时间标记和创意方向。**不要摘要、不要缩短、不要重新格式化**。唯一允许的改动是替换 banned words。

## Reference Images

如果用户提供了图片路径，使用 `browser_upload_file` 上传，进入 Image-to-Video 模式。

## 架构三层

```
┌─────────────────────────────────────────────────┐
│  Claude Code (大脑 - 推理与编排)                 │
├─────────────────────────────────────────────────┤
│  Skills (专业知识 - 领域框架与 prompt 模板)       │
│    .claude/skills/*/SKILL.md                     │
├─────────────────────────────────────────────────┤
│  MCP Servers (四肢 - 工具与外部世界)              │
│    Playwright MCP → 控制浏览器                   │
└─────────────────────────────────────────────────┘
```

- **Skills** = 领域专家知识（电影运镜、光照物理、构图法则），封装为 Claude 能自动调用的结构化框架
- **MCP** = 执行层，让 Claude 真实操作浏览器/API/文件系统
- **Claude Code** = 编排者，接收用户创意 → 调用 Skills 生成 prompt → 调用 MCP 执行

## 工作流约定

### 接到视频生成需求时

1. **先问"要什么风格"**（电影级 / 电商 / 动漫 / MV / 3D CGI）— 决定调用哪个 skill
2. **调用对应 skill**（如 `cinematic-video`）获取领域框架
3. **用 skill 的 2 秒钩子 + 5 段式结构**生成 prompt
4. **参考 `camera-encyclopedia`** 精确描述运镜/光照/构图
5. 如果已配置 Playwright MCP + 有账号：**自动打开浏览器执行渲染**
6. 如果没配置：**输出最终 prompt 给用户手动粘贴**

### 接到新领域需求时

1. 先检查 `.claude/skills/` 有没有对应 skill
2. 没有就用 `/new-skill` 基于 `_template` 创建
3. 把领域知识结构化填进去（不要只写 prompt，要写"为什么这样 prompt"）

## 关键文件位置

| 作用 | 路径 |
|------|------|
| Skills（自动调用） | `.claude/skills/*/SKILL.md` |
| Slash 命令 | `.claude/commands/*.md` |
| MCP 服务器配置 | `.mcp.json` |
| 浏览器自动化流程 | `workflows/*.md` |
| 原始 prompt 库 | `prompts/` |
| 参考素材 | `assets/` |

## 硬性要求

- **不要把 API Key 写进代码或 commit**。所有密钥走 `.env`（已在 `.gitignore`）
- **不要自作主张打开浏览器做付费操作**（生成视频会扣积分）。除非用户明确授权，只生成 prompt
- **Skills 内容要"模型无关"**：写清"为什么这样描述镜头"，而不是只给某个模型的死 prompt。换模型时只改 adapter 部分
- **中英文并存**：面向中文用户 UI 用中文；技术术语（prompt、shot、frame rate）保持英文
- **不要修改 `.claude/skills/_template/`**，那是新建 skill 的脚手架

## 当前状态

### Phase 1 & 1.5 (已完成，v0.2.0)
- [x] 工程骨架 + 项目文档
- [x] Playwright MCP 配置
- [x] 15 个视频 Skills:
  - cinematic-video（电影级，含 5 个 references）
  - ecommerce-video（电商广告，含 3 个 references）
  - anime-mv（4 大动漫流派）
  - music-video（7 大音乐流派）
  - 3d-cgi（CGI 产品动画）
  - fight-scenes（打斗编排，3 大风格 + 安全词汇）
  - social-hook（社媒爆款，0.5s 钩子 + 竖屏构图）
  - cartoon（2D 卡通，4 大西方动画流派）
  - brand-story（品牌叙事，4 种模板 + 纪录片手持）
  - comic-to-video（漫画分镜 → 视频，3 种翻译模式）
  - motion-design-ad（SaaS/科技 Motion Design，4 种类型）
  - product-360（360° 产品转台，3 种模式）
  - fashion-lookbook（时尚走秀，4 种风格 + 面料语言）
  - food-beverage（美食视频，5 种类型 + 食物质感词典）
  - real-estate（房产建筑，4 种类型 + 空间感技巧）
- [x] camera-encyclopedia（参考百科）
- [x] content-filter（Higgsfield banned words 替换表）
- [x] 3 个 slash 命令：/new-skill, /generate-video, /list-skills
- [x] 3 个 workflow 模板：higgsfield / kling / runway
- [x] 5 个示例 prompts（prompts/_examples/）
- [x] TROUBLESHOOTING.md（结构化排错指南）

### Phase 2 (待用户有账号后)
- [ ] 用户注册至少一个平台（推荐 Kling 或即梦）
- [ ] 首次登录填真实选择器
- [ ] 跑通单条渲染端到端
- [ ] 跑通批量渲染

### Phase 3 (领域扩展)
- [ ] 小红书图文生产 skill
- [ ] 电商详情页生成 skill
- [ ] 数据采集 / 竞品监控 skill

## 给未来 Claude Code 会话的提示

用户第一次来时可能会问"怎么用这个 repo"，引导他们：
1. 读 `GETTING_STARTED.md` 装依赖
2. 运行 `/doctor` 检查 MCP 是否连上
3. 运行 `/list-skills` 看所有可用技能
4. 试一句："帮我用 cinematic-video skill 生成一个赛博朋克雨夜追车的 prompt"
5. 参考 `prompts/_examples/` 里的示例理解 prompt 写法

**如果用户想做视频生成但没账号**：推荐先注册**可灵（Kling）**，手机号即可，
新用户送免费积分，中文 prompt 最好用。参考 `workflows/kling-login.md`。
