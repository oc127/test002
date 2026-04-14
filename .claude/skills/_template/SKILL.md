---
name: _template
description: 新建 skill 的脚手架。不要直接使用，复制整个 _template/ 目录为新名字再修改。Claude 应忽略此 skill，description 以 "TEMPLATE:" 开头表示不自动调用。
---

<!--
=============================================================
  这是 SKILL 脚手架。使用方式：
  1. 复制整个 _template/ 目录 → 新命名（例如 music-video/、smallredbook-content/）
  2. 改 YAML frontmatter 的 name 和 description
  3. description 要写清"什么场景下 Claude 应该调用这个 skill"——这是 Claude 决定是否调用的关键
  4. 按下面的结构填充领域知识，删除所有 <!-- ... --> 注释
  5. 把 references/ 下的参考文件按需增删
=============================================================
-->

# Skill 名称（显示用）

## 调用时机 (When to invoke)

<!-- 写清 5-10 个触发关键词或典型场景句式，例如：-->
用户说到以下关键词时自动调用：
- "xxx 风格"
- "做一个 xxx"
- "xxx 感觉的"

典型请求示例：
- "帮我生成一个 [具体场景] 的 [媒介]"
- "用 [主题] 做个 [时长] 的 [媒介]"

## 输出什么 (What to produce)

<!-- 明确这个 skill 返回给用户的成品格式，例如：-->
- 一段结构化的 prompt（可直接粘贴到目标平台）
- 一份分镜脚本（如果是视频）
- 一组参数建议（如时长、比例、帧率）

## 工作流 (Workflow)

1. **理解需求**：提取主题、风格、时长/尺寸、目标平台
2. **选择框架**：根据需求查 `references/xxx.md`
3. **填充细节**：依序决定 [关键维度 A] → [B] → [C]
4. **适配输出**：查 `references/model-adapters.md` 转成目标模型的 prompt 格式
5. **给用户**：附上 1 句简要说明为什么这样架构

## 领域核心知识

<!-- 这里写该领域的"第一性原理"——为什么这样做 prompt 效果最好。
     这是 skill 的价值所在，不要只写"怎么做"，要写"为什么这样做"。
-->

### 原理一：[标题]
解释……

### 原理二：[标题]
解释……

## 决策树 (Decision tree)

<!-- 给 Claude 快速匹配场景的映射表，例如：-->

| 用户需求关键词 | 选用框架 | 参考文件 |
|---|---|---|
| 紧张/悬疑 | xxx | references/xxx.md |
| 浪漫/唯美 | yyy | references/yyy.md |
| 幽默/反差 | zzz | references/zzz.md |

## 参考文件 (References)

<!-- 列出 references/ 下的子文件，说明各自用途 -->
- `references/xxx.md` — [用途说明]
- `references/yyy.md` — [用途说明]
- `references/model-adapters.md` — 不同模型的 prompt 格式转换

## 注意事项 (Gotchas)

- 不要……
- 必须……
- 如果用户没说……就问清楚再生成

## 质量自检 (Self-check before returning)

Claude 在输出前应确认：
- [ ] 主题/风格/时长都明确了吗？
- [ ] prompt 覆盖了 [核心维度]？
- [ ] 用了正确的模型 adapter 格式？
- [ ] 是否需要提醒用户调整参数（如比例、帧率）？
