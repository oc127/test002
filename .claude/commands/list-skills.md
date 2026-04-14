---
description: 列出当前 repo 里所有可用的 Skills 和它们的触发场景
---

# 列出所有可用 Skills

扫描 `.claude/skills/` 下的所有 skill，读取每个 `SKILL.md` 的 YAML frontmatter，
汇总成一张表给用户看。

## 工作流

1. **扫描目录**
   ```
   Glob(".claude/skills/*/SKILL.md")
   ```

2. **读取每个 skill 的 frontmatter**
   ```
   for each SKILL.md:
     读取 name + description 字段
   ```

3. **跳过 `_template`**
   `_template/` 是脚手架，不算可用 skill。

4. **按类型分组展示**
   - **视频生成类**：cinematic-video, ecommerce-video, anime-mv, music-video, 3d-cgi
   - **参考类**：camera-encyclopedia
   - **其他**：用户自己添加的

5. **输出格式**

   ```
   ## 📚 当前可用 Skills (共 N 个)

   ### 🎬 视频生成

   #### cinematic-video
   **触发**: 电影感 / 剧情向 / 史诗感 / cinematic
   **输出**: 电影级 prompt，覆盖 5 大海外视频模型
   **参考文件**: 5 个（叙事/运镜/光照/构图/adapter）

   #### ecommerce-video
   **触发**: 带货 / 电商 / 产品广告 / 2 秒钩子
   **输出**: 转化率导向的电商 prompt
   **参考文件**: 3 个（钩子公式/产品镜头/adapter）

   #### anime-mv
   **触发**: 动漫 / 二次元 / 新海诚 / 宫崎骏
   **输出**: 4 大流派动漫风格 prompt

   #### music-video
   **触发**: MV / 音乐视频 / 嘻哈 / 电子
   **输出**: 7 大音乐流派 MV prompt

   #### 3d-cgi
   **触发**: 3D / CGI / 产品动画 / 工业渲染
   **输出**: CGI 级产品展示 prompt

   ### 📖 参考百科

   #### camera-encyclopedia
   **作用**: 摄影术语词典，被其他 skill 引用
   **不直接调用**，查术语时调

   ---

   想新建 skill？用 `/new-skill <name>`
   想生成视频？用 `/generate-video [创意]`
   ```

6. **末尾提示**
   - 如何调用 skill：直接说对应关键词，Claude 会自动识别
   - 如何新建 skill：`/new-skill`
   - 如何查看 skill 详情：`cat .claude/skills/<name>/SKILL.md`

## 注意事项

- **只展示真正的 skills**，跳过 `_template`
- **触发关键词要从 description 提炼**，不要自己编
- **数字要准**：有多少 references 就写多少，别估计
