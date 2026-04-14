# Prompts 库

存放已生成 / 验证过的 prompt，方便复用、版本管理、批量渲染。

## 目录约定

```
prompts/
├── README.md                          # 本文件
├── <project-name>/                    # 按项目分组
│   ├── 01-<描述>.md                   # 单条 prompt
│   ├── 02-<描述>.md
│   └── batch.md                       # 批量说明
├── cinematic/                         # 按风格分组（可选）
│   └── ...
└── ecommerce/
    └── ...
```

## 单条 Prompt 文件格式

```markdown
---
id: <唯一 ID，如 cyberpunk-chase-001>
model: <runway-gen3 | kling | higgsfield | luma | sora>
duration: <秒>
aspect_ratio: <16:9 | 9:16 | 1:1 | 2.35:1>
seed: <可选，固定种子>
created: <YYYY-MM-DD>
tags: [cyberpunk, action, night]
status: <draft | tested | production>
---

# <标题>

## Prompt
<最终 prompt 文本，多语言对照>

## Notes
- 备注 1
- 备注 2

## Render History
- 2026-04-14 Runway Gen-3 seed=12345 → 成品 OK
- 2026-04-15 Kling → 动作不够自然，调整运镜后重试
```

## 使用建议

### 命名
- 用 kebab-case：`product-coffee-maker-asmr`
- 加序号便于批量：`01-`, `02-`
- 不要用中文文件名（容易出编码问题）

### 分组
- **按项目**：为一个特定产品/主题收集 5-10 条 A/B 变体
- **按风格**：收藏自己喜欢的"模板 prompt"供复用
- **按平台**：如果只用某一个模型，可以按模型分

### 版本管理
- 一条 prompt 迭代了多版，用 `git log` 看历史
- 大改动改文件名加 `-v2.md`、`-v3.md`
- 最终稳定版标 `status: production`

## 不要提交什么
- **渲染成品**（.mp4）→ 走 `assets/renders/`，已 `.gitignore`
- **API Key / 账号信息**
- **含真实商业客户机密的 prompt**（走单独私仓）

## Tips

- 每条 prompt 标 `tags`，方便后续全文搜索
- 渲染后记得把结果回填到 `Render History`
- 不错的 prompt 可以抽象成"模板"放到对应 skill 的 references 里

## 示例

见 `prompts/_examples/` 目录（如果还没创建，第一次用 `/generate-video` 时会自动建）。
