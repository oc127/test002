---
description: 基于 _template 快速创建一个新的领域 skill
argument-hint: <skill-name> [领域描述]
---

# 新建 Skill: $ARGUMENTS

你要帮用户基于 `.claude/skills/_template/` 创建一个新的 skill。

## 步骤

1. **解析参数**
   - `$ARGUMENTS` 第一个词是 skill 名（kebab-case，如 `anime-mv`、`xiaohongshu-content`）
   - 其余是领域描述（可能缺失，缺失就引导用户说清楚）

2. **验证名称合法性**
   - 必须是 kebab-case（小写 + 连字符）
   - 不能是已存在的 skill 名
   - 用 Glob 检查 `.claude/skills/<name>/` 是否已存在
   - 如果已存在，停止并提示用户换个名字

3. **引导用户明确 4 个关键问题**（用 AskUserQuestion 或直接问）
   - **何时调用**：用户说什么关键词 / 什么场景下 Claude 应该自动调用这个 skill？
   - **输出什么**：这个 skill 返回什么格式的成品？（prompt / 分镜 / 图片描述 / JSON 数据）
   - **核心知识**：该领域最重要的 3-5 条第一性原理是什么？
   - **需要多少 references**：要不要拆 `references/` 子文件？一般简单 skill 不需要，复杂的需要。

4. **复制模板并定制**
   - 复制 `.claude/skills/_template/` 整个目录为 `.claude/skills/<skill-name>/`
   - 修改 `SKILL.md` 的 YAML frontmatter：
     - `name: <skill-name>`
     - `description:` 用用户描述填充，要明确触发词
   - 根据用户回答，填充各个章节
   - 删除所有 `<!-- ... -->` 注释

5. **提示下一步**
   - 告诉用户：
     - 新 skill 路径
     - 重启 Claude Code 或用 `/reload` 让新 skill 生效
     - 如何测试触发（给一个示例句子）

## 注意事项

- **不要直接修改 `_template/`**，那是脚手架
- **description 要好**：Claude 是否自动调用完全取决于 description 的匹配度
- **先问清楚再建文件**，不要未经确认就创建满是空内容的 skill

## 示例对话流

```
用户: /new-skill anime-mv 动漫 MV 风格视频

你: 好，我要新建一个叫 anime-mv 的 skill，领域是"动漫 MV 风格视频"。
    在建立之前，我需要确认 4 件事：

    1. 哪些关键词/场景应该触发这个 skill？
       例如：用户说"做个 MV / 二次元 / 动漫感 / J-pop 风"
       你希望还覆盖哪些词？

    2. 成品输出什么？
       a) 只生成 prompt（给 AI 视频模型）
       b) 完整分镜 + prompt
       c) 其他？

    3. 动漫 MV 的核心"第一性原理"是什么？
       （我会结合电影理论写，但你可能有独到的偏好）

    4. 要不要拆 references/？
       例如：anime-visual-styles.md（分宫崎骏、新海诚、京都动画风）、
             mv-pacing.md（MV 剪辑节奏）、
             model-adapters.md

...（用户回答后）...

你: 好，现在创建 skill。
    [执行创建]

    ✅ 已创建 `.claude/skills/anime-mv/`
    重启 Claude Code 后，试试说"帮我做个新海诚风格的 MV"就能触发。
```
