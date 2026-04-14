# Assets 目录

存放参考素材、分镜草图、渲染成品等二进制资源。

## 目录约定

```
assets/
├── README.md                # 本文件
├── references/              # 参考素材（风格图、分镜手稿等）
│   └── <项目名>/
├── samples/                 # 示例成品（小体积，可入库）
│   └── <项目名>/
├── renders/                 # 批量渲染的成品（大文件，不入库）
│   └── YYYY-MM-DD-<batch>/
└── downloads/               # 从网页下载的临时文件（不入库）
```

## 什么入库，什么不入库

### ✅ 入库（`git add`）
- `references/` 下的参考图（< 500 KB 的图片）
- `samples/` 下的小体积示例成品（< 5 MB）
- 手绘分镜、flow 图

### ❌ 不入库（已在 `.gitignore`）
- `renders/` — 批量渲染成品，通常每条数 MB-数十 MB
- `downloads/` — 下载临时文件
- 所有 `.mp4`、`.mov`、`.webm`（除 `samples/` 外）

### 🤔 大文件怎么办

如果要团队协作分享大量渲染成品：
1. **Git LFS**：`git lfs track "*.mp4"`，费用和配额要注意
2. **对象存储**：S3 / OSS / R2，在 `.env` 配 S3_* 变量
3. **外链**：存到 Google Drive / 网盘，在 prompt 文件的 Notes 里贴链接

## 命名约定

- **时间戳开头**：`2026-04-14-cyberpunk-v1.mp4`
- **批次目录**：`2026-04-14-product-ad-batch/`
- **版本**：`-v1`, `-v2` 表示迭代
- **参考图**：`reference-<描述>.jpg`，如 `reference-bladerunner-rain.jpg`

## 敏感内容警告

- 不要上传**有版权的参考片段**到公开 repo
- **客户 LOGO / 素材**走单独私有仓库
- **真人面部素材**注意肖像权

## Tips

- 把"启发自己的风格参考"归档到 `references/<project>/`，下次复用
- 把"渲染出来觉得很棒的片段"备份到 `samples/`（压缩后 < 5MB 能入库分享）
- 养成"先命名再存"的习惯，别让资源变成 `Untitled (3).mp4`
