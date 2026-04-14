---
name: camera-encyclopedia
description: 摄影与电影摄像机术语百科。当用户询问专业名词（景别、焦段、光圈、帧率、运镜、打光等）或需要准确使用影视摄影术语时调用。也被其他 skill（cinematic-video、ecommerce-video）引用作为底层参考。中英文对照，含视觉效果示意与适用场景。
---

# 摄像机 / 摄影术语百科

被其他 skill 引用的底层参考库。**不用来生成 prompt**，专门用来当"词典"查术语。

---

## A. 景别（Shot Size / Framing）

景别决定"观众离主体多远"，直接影响情绪。

| 中文 | 英文 | 缩写 | 包含 | 情绪效果 |
|------|------|------|------|---------|
| 极远景 | Extreme Long Shot | ELS | 主体只是一个小点 | 史诗、孤独、渺小 |
| 远景 | Long Shot / Wide Shot | LS / WS | 主体全身 + 大量环境 | 空间感、交代环境 |
| 全景 | Full Shot | FS | 主体完整身体 | 动作感 |
| 中全景 | Medium Long Shot | MLS | 膝盖以上 | 半身动作 |
| 中景 | Medium Shot | MS | 腰部以上 | 对话、互动 |
| 中近景 | Medium Close-Up | MCU | 胸部以上 | 访谈、情绪 |
| 近景 | Close-Up | CU | 头部 / 肩部 | 情感、心理 |
| 大特写 | Extreme Close-Up | ECU | 眼睛、嘴唇、手指 | 极致强调、细节 |
| 定场镜头 | Establishing Shot | ES | 场景全景 | 开场建立场景 |
| 插入镜头 | Insert Shot | — | 物品/细节特写 | 强调关键元素 |
| 反应镜头 | Reaction Shot | — | 观看者的脸 | 情绪反应 |

---

## B. 镜头焦段（Lens Focal Length）

焦段决定"视野多宽 + 畸变 + 空间压缩感"。

| 焦段 | 类型 | 视觉效果 | 适用 |
|------|------|---------|------|
| **8-16mm** | 鱼眼 Fisheye | 极度畸变，球面感 | 极端风格、运动相机 |
| **16-24mm** | 超广角 Ultra-wide | 视野极宽，边缘畸变 | 风景、建筑、压迫 |
| **24-35mm** | 广角 Wide | 视野宽，轻微畸变 | 环境、街拍、VLog |
| **35mm** | 准标准 Quasi-standard | 自然感，电影常用 | 纪录片、故事片 |
| **50mm** | 标准 Standard | 接近人眼视角 | 人像、日常 |
| **85mm** | 人像 Portrait | 浅景深，面部好看 | 人像、情感戏 |
| **100-135mm** | 短长焦 Short Telephoto | 压缩空间 | 人像、隔空拍 |
| **200-300mm** | 长焦 Telephoto | 强压缩、强虚化 | 野生动物、隔空偷拍 |
| **400mm+** | 超长焦 Super-telephoto | 极度压缩 | 体育、监视感 |

### 焦段的情绪暗示
- **广角（< 35mm）**：拉近距离、空间大、沉浸、但也可扭曲
- **标准（50mm）**：真实、平衡、日常
- **长焦（> 85mm）**：疏离、压缩、偷窥、背景虚化

---

## C. 光圈（Aperture / F-stop）

光圈决定"进光量 + 景深"。

| F值 | 光圈大小 | 景深 | 进光 | 适用 |
|-----|---------|------|------|------|
| f/1.2 | 极大 | 极浅 | 极多 | 夜景人像、极度背景虚化 |
| f/1.4 | 很大 | 很浅 | 很多 | 人像、电影感 |
| f/2.0 | 大 | 浅 | 多 | 人像、室内 |
| f/2.8 | 较大 | 较浅 | 较多 | 人像、低光 |
| f/4.0 | 中 | 中 | 中 | 通用 |
| f/5.6 | 较小 | 较深 | 较少 | 双人合影 |
| f/8.0 | 小 | 深 | 少 | 风景、多人 |
| f/11-16 | 很小 | 很深 | 很少 | 大风景、全场景清晰 |
| f/22+ | 极小 | 极深 | 极少 | 超景深、光芒星芒效果 |

### AI 视频 Prompt 里的光圈表达
- "shallow depth of field" = 浅景深（大光圈 f/1.4-2.8）
- "deep focus" = 深焦（小光圈 f/8+，一切都清晰）
- "bokeh" = 焦外虚化（大光圈效果）
- "background blur" = 背景虚化

