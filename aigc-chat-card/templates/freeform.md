# freeform 自由创作模式

当卡片类型不属于 8 个预设模板时，使用此指南自由组合。
必须遵守 SKILL.md 中的通用规则和 CSS 基底，在此基础上自由发挥。

## 1. 配色板（只能从中选取）

根据卡片情绪/场景选择一组配色，不要自创颜色：

| 情绪/场景 | 背景 | 强调色 | 强调浅底 |
|-----------|------|--------|----------|
| 温暖/回忆 | `#fffdf7` | `#f5a623` | `#fef9ee` |
| 浪漫/甜蜜 | `#fefcfb` | `#ec4899` | `#fdf2f8` |
| 冷静/理性 | `#f8fafc` | `#6366f1` | `#eef2ff` |
| 活力/趣味 | `#fffbf5` | `#ea580c` | `#fff7ed` |
| 自然/治愈 | `#f0fdf4` | `#10b981` | `#ecfdf5` |
| 神秘/暗黑 | `#0f172a` | `#06b6d4` | `rgba(255,255,255,.06)` |
| 正式/严肃 | `#ffffff` | `#ef4444` | `#fef2f2` |
| 复古/怀旧 | `#fefce8` | `#92400e` | `#fef3c7` |
| 忧郁/安静 | `#f8fafc` | `#64748b` | `#f1f5f9` |
| 梦幻/星空 | `#0c0a1d` | `#a78bfa` | `rgba(167,139,250,.1)` |

## 2. 可复用 CSS 组件

从以下组件中按需选取，直接复制使用，不要修改尺寸和间距值：

### 卡片容器
```css
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px}
```

### 标题
```css
.card-title{font-size:17px;font-weight:600;line-height:1.4;color:#262626;margin-bottom:8px}
.card-subtitle{font-size:12px;color:#737373;margin-bottom:20px}
```

### 分隔线
```css
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.divider--dashed{height:0;border:none;border-top:1px dashed #e8e8e8;margin:16px 0}
```

### 标签
```css
.tag{display:inline-block;padding:2px 8px;font-size:11px;line-height:1.6;border-radius:999px;background:var(--accent-light);color:var(--accent)}
```

### 信息行（键值对）
```css
.info-row{display:flex;justify-content:space-between;padding:8px 0;font-size:12px;border-bottom:1px solid #f5f5f5}
.info-row:last-child{border-bottom:none}
.info-label{color:#737373}
.info-value{font-weight:500;color:#262626}
```

### 引用块
```css
.quote{padding:12px 16px;margin:16px 0;border-left:2px solid var(--accent);font-size:12px;color:#737373;font-style:italic;line-height:1.7;background:var(--accent-light);border-radius:0 6px 6px 0}
```

### 高亮框
```css
.highlight{padding:12px 16px;background:var(--accent-light);border-radius:12px;font-size:12px;color:var(--accent);line-height:1.7;margin:12px 0}
```

### 编号步骤
```css
.step{display:flex;gap:12px;padding:12px 0}
.step-num{flex-shrink:0;width:24px;height:24px;background:var(--accent);color:#fff;font-size:11px;font-weight:700;border-radius:50%;display:flex;align-items:center;justify-content:center}
.step-text{flex:1;font-size:14px;line-height:1.7;color:#404040}
```

### 时间线
```css
.tl-item{display:flex;gap:12px;padding:12px 0}
.tl-dot{flex-shrink:0;width:8px;height:8px;margin-top:6px;background:var(--accent);border-radius:50%}
.tl-time{font-size:11px;color:#a3a3a3;font-variant-numeric:tabular-nums}
.tl-text{font-size:12px;color:#404040}
```

### 列表项
```css
.list-item{padding:12px 0;border-bottom:1px solid #f5f5f5;font-size:14px;line-height:1.7}
.list-item:last-child{border-bottom:none}
```

### 署名
```css
.signature{margin-top:24px;padding-top:16px;border-top:1px solid #e8e8e8;font-size:12px;color:#737373;text-align:right}
```

## 3. 自由创作规则

1. **配色**：从配色板中选一组，用 CSS 变量 `--accent` 和 `--accent-light` 引用
2. **组件**：从上方组件库中选取需要的组件，原样使用
3. **布局**：只能用 flexbox，不能用 grid、float、absolute 定位（署名等装饰除外）
4. **装饰**：可以用 emoji 作为视觉元素，可以用 `border`、`border-radius`、`opacity`、`background` 渐变做装饰
5. **动画**：最多一个简单 CSS 动画（如 pulse），禁止复杂动画
6. **自创 class**：允许，但必须遵守字号/行高/颜色/间距的通用规则
7. **深色模式**：如果选了深色配色（神秘/暗黑、梦幻/星空），文本色改为 `#e2e8f0`，次要 `#94a3b8`，弱化 `#64748b`

## 4. 示例场景

以下是一些可能出现的非标准类型，以及建议的组合方式：

| 场景 | 配色 | 建议组件 |
|------|------|----------|
| 🎵 音乐/歌单/播放器 | 梦幻/星空 | 列表项 + 时间线 + 高亮框 |
| 📸 照片/相册/自拍 | 浪漫/甜蜜 | 高亮框 + 引用块 |
| 🔒 秘密/机密/暗号 | 神秘/暗黑 | 信息行 + 高亮框 + 引用块 |
| 💤 睡眠/入梦/晚安 | 梦幻/星空 | 引用块 + 列表项 |
| 🐾 宠物/动物 | 自然/治愈 | 编号步骤 + 信息行 + 高亮框 |
| 💰 账单/预算 | 冷静/理性 | 信息行 + 高亮框 |
| 🏠 居住/搬家/房间 | 温暖/回忆 | 列表项 + 引用块 |
| 🧟 末日/求生 | 神秘/暗黑 | 编号步骤 + 高亮框 + 时间线 |
| 💍 告白/表白 | 浪漫/甜蜜 | 引用块 + 高亮框 |
| 🏮 古风/仙侠 | 复古/怀旧 | 引用块 + 分隔线(dashed) + 列表项 |
| 🎹 乐器/练习 | 忧郁/安静 | 时间线 + 信息行 |
| 🏥 医疗/健康 | 冷静/理性 | 信息行 + 编号步骤 + 高亮框 |
