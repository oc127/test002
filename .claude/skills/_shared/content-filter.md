# Higgsfield 内容过滤词替换表 (Content Filter)

Higgsfield 的内容审核系统会拦截以下词汇，**即使在完全无害的 motion design 上下文中也会触发**。
所有 skill 在生成 Higgsfield Seedance 2.0 prompt 时，必须自动将禁用词替换为安全替代词。

> **适用范围**：仅对 Higgsfield 平台生效。Runway / Kling / Luma / Sora 等其他平台**保留原始词汇**，不做替换。

## 替换规则表

| # | 禁用词（Never use） | 安全替代词（Use instead） |
|---|---|---|
| 1 | explosion, explodes, exploding | radial particle scatter, dynamic reveal |
| 2 | burst, bursts | radiates outward, fans out, expands, pulses |
| 3 | smashes, crashes, slams | transitions into, resolves into, shifts to |
| 4 | snap, snaps | separates, divides, parts cleanly |
| 5 | break, breaks, broken | separates, opens, reveals |
| 6 | crack, cracks | opens along the edge, parts at the seam |
| 7 | shatter, shards | separates cleanly, dissolves |
| 8 | pull-apart, tear, rip | gentle separation, parts along the seam |
| 9 | impact, collision | transition, shift, contact |
| 10 | blows up, detonates | transforms, morphs, reveals |
| 11 | crush, crushed | press, compress, flatten smoothly |
| 12 | fire, flame, burning, ignite | warm amber glow, luminance, warm light |
| 13 | destroy, obliterate | dissolve, transform, fade out |
| 14 | violent, aggressive | dynamic, energetic, bold, forceful |
| 15 | naked, bare, exposed, raw | clean, minimal, natural, uncoated |

## 语境注意事项

某些禁用词在特定语境下需要更精细的替换：

| 原始用法 | 语境 | 推荐替换 |
|---------|------|---------|
| "fire warrior" | 角色描述 | "luminance warrior" 或 "ember-glow warrior" |
| "campfire" | 场景元素 | "warm amber glow from ground level" |
| "fireplace" | 室内场景 | "hearth with warm luminance" |
| "crack in the wall" | 材质描述 | "textured surface with fine separation lines" |
| "broken glass" | 特效 | "glass that separates cleanly" |
| "flames licking upward" | 火焰动作 | "warm amber glow intensifying upward" |
| "explosion of color" | 比喻 | "radial scatter of color" 或 "dynamic color reveal" |
| "fire dragon" | 生物描述 | "luminance dragon" 或 "ember-scaled dragon" |
| "flame breath" | 龙的能力 | "radiant energy projection" 或 "warm luminance beam" |

## 高危场景（禁用词密度最高的领域）

以下 skill 类型的 prompt 最容易触发内容过滤，生成时需格外注意：

1. **fight-scenes** — 打斗场景几乎每句都含高危词（impact, explosion, smash, destroy, violent）
2. **cinematic-video** — 光照描述常用 fire, flame, burning
3. **3d-cgi** — 材质描述常用 crack, shatter, exposed
4. **anime-mv** — 赛璐璐动作派常用 explosive, impact, violent

## 强制验证清单

Claude 在输出任何 Higgsfield prompt 之前，必须完成以下检查：

- [ ] 逐条扫描 15 组禁用词（含变体形式）
- [ ] 仅替换匹配的禁用词，**不修改 prompt 其他任何内容**
- [ ] 替换后重读确认语义不变形（"warm amber glow" 是否在上下文中合理）
- [ ] 确认替换后的 prompt 仍然自然流畅
- [ ] 如有不确定的词，宁可替换（false positive 比被拦截好）

## 被引用方式

其他 skill 在 Higgsfield 模型适配段应写：

```
### Higgsfield Seedance 2.0
> ⚠️ 生成前必须过 `_shared/content-filter.md` 的词替换检查

[prompt 内容]
```