---

## D. 快门速度（Shutter Speed）

影响"运动模糊"。

| 快门 | 效果 | 适用 |
|------|------|------|
| 1/2000s 以上 | 冻结瞬间 | 极速运动、水珠飞溅 |
| 1/500s | 清晰冻结 | 体育 |
| 1/250s | 轻微模糊 | 普通动作 |
| 1/125s | 标准 | 日常 |
| 1/60s | 人类手持极限 | 静物 |
| 1/30s | 明显动态模糊 | 梦境感 |
| 1s 以上 | 极长曝光 | 光轨、水流如绸 |

### 电影的 180° 快门规则
- 电影标准：**快门时长 = 帧率倒数 × 2**
- 24fps → 1/48s（近似 1/50s）快门
- 这个比例产生"电影感"动态模糊
- Prompt 写法：`cinematic motion blur, 180 degree shutter`

---

## E. 帧率（Frame Rate）

帧率决定"视频的流畅度 + 风格"。

| 帧率 | 风格 | 适用 |
|------|------|------|
| 24 fps | 电影感 | 电影、剧情 |
| 25 fps | PAL 电视 | 欧洲电视 |
| 30 fps | 视频 | 网络视频标准 |
| 48 / 50 fps | 高帧 | 体育、纪实 |
| 60 fps | 丝滑 | 游戏、运动 |
| 120 fps | 慢动作素材 | 后期 4x 慢放 |
| 240 fps+ | 超慢动作 | 液体、爆炸 |
| 1000 fps+ | 科学慢动作 | 研究 |

### AI 视频的帧率
- 多数 AI 视频模型默认 24/30 fps
- 想要慢动作效果，在 prompt 里写 `slow motion` / `high-speed capture`
- 想要复古感：`film grain 24fps cinematic`

---

## F. 运镜术语速查

（详细版见 `cinematic-video/references/camera-moves.md`）

### 移动类
| 中文 | 英文 | 本质 |
|------|------|------|
| 推 | Push in / Dolly in | 镜头前移 |
| 拉 | Pull out / Dolly out | 镜头后移 |
| 摇 | Pan | 原地水平转 |
| 摆 | Tilt | 原地垂直转 |
| 移 | Truck / Track | 横向平移 |
| 升/降 | Crane up/down | 垂直升降 |
| 跟 | Follow / Tracking | 跟随主体 |
| 绕 | Orbit / Arc | 绕主体转 |

### 焦段类
| 中文 | 英文 | 本质 |
|------|------|------|
| 变焦 | Zoom | 焦段拉长/变短 |
| 变焦推拉 | Dolly Zoom / Vertigo | 镜头前进同时 zoom out |
| 快变焦 | Crash Zoom | 突然快速 zoom |

### 稳定类
| 中文 | 英文 | 本质 |
|------|------|------|
| 手持 | Handheld | 模拟手抖 |
| 稳定器 | Steadicam / Gimbal | 平滑跟拍 |
| 肩扛 | Shoulder mount | 类手持略稳 |

### 视角类
| 中文 | 英文 | 本质 |
|------|------|------|
| 主观镜头 | POV | 第一视角 |
| 低角度 | Low angle | 仰拍 |
| 高角度 | High angle | 俯拍 |
| 鸟瞰 | Bird's eye / Top-down | 垂直俯拍 |
| 荷兰角 | Dutch angle | 倾斜画面 |

---

## G. 光照术语速查

（详细版见 `cinematic-video/references/lighting.md`）

### 光源方向
| 中文 | 英文 | 效果 |
|------|------|------|
| 正面光 | Front light | 平面化、无阴影 |
| 侧光 | Side light | 立体、戏剧 |
| 逆光 | Back light | 剪影、勾边 |
| 顶光 | Top light | 威严、诡异 |
| 底光 | Bottom light / Under light | 恐怖、异常 |
| 轮廓光 | Rim light | 勾勒主体轮廓 |

### 光的硬度
| 中文 | 英文 | 特性 |
|------|------|------|
| 硬光 | Hard light | 阴影锐利、高对比 |
| 软光 | Soft light | 阴影柔和、低对比 |
| 柔光 | Diffused light | 散射后的软光 |

### 色温
| 中文 | 英文 | 色温 K |
|------|------|--------|
| 烛光 | Candlelight | 1800 K |
| 钨丝灯 | Tungsten | 3200 K |
| 日光 | Daylight | 5600 K |
| 阴天 | Overcast | 6500 K |
| 蓝天 | Clear sky shade | 8000 K+ |

