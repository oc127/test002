# 工作流：批量渲染

从一个 prompt 列表自动批量生成视频，下载归档。

---

## A. 前置条件

- 已走通 `workflows/higgsfield-login.md`（或其他平台的登录 workflow）
- `prompts/` 目录下已有待渲染的 prompt 文件
- 有足够的渲染积分
- `.env` 里 `ALLOW_PAID_OPERATIONS=true`（用户明确授权）

## B. Prompt 文件格式

`prompts/` 下的文件按统一格式：

### 单条 prompt：`prompts/cyberpunk-chase.md`

```markdown
---
id: cyberpunk-chase-001
model: runway-gen3
duration: 10
aspect_ratio: 16:9
created: 2026-04-14
---

# 赛博朋克雨夜追车

## Prompt
Slow tracking shot following a female rider on a modified motorcycle through
neon-lit rain-soaked alleys. Cyan and magenta neon reflections on wet pavement.
Sparks fly as she drifts around a corner. Cinematic Blade Runner 2049 aesthetic.

## Notes
- Seed: 12345
- 第 1 版，电影感强但动作略慢
```

### 批量 prompt：`prompts/product-ad-batch/`

目录下每个 `.md` 一条：
```
prompts/product-ad-batch/
├── 01-pain-hook.md
├── 02-asmr-detail.md
├── 03-ugc-review.md
├── 04-before-after.md
└── 05-hero-product.md
```

所有文件共享同一个 `seed`（用同一主播形象）或分别指定。

---

## C. 批量渲染执行步骤

### Step 1: 扫描 prompts 目录

Claude 读取 `prompts/` 下所有 `.md` 文件（或用户指定的子目录）：

```
Glob("prompts/**/*.md")
```

解析每个文件的 frontmatter + Prompt 章节。

### Step 2: 预检

在开始之前，Claude 必须给用户一个**确认清单**：

```
📋 批量渲染预览

共 5 条 prompt 待渲染：
1. 01-pain-hook (Runway Gen-3, 10s, 9:16)
2. 02-asmr-detail (Runway Gen-3, 6s, 9:16)
3. 03-ugc-review (Kling 2.0, 15s, 9:16)
4. 04-before-after (Runway Gen-3, 8s, 16:9)
5. 05-hero-product (Higgsfield, 10s, 16:9)

预估积分消耗：~ 500 credits
预估总耗时：~ 20 分钟（每条 2-4 分钟）
输出目录：assets/renders/2026-04-14-product-batch/

是否继续？(y/n)
```

**用户明确说 y 才能继续**。CLAUDE.md 硬性要求：扣积分前必须确认。

### Step 3: 登录目标平台

根据 frontmatter 里的 `model`：
- `runway-gen3` → 先登录 Runway
- `kling` → 登录 Kling
- `higgsfield` → 登录 Higgsfield

如果一批 prompt 跨多平台，分组处理。

### Step 4: 逐条渲染

```
for prompt in batch:
    navigate(平台创作页)
    fill(prompt_text)
    select(duration, aspect_ratio)
    click(Generate)
    wait_for("Completed", max=300s)
    download(保存到 assets/renders/{date}-{batch_name}/{prompt_id}.mp4)
    log(✓ {prompt_id} done)
```

### Step 5: 失败处理

某条失败时：
- 记录错误（`assets/renders/.../errors.log`）
- 继续下一条（不要因为一条停住整批）
- 最后汇总成功/失败数

### Step 6: 汇总报告

结束后给用户：

```
✅ 批量渲染完成

成功：4 / 5
失败：1 / 5
  - 03-ugc-review: Kling timeout after 5min

输出目录：assets/renders/2026-04-14-product-batch/
- 01-pain-hook.mp4 (2.1 MB)
- 02-asmr-detail.mp4 (1.4 MB)
- 04-before-after.mp4 (1.8 MB)
- 05-hero-product.mp4 (2.3 MB)

失败的 03-ugc-review 可以单独重试：
  /retry prompts/product-ad-batch/03-ugc-review.md
```

---

## D. 高级：并发批量

部分平台支持并行渲染（后台队列）：
- Runway: 多个 job 并发，自动排队
- Kling: 每账号限 1-2 个并发
- Higgsfield: 队列制

