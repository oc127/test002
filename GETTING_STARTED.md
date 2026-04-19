# Getting Started

从零到第一个自动生成的视频。

## What This Does

Claude Code 使用 Playwright MCP 控制你的浏览器，在 Higgsfield 上自动化视频生成。你描述一个产品或概念，Claude 调用专业的 Seedance 2.0 skill 生成高质量 prompt，然后自动导航到 Higgsfield，填入 prompt，点击生成——**全程不用你动手**。

**工作流**：
1. 你输入简单描述（例："3 个 KitKat 广告"）
2. Claude 调用对应 skill 生成 prompt
3. Claude 通过 Playwright 打开 Higgsfield
4. Claude 逐条提交 prompt，等待生成，继续下一条

## 前置条件

| 必需 | 说明 |
|------|------|
| [Claude Code](https://claude.ai/code) | CLI 或 VS Code 扩展 |
| Node.js 18+ | Playwright MCP 需要（自带 npx） |
| Git | 克隆项目 |
| Higgsfield 账号 | [higgsfield.ai](https://higgsfield.ai)（免费注册） |

## Setup

### 1. 添加 Playwright MCP（全局，所有项目可用）

```bash
claude mcp add -s user playwright npx '@playwright/mcp@latest'
```

### 2. 克隆并进入项目

```bash
git clone <this-repo-url> test002
cd test002
npm install
```

### 3. 启动 Claude Code

```bash
claude
```

首次启动时会提示你是否信任 `.mcp.json` 中的 Playwright MCP — 选 **Allow**。

### 4. 登录 Higgsfield

在 Claude Code 对话里输入：

```
Use Playwright MCP to open https://higgsfield.ai in the browser and wait
```

浏览器会弹出。**手动登录**（邮箱或 Google）。登录完成后回到 Claude 说 "logged in"。

### 5. 开始生成

```
3 video ads for KitKat chocolate bar
```

Claude 会自动调用 skill、生成 prompt、提交到 Higgsfield、等待生成。

---

## 使用示例

### 基础：生成并提交广告

```
3 ads for KitKat chocolate bar
```

```
2 ads for InstaCarousel — SaaS that automates Instagram carousels, saves 5 hours per week
```

```
1 cinematic ad for a luxury coffee brand
```

### 使用参考图片（Image-to-Video，质量更好）

把图片放到项目文件夹，然后提及它：

```
3 KitKat ads, use ref.jpg
```

Claude 会自动通过 `browser_upload_file` 上传图片到 Higgsfield，进入 Image-to-Video 模式。

### 只生成 prompt（不提交，零成本）

```
用 cinematic-video skill 设计一个 10 秒短片：
主题是"末日废土少女骑着改装摩托穿过沙尘暴"
要求：冷色调 + 慢动作 + 史诗感
```

Claude 会返回结构化 prompt，你自己粘贴到任何平台。

### 批量生成同系列

```
用 ecommerce-video 给这款蓝牙耳机生成 5 条不同卖点的 2 秒钩子视频
```

### 指定 Skill

```
用 fight-scenes skill 设计一个 Owen 骑龙 vs 石像巨人的 5 秒打斗
```

```
用 food-beverage skill 做一个汉堡的慢动作 hero shot
```

### 新建自定义 Skill

```
/new-skill my-new-domain
```

---

## 15 个可用 Skills

| # | Skill | 用途 |
|---|-------|------|
| 01 | cinematic-video | 电影级叙事、预告片 |
| 02 | 3d-cgi | 3D 渲染、CGI、Unreal Engine |
| 03 | cartoon | 2D 卡通、Pixar、Disney |
| 04 | comic-to-video | 漫画分镜→视频 |
| 05 | fight-scenes | 打斗、格斗、动作编排 |
| 06 | motion-design-ad | SaaS、App、科技产品 |
| 07 | ecommerce-video | 实物产品、电商广告 |
| 08 | anime-mv | 动漫、日系动画 |
| 09 | product-360 | 360° 产品转台 |
| 10 | music-video | MV、节奏感视频 |
| 11 | social-hook | TikTok/Reels 爆款 |
| 12 | brand-story | 品牌叙事、创始人故事 |
| 13 | fashion-lookbook | 时尚、走秀、Lookbook |
| 14 | food-beverage | 美食、饮品、餐厅 |
| 15 | real-estate | 房产、建筑、室内设计 |

---

## 目录布局

```
test002/
├── CLAUDE.md                  # Claude 项目指令（自动加载）
├── README.md                  # 项目介绍
├── GETTING_STARTED.md         # 本文件
├── TROUBLESHOOTING.md         # 排错指南
├── .mcp.json                  # Playwright MCP 配置
├── .env.example               # 环境变量模板
├── package.json               # Node 依赖
│
├── .claude/
│   ├── skills/                # 核心：15 个领域 Skills
│   │   ├── _template/         # 新 skill 脚手架
│   │   ├── _shared/           # 共享基础设施
│   │   │   └── content-filter.md  # Higgsfield banned words
│   │   ├── cinematic-video/   # 电影级
│   │   ├── ecommerce-video/   # 电商
│   │   ├── anime-mv/          # 动漫
│   │   ├── music-video/       # 音乐 MV
│   │   ├── 3d-cgi/            # 3D CGI
│   │   ├── fight-scenes/      # 打斗
│   │   ├── social-hook/       # 社媒爆款
│   │   ├── cartoon/           # 卡通
│   │   ├── brand-story/       # 品牌叙事
│   │   ├── comic-to-video/    # 漫画→视频
│   │   ├── motion-design-ad/  # 科技广告
│   │   ├── product-360/       # 产品转台
│   │   ├── fashion-lookbook/  # 时尚
│   │   ├── food-beverage/     # 美食
│   │   ├── real-estate/       # 房产
│   │   └── camera-encyclopedia/ # 镜头百科（参考）
│   └── commands/              # Slash 命令
│       ├── new-skill.md       # /new-skill
│       ├── generate-video.md  # /generate-video
│       └── list-skills.md     # /list-skills
│
├── workflows/                 # 浏览器自动化流程模板
│   ├── higgsfield-login.md
│   ├── kling-login.md
│   ├── runway-login.md
│   └── batch-render.md
│
├── prompts/                   # 成品 prompt 库
│   └── _examples/             # 示例 prompts
└── assets/                    # 参考素材 + 渲染输出
```

## 排错

遇到问题？看 [TROUBLESHOOTING.md](./TROUBLESHOOTING.md)，覆盖 7 大类常见问题。

快速排查：

**Q: Playwright MCP 连不上**
A: 运行 `npx -y @playwright/mcp@latest --help` 确认 Node 可用。详见 TROUBLESHOOTING.md §B。

**Q: Higgsfield 视频 Failed**
A: 大概率是 prompt 含 banned words（fire/explosion/destroy 等）。详见 TROUBLESHOOTING.md §C。

**Q: Skill 没被自动调用**
A: 确认在项目目录启动 Claude Code。详见 TROUBLESHOOTING.md §E。
