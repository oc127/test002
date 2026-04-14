# 光照设计库 (Lighting Design)

光照决定画面的"情绪 70%"。同一个场景不同打光 = 完全不同的电影。

---

## A. 光照基本原理

### 光的 3 个维度

| 维度 | 选项 | 情绪影响 |
|------|------|---------|
| **方向** | 正面 / 侧面 / 背面 / 顶光 / 底光 | 平面化 / 立体 / 剪影 / 威严 / 诡异 |
| **硬度** | 硬光 (hard) / 软光 (soft) | 戏剧、硬朗 / 温柔、日常 |
| **色温** | 暖 (3200K) / 中性 (5600K) / 冷 (7000K+) | 温馨 / 日常 / 冰冷 |

### 光的 3 种来源（写 prompt 时要说清楚）

1. **主光 Key Light** — 最强光源，决定画面亮面
2. **补光 Fill Light** — 弱光，减淡主光阴影
3. **轮廓光 / 背光 Rim / Back Light** — 从背后打，勾勒主体轮廓

完整布光叫 **三点布光 (Three-point Lighting)**，是电影打光的基本盘。

---

## B. 经典光照方案（直接套用）

### 1. 三点布光 (Three-Point Lighting)
- **描述**：主光从一侧 45° 斜上打，补光从对侧略弱，背光从后上方勾边
- **情绪**：标准、专业、访谈、正式
- **适用**：人物对话、采访、企业宣传片
- **Prompt 写法**：`classic three-point lighting, key light from 45 degrees, fill light reducing shadows, rim light separating subject from background`

### 2. 伦勃朗光 (Rembrandt Lighting)
- **描述**：单侧主光，在远侧脸颊形成一个三角形光斑
- **情绪**：古典、绘画感、深邃、戏剧
- **适用**：肖像、历史剧、艺术片
- **Prompt 写法**：`Rembrandt lighting, with a characteristic triangle of light on the cheek`

### 3. 高调光 (High Key)
- **描述**：整体高亮度、低对比，几乎无阴影
- **情绪**：明亮、快乐、日常、青春
- **适用**：喜剧、时尚、美妆、儿童
- **Prompt 写法**：`high-key lighting, bright and evenly lit, minimal shadows`

### 4. 低调光 (Low Key)
- **描述**：大面积阴影 + 局部强光，高对比
- **情绪**：悬疑、神秘、电影黑色 (film noir)
- **适用**：黑色电影、悬疑、恐怖、硬汉
- **Prompt 写法**：`low-key lighting, deep shadows with dramatic highlights, film noir style`

### 5. 剪影 (Silhouette)
- **描述**：主体完全暗，背景亮
- **情绪**：神秘、匿名、强调轮廓
- **适用**：结尾、转场、悬疑登场
- **Prompt 写法**：`silhouette of the subject against a bright [背景]`

---

## C. 自然光方案

### 6. 黄金时刻 (Golden Hour)
- **描述**：日出后 / 日落前 1 小时，阳光低角度金黄色
- **情绪**：浪漫、温暖、史诗、希望
- **适用**：浪漫、治愈、开场/结尾
- **Prompt 写法**：`golden hour lighting, warm orange sunlight at low angle, long shadows`
- **色温**：约 2500-3500K

### 7. 蓝调时刻 (Blue Hour)
- **描述**：日落后 / 日出前约 30 分钟，天空深蓝
- **情绪**：宁静、忧郁、城市夜幕
- **适用**：都市、孤独、爱情文艺
- **Prompt 写法**：`blue hour, deep blue sky after sunset, cool ambient light`
- **色温**：约 7000-10000K

### 8. 顶光正午 (Harsh Midday Sun)
- **描述**：太阳正上方，硬光、短阴影
- **情绪**：酷热、压抑、末世、冷峻
- **适用**：西部片、荒漠、末日
- **Prompt 写法**：`harsh midday sunlight from directly above, sharp short shadows`

### 9. 阴天柔光 (Overcast / Soft Daylight)
- **描述**：云层散射，整体柔和无阴影
- **情绪**：平静、忧伤、日常、纪录片感
- **适用**：纪实、日常、低饱和叙事
- **Prompt 写法**：`overcast sky, soft diffused daylight, no harsh shadows`

### 10. 窗光 (Window Light)
- **描述**：单侧窗户自然光，室内明暗对比强
- **情绪**：私密、怀旧、文艺
- **适用**：室内肖像、情感戏、回忆
- **Prompt 写法**：`soft window light from the left, creating natural light fall-off`

### 11. 丁达尔光 (God Rays / Volumetric Light)
- **描述**：光穿过灰尘/雾/树叶形成可见光柱
- **情绪**：神圣、梦幻、希望、启示
- **适用**：森林、教堂、史诗揭示
- **Prompt 写法**：`volumetric god rays piercing through [介质], dust particles visible in the light`

---

## D. 人工光方案

