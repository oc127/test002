# Getting Started

从零到第一个自动生成的视频 prompt。

## 前置条件

| 必需 | 说明 |
|------|------|
| Claude Code | [安装指南](https://docs.claude.com/claude-code) |
| Node.js 18+ | Playwright MCP 需要 |
| 浏览器 | Chrome / Edge / Firefox（Playwright 会自动下载） |

可选（Phase 2 才需要）：
- Higgsfield.ai 账号（或 Kling / Runway / 即梦 等）

## 5 分钟上手

### 1. 克隆并安装

```bash
git clone <this-repo-url> test002
cd test002
npm install
```

### 2. 启动 Claude Code

```bash
claude
```

首次启动时，Claude Code 会读到 `.mcp.json`，提示你是否信任 Playwright MCP 服务器 — 选"是"。

### 3. 验证环境

在 Claude Code 对话里输入：

```
/doctor
```

确认 `playwright` MCP 已连接。如果没连上，检查：
- `node --version` 是否 ≥ 18
- 是否装了 `npx`（应该随 Node.js 自带）

### 4. 试生成第一个 prompt（不需要账号）

```
帮我用 cinematic-video skill 设计一个 10 秒短片：
主题是"末日废土少女骑着改装摩托穿过沙尘暴"
要求：冷色调 + 慢动作 + 史诗感
```

Claude 会自动调用 `cinematic-video` skill，返回结构化 prompt。

### 5. 试浏览器自动化（可选，需要 Higgsfield 账号）

```
用 Playwright 打开 higgsfield.ai，帮我登录（我会手动扫码）
```

Claude 会弹出真实浏览器，你扫码登录后告诉它"好了"，后续渲染就能全自动。

---

## 目录布局

```
test002/
├── CLAUDE.md                  # Claude Code 项目指令（必读）
├── README.md                  # 项目介绍
├── GETTING_STARTED.md         # 本文件
├── .mcp.json                  # MCP 服务器配置
├── .env.example               # 环境变量模板
├── package.json               # Node 依赖
│
├── .claude/
│   ├── skills/                # 核心：领域 Skills
│   │   ├── _template/         # 新 skill 脚手架
│   │   ├── cinematic-video/   # 电影级视频
│   │   ├── ecommerce-video/   # 电商视频
│   │   └── camera-encyclopedia/ # 镜头百科
│   └── commands/              # Slash 命令
│       ├── new-skill.md       # /new-skill
│       └── generate-video.md  # /generate-video
│
├── workflows/                 # 浏览器自动化流程
│   ├── higgsfield-login.md
│   └── batch-render.md
│
├── prompts/                   # 成品 prompt 库
└── assets/                    # 参考素材
```

## 常用姿势

### 生成一个视频 prompt

```
用 cinematic-video 生成一个 [风格/主题] 的 [时长] 秒短片
```

### 批量生成同系列

```
用 ecommerce-video 给这款蓝牙耳机生成 5 条不同卖点的 2 秒钩子视频
```

### 新建一个领域 skill

```
/new-skill anime-mv
```

然后告诉 Claude 这个领域要涵盖什么知识，它会帮你填充 skill 内容。

### 让 Claude 自动渲染

```
用刚才生成的 prompt，自动跑 higgsfield-login 流程并提交渲染
```

## 下一步

- 想接视频模型账号？看 `workflows/higgsfield-login.md`
- 想加新领域 skill？看 `.claude/skills/_template/SKILL.md`
- 想批量生产？看 `workflows/batch-render.md`

## 排查

**Q: Playwright MCP 连不上**
A: 手动跑 `npx -y @playwright/mcp@latest --help`，看看是否报错。通常是 Node 版本问题。

**Q: Skill 没被自动调用**
A: 看 `.claude/skills/<name>/SKILL.md` 的 YAML frontmatter 里 `description` 写得够不够明确。Claude 根据 description 决定是否调用。

**Q: 不想每次确认 Playwright 权限**
A: 在 Claude Code 里运行 `/permissions` 给 playwright 加白名单。
