# Changelog

所有对这个项目的重要变更记录。

格式参考 [Keep a Changelog](https://keepachangelog.com/zh-CN/1.1.0/)。

---

## [Unreleased]

### TODO
- [ ] Phase 2: 用户注册视频模型账号后，填 `workflows/*-login.md` 的真实选择器
- [ ] Phase 2: 跑通单条端到端渲染验证
- [ ] Phase 2: 跑通批量渲染验证
- [ ] Phase 3: 扩展到其他领域（小红书 / 电商详情页 / 数据采集）
- [ ] Phase 4: 考虑产品化（SaaS / GPT）

---

## [0.2.0] - 2026-04-14（深夜扩充）

### Added

**新增 3 个视频 Skills**：
- `.claude/skills/anime-mv/SKILL.md` — 动漫风格视频，覆盖新海诚/宫崎骏/京阿尼/赛璐璐 4 大流派
- `.claude/skills/music-video/SKILL.md` — 音乐视频 MV，覆盖嘻哈/流行/电子/摇滚/R&B/独立/金属 7 大流派
- `.claude/skills/3d-cgi/SKILL.md` — 3D CGI 产品动画，覆盖 Reveal/Showcase/Abstract/Simulation 4 大类型

**新增 5 条示例 Prompts**（`prompts/_examples/`）：
- `01-cinematic-cyberpunk-chase.md` — 赛博朋克雨夜追车（cinematic-video）
- `02-ecommerce-coffee-maker-batch.md` — 咖啡机 5 变体 A/B 测试（ecommerce-video）
- `03-anime-shinkai-station.md` — 新海诚风格黄昏告别（anime-mv）
- `04-music-video-hiphop.md` — 嘻哈 MV Drop 瞬间（music-video）
- `05-3d-cgi-luxury-watch.md` — 奢侈腕表 CGI Hero（3d-cgi）

**新增浏览器自动化 Workflow**：
- `workflows/kling-login.md` — 可灵（国内首推）登录 + 渲染 + API 调用
- `workflows/runway-login.md` — Runway 登录 + Camera Control + API

**新增 Slash Command**：
- `/list-skills` — 快速列出所有可用 skills

**项目管理**：
- `CHANGELOG.md` — 本文件，记录变更历史

### Stats
- 新增 12 个文件
- 总文件数：37
- 总技能数：5 个可调用 + 1 个参考（camera-encyclopedia）

---

## [0.1.0] - 2026-04-14（初始搭建）

### Added

**项目文档**：
- `README.md` — 项目介绍（中英双语友好）
- `CLAUDE.md` — Claude Code 项目指令与工作流约定
- `GETTING_STARTED.md` — 5 分钟上手指南

**工程基础**：
- `.mcp.json` — Playwright MCP 配置
- `package.json` — Node 依赖声明（@playwright/mcp）
- `.gitignore` — 保护 .env / 渲染成品 / Playwright 状态
- `.env.example` — 5 平台账号模板

**核心 Skills**（`.claude/skills/`）：
- `_template/` — 新 skill 脚手架
- `cinematic-video/` — 电影级视频（含 5 个 references）
  - narrative-frameworks.md（5 段式/三幕式/2 秒钩子）
  - camera-moves.md（20+ 运镜词典）
  - lighting.md（15+ 光照方案）
  - composition.md（20+ 构图技巧）
  - model-adapters.md（Higgsfield/Runway/Kling/Luma/Sora）
- `ecommerce-video/` — 电商广告视频（含 3 个 references）
  - hook-formulas.md（12 种 2 秒钩子公式）
  - product-shot-templates.md（10 种产品镜头）
  - model-adapters.md（电商场景专用）
- `camera-encyclopedia/` — 摄像术语百科（被引用的基础参考）

**Slash 命令**（`.claude/commands/`）：
- `/new-skill` — 快速基于模板建新技能
- `/generate-video` — 引导式生成视频 prompt

**浏览器自动化**（`workflows/`）：
- `higgsfield-login.md` — Higgsfield Seedance 2.0 登录模板
- `batch-render.md` — 批量渲染 + 归档流程

**目录占位**：
- `prompts/README.md`
- `assets/README.md`

### Stats
- 25 个文件，3692 行
- Commit: `9774c65`
- Branch: `claude/review-codebase-9S8gJ`

### Design Decisions

- **Skills 放 `.claude/skills/`** — 让 Claude 自动识别触发，而不是手动引用
- **中英双语内容** — 中文叙述 + 英文技术术语，兼顾本土用户与开源传播
- **模型无关设计** — Skills 写领域知识，`model-adapters.md` 单独处理模型语法
- **Playwright MCP 占位** — Phase 1 只写流程模板，Phase 2 填真实选择器
- **所有密钥走 `.env`** — 硬性规则，写进 CLAUDE.md

### 灵感来源
- [@roman.knox 的 Higgsfield Seedance 项目](https://knoxhub.io/hub)
- Anthropic Claude Code Skills & MCP 机制
- Microsoft Playwright MCP

---

## 版本号说明

- **0.x.x**：早期搭建阶段，接口可能有破坏性变更
- **1.0.0**：第一个正式版本（要求：Phase 2 完成，至少跑通 1 个平台端到端）
- **2.0.0**：领域扩展版本（Phase 3 开始）

## 贡献建议

每次添加 skill / workflow / 重要 prompt，在此追加一条记录。模板：

```markdown
## [版本号] - YYYY-MM-DD

### Added
- 新增内容

### Changed
- 变更内容

### Deprecated
- 即将废弃

### Removed
- 已移除

### Fixed
- Bug 修复

### Security
- 安全相关
```
