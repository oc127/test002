# Claude Skills × AI Studio

> 把 Claude Code 从"聊天工具"改造成"领域自动化工作室"的工程骨架。

灵感来自 [@roman.knox](https://knoxhub.io/hub) 的 Higgsfield Seedance 2.0 × Claude Skills 项目，在此基础上做了**架构泛化**——不绑定具体视频模型，也能迁移到视频以外的领域。

---

## 这是什么

一套可直接用的 **Claude Code 项目模板**，三层架构：

```
Claude Code  (大脑)
   ↓
Skills       (领域知识 - 电影摄影、构图、光照)
   ↓
MCP Servers  (执行层 - Playwright 控制浏览器)
   ↓
外部世界     (Higgsfield / Kling / Runway / 任何网页应用)
```

## 为什么不只是写 prompt？

直接写 prompt 的问题：
- 换个视频模型就要重写
- 团队协作时知识不沉淀
- Claude 不会"自动调用"，每次都要复制粘贴

**Skills 的核心价值**：把领域知识（运镜物理、光照法则、构图三分法）写成 Claude 能**自动匹配场景调用**的结构化模块。你说一句"生成一个赛博朋克雨夜追车"，Claude 会自动调用 `cinematic-video` skill 给你架构出专业 prompt，并可选直接通过 Playwright 去渲染。

## 目录速览

| 路径 | 作用 |
|------|------|
| `.claude/skills/` | 领域专家 Skills（自动调用） |
| `.claude/commands/` | Slash 命令（如 `/new-skill`, `/generate-video`） |
| `.mcp.json` | Playwright 等 MCP 服务器配置 |
| `workflows/` | 浏览器自动化流程模板 |
| `prompts/` | 原始 prompt 版本库 |
| `assets/` | 参考分镜、素材 |

## 当前内置 Skills

- **cinematic-video** — 电影级视频生成（5 段式叙事框架 + 运镜库）
- **ecommerce-video** — 电商广告视频（2 秒钩子公式 + 产品展示模板）
- **camera-encyclopedia** — 镜头百科（运镜术语、镜头语言、光照参数）
- **_template** — 新建 skill 的脚手架

## 快速开始

详见 [GETTING_STARTED.md](./GETTING_STARTED.md)

```bash
# 1. 克隆并进入
git clone <this-repo> && cd test002

# 2. 装 Playwright MCP
npm install

# 3. 在这个目录启动 Claude Code
claude

# 4. 试一句
> 用 cinematic-video skill 帮我设计一个"末日废土少女骑摩托"的 10 秒短片
```

## 使用模式

### 模式 A：只生成 prompt（零成本）

不需要任何付费账号，Claude 用 Skills 帮你架构最强 prompt，你自己粘贴到 Higgsfield/Kling/即梦/Runway 等平台。

### 模式 B：浏览器全自动（需要账号）

配置好 Playwright MCP + 视频模型账号后，Claude 可以：
1. 自动登录目标平台
2. 批量提交 prompt 渲染
3. 下载成片归档

### 模式 C：跨领域复用

换个 Skills 就能做：
- 电商：自动生成商品详情页文案 + 主图
- 小红书：批量生成图文 + 自动排版
- 数据采集：定时抓取网页 + 结构化入库
- 设计：给 Figma/Midjourney/即梦 架构专业 prompt

## 设计哲学

1. **Prompt 不是代码，Skills 才是** — Prompt 易变易失效，Skills 是沉淀下来的领域模型
2. **模型无关** — 视频模型迭代极快，Skills 里写"物理规律"，只在 adapter 里写"某模型怎么描述"
3. **可组合** — 小 skill 组合成大工作流，不要写巨无霸 skill
4. **人机交接要干净** — Claude 负责架构，人负责创意与审美把关

## License

MIT（待添加）

## 致谢

- [@roman.knox](https://knoxhub.io/hub) — 灵感来源
- Anthropic Claude Code 团队 — Skills & MCP 机制
- Microsoft Playwright MCP — 浏览器控制能力