### 经典打光
| 中文 | 英文 | 特征 |
|------|------|------|
| 三点布光 | Three-point lighting | 主+补+轮廓 |
| 伦勃朗光 | Rembrandt lighting | 脸颊三角光斑 |
| 分割光 | Split lighting | 脸一半亮一半暗 |
| 高调 | High key | 整体亮、低对比 |
| 低调 | Low key | 整体暗、高对比 |
| 蝶形光 | Butterfly / Paramount | 鼻下有蝶形阴影 |

---

## H. 构图术语速查

（详细版见 `cinematic-video/references/composition.md`）

| 中文 | 英文 | 要点 |
|------|------|------|
| 三分法 | Rule of thirds | 主体在 1/3 交点 |
| 对称 | Symmetry | 左右/上下镜像 |
| 引导线 | Leading lines | 线条指向主体 |
| 黄金分割 | Golden ratio | 螺旋交汇点 |
| 负空间 | Negative space | 大面积留白 |
| 框中框 | Frame within frame | 用元素框住主体 |
| 前景 | Foreground | 最近的一层 |
| 中景 | Midground | 中间层 |
| 背景 | Background | 最远的一层 |
| 景深 | Depth of field (DOF) | 清晰范围 |

---

## I. 色彩术语

| 中文 | 英文 | 含义 |
|------|------|------|
| 色温 | Color temperature | 冷暖 |
| 色调 | Hue | 具体颜色 |
| 饱和度 | Saturation | 颜色浓度 |
| 明度 | Value / Luminance | 亮度 |
| 色彩分级 | Color grading | 后期调色 |
| LUT | LUT (Look-Up Table) | 色彩预设 |
| 蓝橙 | Teal & Orange | 肤橙阴青 |
| 黑金 | Black & Gold | 暗调暖光 |

---

## J. 胶片/质感参考

常在 prompt 里引用，大部分 AI 视频模型能识别：

| 胶片 / 风格 | 特点 |
|------------|------|
| Kodak Portra 400 | 柔肤、低饱和 |
| Kodak Gold 200 | 暖黄、复古 |
| Kodak Ektar 100 | 高饱和风景 |
| Kodak 500T | 电影胶片、低光 |
| Fuji Pro 400H | 清冷、绿调 |
| Fuji Velvia 50 | 极高饱和 |
| Cinestill 800T | 霓虹光晕 |
| Ilford HP5 | 粗颗粒黑白 |
| VHS aesthetic | 磁带感、噪点、彩带干扰 |
| 16mm film | 复古电影、颗粒感 |
| 35mm anamorphic | 宽银幕电影 |
| IMAX | 超高分辨率、大画幅 |

---

## K. 影视流派风格参考（Prompt 里常用的"导演/电影风"）

| 风格 | 特征 | 关键词 |
|------|------|--------|
| 王家卫 Wong Kar-wai | 霓虹、慢镜、粉青、港风 | `Wong Kar-wai style, teal and amber` |
| 韦斯·安德森 Wes Anderson | 对称、饱和、复古、中心构图 | `Wes Anderson aesthetic, symmetrical, pastel palette` |
| 塔可夫斯基 Tarkovsky | 长镜头、诗意、自然 | `Tarkovsky-esque, poetic long takes` |
| 库布里克 Kubrick | 对称、一点透视 | `Kubrickian one-point perspective symmetry` |
| 大卫·芬奇 Fincher | 暗调、精准、绿调 | `Fincher-style green-tinted dark mood` |
| 诺兰 Nolan | IMAX、实景、复杂叙事 | `Nolan cinematography, IMAX aesthetic` |
| 迈克尔·贝 Michael Bay | 爆炸、仰拍、英雄 | `Michael Bay hero shot` |
| Blade Runner 2049 | 烟雾、大色块、反乌托邦 | `Blade Runner 2049 dystopian color palette` |
| A24 | 独立电影质感、冷静、克制 | `A24 indie cinematic aesthetic` |

---

## L. 重要 Tips

### 在 Prompt 里引用术语时
- **优先英文**：多数模型英文训练语料多
- **简洁具体**：`35mm anamorphic, shallow DOF` 胜过 `shot like a movie`
- **组合使用**：景别 + 焦段 + 运镜 + 光照 = 完整镜头语言

### 查不到术语怎么办
这个百科覆盖 90% 场景。真的冷门术语：
1. 先问自己"这个术语对画面产生什么效果"
2. 用"效果"的英文描述代替术语
3. 例：查不到"low-key chiaroscuro" → 写 "dark dramatic lighting with single light source and deep shadows"
