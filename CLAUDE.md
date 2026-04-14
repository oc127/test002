# Claude Code Project Memory

这是一个 **"Claude Code + Playwright MCP + 领域 Skills"** 架构的工程骨架，用来把 Claude 从"聊天助手"变成"专业领域自动化工作室"。

当前主要领域：**AI 视频生成**（Higgsfield Seedance 2.0 等），架构本身可迁移到电商、设计、数据采集等其他领域。

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

- [x] 工程骨架搭建
- [x] 核心 skills: cinematic-video, ecommerce-video, camera-encyclopedia
- [x] Playwright MCP 配置
- [ ] 接入具体视频模型账号（等用户注册）
- [ ] 批量渲染工作流实际跑通
- [ ] 扩展到其他领域（电商运营、设计出图等）

## 给未来 Claude Code 会话的提示

用户第一次来时可能会问"怎么用这个 repo"，引导他们：
1. 读 `GETTING_STARTED.md` 装依赖
2. 运行 `/doctor` 检查 MCP 是否连上
3. 试一句："帮我用 cinematic-video skill 生成一个赛博朋克雨夜追车的 prompt"