**Claude 的策略**：
- 默认串行（最稳）
- 如用户指定 `parallel=true`，则一次性提交所有 prompt，然后轮询状态
- 并发提交代码骨架：
  ```
  # 提交所有任务
  for prompt in batch:
      submit(prompt)  # 不等待完成
      sleep(2)  # 避免触发反爬
      
  # 轮询所有任务状态
  while not all_completed:
      check_status(all_jobs)
      sleep(30)
  
  # 统一下载
  for job in completed:
      download(job)
  ```

---

## E. 输出目录约定

```
assets/renders/
├── YYYY-MM-DD-<batch-name>/    # 按日期 + 批次命名
│   ├── 01-xxx.mp4
│   ├── 02-xxx.mp4
│   ├── metadata.json            # 保存 prompt/模型/参数
│   └── errors.log               # 失败记录
```

`metadata.json` 内容示例：
```json
{
  "batch_name": "product-ad-batch",
  "date": "2026-04-14",
  "total": 5,
  "successful": 4,
  "failed": 1,
  "results": [
    {
      "id": "01-pain-hook",
      "prompt_file": "prompts/product-ad-batch/01-pain-hook.md",
      "model": "runway-gen3",
      "output": "01-pain-hook.mp4",
      "duration_seconds": 10,
      "seed": 12345,
      "credits_used": 100,
      "render_time_seconds": 180,
      "status": "success"
    },
    ...
  ]
}
```

---

## F. 常用调用姿势

### 调用 1：渲染单条

```
用刚才保存在 prompts/cyberpunk-chase.md 的 prompt，
去 Runway 渲染一次。
```

### 调用 2：渲染整个目录

```
把 prompts/product-ad-batch/ 目录下 5 条 prompt 全部跑一遍。
```

### 调用 3：预检不执行

```
扫描 prompts/，告诉我会消耗多少积分，不要真跑。
```

### 调用 4：只对失败的重试

```
把上次 assets/renders/2026-04-14-product-batch/errors.log 里失败的条目重跑一次。
```

---

## G. 成本控制

### 估算规则（大致）

| 模型 | 每秒视频 credits | 10 秒总计 |
|------|----------------|----------|
| Runway Gen-3 | 10 | 100 |
| Higgsfield Seedance 2.0 | 8 | 80 |
| Kling 2.0 | 5-15（看时长和质量） | 50-150 |
| Luma Ray 2 | 1-5（按 resolution） | 10-50 |
| Sora | 按配额计 | 看订阅 |

> 以上为 2025 年中期平均价格，实际以平台为准。

### 预算守护

在 `.env` 加：
```
MAX_BATCH_CREDITS=1000   # 单批最多消耗
DAILY_CREDIT_LIMIT=5000  # 每天总上限
```

Claude 在执行前检查：
- 预估 > MAX_BATCH_CREDITS → 停下来让用户确认
- 本日累计 > DAILY_CREDIT_LIMIT → 停止

---

## H. 故障排查

### Q: 渲染一半积分没了
A: 记录已完成的，剩下的标记为 `skipped: insufficient credits`，让用户充值后 `/resume`。

### Q: 下载的视频打不开
A: 检查文件大小。<100KB 可能是错误页，不是真实视频。自动重试一次。

### Q: 同一 prompt 多次结果差异大
A: AI 视频本来就有随机性。加 `seed` 能减少波动。同 seed 同 prompt 结果应该一致。

### Q: 页面改版导致选择器失效
A: 让 Claude 跑 `browser_snapshot` 看新 DOM，更新 `workflows/<platform>-login.md` 里的选择器。

---

## I. Phase 1 当前状态

**当前本 workflow 只是文档模板**，真正跑起来需要：
1. 用户注册对应平台账号
2. 首次登录后填真实 DOM 选择器
3. 跑一次单条验证流程
4. 再上批量

Phase 2 的任务清单（Roadmap）：
- [ ] 注册 Runway / Kling / Luma / Higgsfield 至少 1 个
- [ ] 跑通 `higgsfield-login.md`（或其他平台的对应文件）
- [ ] 填真实选择器
- [ ] 跑 1 条单渲染验证
- [ ] 跑 5 条批量验证
- [ ] 写成品示例到 `assets/samples/`
