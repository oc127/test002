# 示例 Prompts

展示各个 skill 能力的参考样本。你可以：
- 直接复制修改后使用
- 用作新 prompt 的起点
- 参考文件结构写自己的 prompt

## 目录

| 文件 | Skill | 风格 | 平台推荐 |
|------|-------|------|---------|
| `01-cinematic-cyberpunk-chase.md` | cinematic-video | 赛博朋克 / 电影 | Runway Gen-3 |
| `02-ecommerce-coffee-maker-batch.md` | ecommerce-video | 电商带货 / 5 变体 A/B | Kling + Runway |
| `03-anime-shinkai-station.md` | anime-mv | 新海诚 / 日系 | Kling + Sora |
| `04-music-video-hiphop.md` | music-video | 嘻哈 / Trap | Kling + Runway + Sora |
| `05-3d-cgi-luxury-watch.md` | 3d-cgi | 奢侈品腕表 | Runway + Luma |

## 使用方式

### 方式 1: 在 Claude Code 里召唤

```
参考 prompts/_examples/01-cinematic-cyberpunk-chase.md 的格式，
帮我做一个末日废土摩托追车的 prompt
```

### 方式 2: 复制修改

```bash
cp prompts/_examples/01-cinematic-cyberpunk-chase.md \
   prompts/my-projects/01-my-video.md

# 然后在新文件里改
```

### 方式 3: 批量渲染

把要跑的 prompt 放到 `prompts/<项目名>/` 下，然后参考
`workflows/batch-render.md` 的流程让 Claude 批量提交。

## 格式约定

每个示例文件必须包含：
- **YAML frontmatter**：id / skill / model / duration / tags / status
- **核心概念**：一句话说清
- **分镜**（如果是多段式）
- **Prompts**：至少覆盖 2 个模型的格式
- **Notes / 变体**：迭代思路
- **Render History**：跑过一次就回填成品链接

## 贡献你的好 Prompt

跑出好成品的 prompt，建议归档到这个目录（注意去除个人敏感信息），
方便未来复用。可以改成：
```
prompts/_library/<风格>/<id>.md
```

然后在对应 skill 的 references 里引用：
> "见 prompts/_library/cinematic/cyberpunk-002 的成功案例"