### 12. 霓虹光 (Neon Lighting)
- **描述**：多色霓虹灯，常见青蓝 + 洋红组合
- **情绪**：赛博朋克、都市夜景、反叛
- **适用**：赛博、港风、都市夜
- **Prompt 写法**：`neon lighting with cyan and magenta tones, reflections on wet surfaces`

### 13. 实用光源 (Practical Lights)
- **描述**：画面中可见的光源（台灯、蜡烛、手电筒、屏幕）
- **情绪**：真实、沉浸、情境
- **适用**：室内戏、夜景、悬疑
- **Prompt 写法**：`scene lit only by practical lights visible in frame: [台灯/蜡烛/屏幕]`

### 14. 频闪 (Strobe)
- **描述**：灯光闪烁
- **情绪**：混乱、狂欢、暴力瞬间
- **适用**：夜店、迪斯科、MV 高潮
- **Prompt 写法**：`strobing lights flashing rapidly, creating staccato motion`

### 15. 舞台光 (Stage / Theatrical Lighting)
- **描述**：彩色聚光灯从多角度打
- **情绪**：戏剧、仪式、表演
- **适用**：演唱会、舞台、MV
- **Prompt 写法**：`theatrical stage lighting with colored spotlights from multiple angles`

---

## E. 情绪 → 光照 映射表

| 情绪目标 | 光照方案 | 色温 | 硬度 |
|---------|---------|------|------|
| 浪漫 | 黄金时刻 + 柔光 | 暖 3000K | 软 |
| 悬疑 | 低调光 + 实用光源 | 冷 6000K | 硬 |
| 史诗 | 黄金时刻 + 逆光 + 丁达尔光 | 暖 2500K | 中硬 |
| 恐怖 | 底光 + 单一硬光源 | 中性 5000K | 极硬 |
| 赛博朋克 | 霓虹多光源 + 雨 | 极冷青 + 洋红 | 中 |
| 日常 | 窗光 / 阴天柔光 | 中性 5000-5600K | 软 |
| 末日 | 顶光 + 扬尘 + 降饱和 | 中性偏暖 | 硬 |
| 孤独 | 单一光源 + 大暗部 | 冷 6500K | 硬 |
| 梦幻 | 柔焦逆光 + 丁达尔 | 暖粉 3500K | 软 |
| 冰冷 | 蓝调时刻 / 冷霓虹 | 极冷 8000K | 中 |

---

## F. 色彩学基础（配色方案）

### 1. Teal & Orange 蓝橙
- **描述**：肤色橙 + 阴影青绿
- **适用**：主流好莱坞大片
- **Prompt 关键词**：`teal and orange color grade, cinematic look`

### 2. Cyan & Magenta 青洋红
- **描述**：冷青色主调 + 洋红点缀
- **适用**：赛博朋克、迈阿密霓虹
- **Prompt 关键词**：`cyberpunk cyan and magenta color palette`

### 3. Monochrome 单色
- **描述**：黑白 / 单一色调
- **适用**：艺术、回忆、极简
- **Prompt 关键词**：`monochrome black and white` / `sepia tone`

### 4. High Saturation 高饱和
- **描述**：所有颜色极饱和
- **适用**：韦斯·安德森、漫画感、复古
- **Prompt 关键词**：`Wes Anderson-inspired, highly saturated pastel palette`

### 5. Desaturated 低饱和
- **描述**：褪色、粗粝
- **适用**：末日、战争、纪实
- **Prompt 关键词**：`desaturated color palette, washed-out look`

### 6. Wong Kar-wai 王家卫风
- **描述**：青绿 + 暖黄对比 + 灯箱光
- **适用**：港味、怀旧、都市爱情
- **Prompt 关键词**：`Wong Kar-wai style, teal and amber tones, nostalgic 1990s Hong Kong atmosphere`

---

## G. 胶片参考（经典胶片的色彩特性）

在 prompt 里引用胶片型号，大部分 AI 模型能识别：

| 胶片 | 特性 | 适用 |
|------|------|------|
| Kodak Portra 400 | 柔和肤色、低饱和 | 人像 |
| Kodak Gold 200 | 暖黄、复古 | 日常、复古 |
| Kodak Ektar 100 | 高饱和风景 | 风景 |
| Kodak 500T | 电影胶片、低光 | 电影 |
| Fuji Pro 400H | 清冷、绿调 | 时尚 |
| Fuji Velvia 50 | 极高饱和 | 风景 |
| Cinestill 800T | 霓虹光晕 | 赛博朋克夜景 |
| Ilford HP5 | 粗颗粒黑白 | 纪实、艺术 |

**Prompt 写法**：`shot on Kodak 500T film, grainy cinematic look`

---

## H. 常见错误

1. **只说"电影感"不说具体方案** — 模型会给你平庸结果
2. **同时要求多种对立光照** — "柔和但是戏剧性的硬光"会拉胯
3. **忽略色温** — "温暖"太模糊，"3000K 暖色"明确
4. **光源方向不明** — 必须说清"从哪边来"
5. **不提光源性质** — 自然光 vs 人工光 vs 实用光差很多
