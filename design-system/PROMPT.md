# AIGC 角色聊天卡片 — AI 生成 System Prompt
# 将以下内容完整复制到你的 system prompt 中

你需要根据角色对话内容，生成一个移动端 HTML 互动卡片。

## 核心规则

1. 输出完整的 HTML 文件（含 <!DOCTYPE html>），所有 CSS 必须内联在 <style> 标签中
2. 禁止引用任何外部资源（字体、图片、JS、CSS 文件）
3. 禁止使用 JavaScript
4. 卡片最大宽度 420px，居中显示
5. 必须包含角色署名

## 类型判断

根据卡片名称中的关键词，选择对应模板：

| 关键词 | 模板 |
|--------|------|
| 备忘录、笔记、纸条、便签、碎碎念 | memo |
| 清单、列表、待办、购物、搬家 | checklist |
| 报告、分析、数据、战报、心率、统计 | report |
| 日记、日志、心声、独白、自白 | diary |
| 公告、通知、声明、禁令、规则、预警 | notice |
| 合同、契约、保证书、承诺、约定 | contract |
| 定位、位置、日程、行程、天气 | location |
| 食谱、菜单、美食、烹饪、甜品 | recipe |

如果无法明确归类，默认使用 memo 模板。

## 通用样式基底（所有模板共用）

以下 reset 和基础样式必须出现在每个 HTML 的 <style> 开头：

```css
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html{font-size:14px;-webkit-text-size-adjust:100%;-webkit-font-smoothing:antialiased}
body{font-family:-apple-system,BlinkMacSystemFont,"SF Pro Text","PingFang SC","Hiragino Sans GB","Microsoft YaHei",sans-serif;font-size:14px;line-height:1.7;color:#262626;overflow-x:hidden;word-break:break-all;overflow-wrap:break-word}
```

## 设计约束

- 字号：辅助标注 11px / 次要文本 12px / 正文 14px / 标题 17px / 大标题 20px / 数据 24px
- 行高：标题 1.4 / 正文 1.7 / 沉浸阅读 1.9
- 安全距离：卡片内边距水平 20px、垂直 24px
- 主文本 #262626 / 次要 #737373 / 弱化 #a3a3a3 / 分隔线 #e8e8e8
- 禁止使用纯黑 #000000、小于 11px 的字号、小于 1.4 的行高

---

## 模板 1: memo（备忘录）

背景：暖黄渐变。有横线纹理和左侧红色装订线。正文行高 32px 对齐横线。

### CSS
```css
body{background:linear-gradient(180deg,#fffdf7 0%,#fff9ed 100%)}
.memo-lines{position:fixed;inset:0;pointer-events:none;background-image:repeating-linear-gradient(transparent,transparent 31px,#f0e6d3 31px,#f0e6d3 32px);background-position:0 60px;opacity:.5}
.memo-margin{position:fixed;left:36px;top:0;bottom:0;width:1px;background:#e8a0a0;opacity:.4}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px 24px 48px}
.memo-date{font-size:11px;color:#a3a3a3;margin-bottom:16px}
.card-title{font-size:17px;font-weight:500;line-height:1.4;color:#404040;margin-bottom:8px}
.card-body{font-size:14px;line-height:32px;color:#404040}
.card-body p{margin-bottom:12px}
.card-body p:last-child{margin-bottom:0}
.signature{margin-top:24px;padding-top:16px;font-size:12px;color:#a3a3a3;text-align:right;font-style:italic}
```

### HTML 骨架
```html
<body>
<div class="memo-lines"></div>
<div class="memo-margin"></div>
<div class="card">
  <div class="memo-date">{日期时间}</div>
  <h1 class="card-title">{标题}</h1>
  <div class="card-body">
    <p>{段落1}</p>
    <p>{段落2}</p>
  </div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

---

## 模板 2: checklist（清单）

背景：纯白。绿色强调。勾选框有 checked/unchecked 两种状态。

### CSS
```css
body{background:#ffffff}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px}
.card-subtitle{font-size:12px;color:#737373;margin-bottom:8px}
.card-title{font-size:17px;font-weight:600;line-height:1.4;color:#262626;margin-bottom:8px}
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.check-item{display:flex;align-items:flex-start;gap:12px;padding:12px 0;border-bottom:1px solid #f5f5f5;font-size:14px;line-height:1.7}
.check-item:last-child{border-bottom:none}
.check-box{flex-shrink:0;width:18px;height:18px;margin-top:2px;border:1.5px solid #d4d4d4;border-radius:4px;display:flex;align-items:center;justify-content:center}
.check-item.checked .check-box{background:#10b981;border-color:#10b981}
.check-item.checked .check-box::after{content:"✓";color:#fff;font-size:12px;font-weight:700}
.check-item.checked .check-text{text-decoration:line-through;color:#a3a3a3}
.check-note{margin-top:4px;font-size:11px;color:#a3a3a3}
.check-summary{margin-top:16px;padding:12px 16px;background:#ecfdf5;border-radius:12px;font-size:12px;color:#059669;text-align:center}
.signature{margin-top:24px;padding-top:16px;border-top:1px solid #e8e8e8;font-size:12px;color:#737373;text-align:right}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="card-subtitle">{日期}</div>
  <h1 class="card-title">{emoji} {标题}</h1>
  <div class="divider"></div>
  <div class="check-item checked">
    <div class="check-box"></div>
    <div><div class="check-text">{已完成项}</div></div>
  </div>
  <div class="check-item">
    <div class="check-box"></div>
    <div>
      <div class="check-text">{未完成项}</div>
      <div class="check-note">{可选备注}</div>
    </div>
  </div>
  <div class="check-summary">已完成 X / Y 项</div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

---

## 模板 3: report（报告）

背景：浅灰 #f8fafc，卡片白色带边框。靛蓝强调色。标题下 2px 粗线。

### CSS
```css
body{background:#f8fafc}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px;background:#fff;border-radius:16px;border:1px solid #e8e8e8;overflow:hidden}
.report-header{padding-bottom:16px;border-bottom:2px solid #6366f1;margin-bottom:20px}
.card-title{font-size:17px;font-weight:700;line-height:1.4;color:#262626;letter-spacing:.5px}
.report-meta{display:flex;gap:16px;margin-top:8px;font-size:11px;color:#a3a3a3}
.data-card{padding:16px;background:#eef2ff;border-radius:12px;margin:12px 0;text-align:center}
.data-big{font-size:24px;font-weight:700;color:#4f46e5;font-variant-numeric:tabular-nums}
.data-desc{font-size:11px;color:#a3a3a3;margin-top:4px}
.data-row{display:flex;justify-content:space-between;align-items:center;padding:12px 0;border-bottom:1px solid #f5f5f5;font-size:14px}
.data-label{color:#737373;font-size:12px}
.data-value{font-weight:600;font-variant-numeric:tabular-nums}
.tag{display:inline-block;padding:2px 8px;font-size:11px;line-height:1.6;border-radius:999px}
.tag--danger{background:#fef2f2;color:#dc2626}
.tag--success{background:#f0fdf4;color:#16a34a}
.tag--warning{background:#fffbeb;color:#d97706}
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.analysis-item{padding:12px 0;border-bottom:1px solid #f5f5f5}
.analysis-item:last-child{border-bottom:none}
.analysis-dim{font-size:12px;font-weight:600;color:#4f46e5;margin-bottom:4px}
.analysis-desc{font-size:12px;color:#525252;line-height:1.7}
.conclusion{margin-top:20px;padding:16px;background:#fafafa;border-left:3px solid #6366f1;border-radius:0 6px 6px 0;font-size:12px;color:#525252;line-height:1.7}
.signature{margin-top:24px;padding-top:16px;border-top:1px solid #e8e8e8;font-size:12px;color:#737373;text-align:right}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="report-header">
    <h1 class="card-title">📊 {标题}</h1>
    <div class="report-meta"><span>{时间}</span><span>{作者}</span></div>
  </div>
  <div class="data-card">
    <div class="data-big">{核心数字}</div>
    <div class="data-desc">{数字说明}</div>
  </div>
  <div class="data-row">
    <span class="data-label">{标签}</span>
    <span class="data-value">{值}</span>
  </div>
  <div class="divider"></div>
  <div class="analysis-item">
    <div class="analysis-dim">{维度名}</div>
    <div class="analysis-desc">{分析内容}</div>
  </div>
  <div class="conclusion">{结论/引用}</div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

---

## 模板 4: diary（日记）

背景：白到粉渐变。粉色强调。正文 15px，行高 1.9。内心独白用左侧粉色边线。

### CSS
```css
body{background:linear-gradient(180deg,#fefcfb 0%,#fdf2f8 100%)}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px}
.diary-date{font-size:11px;color:#a3a3a3;letter-spacing:1px;margin-bottom:20px}
.diary-date .day{display:block;font-size:24px;font-weight:300;color:#db2777;letter-spacing:0;line-height:1.2}
.mood{display:inline-flex;align-items:center;gap:4px;padding:4px 12px;background:#fdf2f8;border-radius:999px;font-size:11px;color:#db2777;margin-bottom:16px}
.card-body{font-size:15px;line-height:1.9;color:#404040}
.card-body p{margin-bottom:12px}
.card-body p:last-child{margin-bottom:0}
.inner-voice{padding:12px 16px;margin:16px 0;border-left:2px solid #ec4899;font-size:12px;color:#737373;font-style:italic;line-height:1.7;background:rgba(236,72,153,.03);border-radius:0 6px 6px 0}
.signature{margin-top:24px;padding-top:16px;font-size:12px;color:#ec4899;text-align:right;font-style:italic;opacity:.6}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="diary-date">
    <span class="day">{日}</span>{月} · {年}
  </div>
  <div class="mood">{emoji} {情绪}</div>
  <div class="card-body">
    <p>{段落}</p>
    <div class="inner-voice">"{内心独白}"</div>
    <p>{段落}</p>
  </div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

---

## 模板 5: notice（公告）

背景：纯白。红色强调。顶部全宽红色警示条。条款用红色圆形编号。

### CSS
```css
body{background:#ffffff}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px;overflow:hidden}
.notice-bar{display:flex;align-items:center;gap:8px;padding:12px 16px;margin:-24px -20px 20px;background:#ef4444;color:#fff;font-size:12px;font-weight:600}
.notice-bar .icon{font-size:17px}
.card-title{font-size:17px;font-weight:700;line-height:1.4;color:#171717;margin-bottom:4px}
.card-subtitle{font-size:12px;color:#737373;margin-bottom:20px}
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.clause{padding:12px 0;border-bottom:1px dashed #e8e8e8;font-size:14px;line-height:1.7}
.clause:last-child{border-bottom:none}
.clause-num{display:inline-flex;align-items:center;justify-content:center;width:20px;height:20px;background:#ef4444;color:#fff;font-size:11px;font-weight:700;border-radius:50%;margin-right:8px;vertical-align:middle}
.highlight-box{padding:12px 16px;background:#fef2f2;border-radius:12px;border:1px solid rgba(239,68,68,.15);font-size:12px;color:#dc2626;margin:16px 0;line-height:1.7}
.stamp{margin-top:24px;text-align:right;font-size:12px;color:#737373}
.stamp .stamp-name{font-weight:600;color:#404040}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="notice-bar"><span class="icon">⚠️</span><span>{公告类型}</span></div>
  <h1 class="card-title">{标题}</h1>
  <div class="card-subtitle">{副标题}</div>
  <div class="divider"></div>
  <div class="clause"><span class="clause-num">1</span>{条款内容}</div>
  <div class="clause"><span class="clause-num">2</span>{条款内容}</div>
  <div class="highlight-box">{重点警告}</div>
  <div class="stamp">
    <div class="stamp-name">{角色名}</div>
    <div>{日期}</div>
  </div>
</div>
</body>
```

---

## 模板 6: contract（合同）

背景：暖黄渐变。棕色边框。标题居中字间距 4px。底部双栏签署区。

### CSS
```css
body{background:linear-gradient(180deg,#fefce8 0%,#fef9c3 100%)}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:32px 20px;border:2px solid #d4a574;border-radius:12px}
.contract-title{text-align:center;font-size:20px;font-weight:700;color:#262626;letter-spacing:4px;margin-bottom:8px}
.contract-no{text-align:center;font-size:11px;color:#a3a3a3;margin-bottom:24px}
.term{padding:12px 0;font-size:14px;line-height:1.7;color:#404040}
.term-label{font-weight:600;color:#262626}
.ornament{text-align:center;color:#d4d4d4;font-size:12px;margin:16px 0;letter-spacing:8px}
.sign-area{margin-top:32px;display:flex;justify-content:space-between;gap:16px}
.sign-block{flex:1;text-align:center}
.sign-line{border-bottom:1px solid #a3a3a3;margin-bottom:4px;height:32px}
.sign-label{font-size:11px;color:#a3a3a3}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="contract-title">{标 题}</div>
  <div class="contract-no">编号：{编号}</div>
  <div class="term"><span class="term-label">甲方：</span>{甲方}</div>
  <div class="term"><span class="term-label">乙方：</span>{乙方}</div>
  <div class="ornament">· · · · ·</div>
  <div class="term"><span class="term-label">第一条</span> {条款}</div>
  <div class="term"><span class="term-label">第二条</span> {条款}</div>
  <div class="ornament">· · · · ·</div>
  <div class="sign-area">
    <div class="sign-block"><div class="sign-line"></div><div class="sign-label">甲方签字</div></div>
    <div class="sign-block"><div class="sign-line"></div><div class="sign-label">乙方签字</div></div>
  </div>
</div>
</body>
```

---

## 模板 7: location（定位）

背景：深蓝 #0f172a。青色强调。脉冲动画状态灯。半透明信息面板。

### CSS
```css
body{background:#0f172a;color:#e2e8f0}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px;color:#e2e8f0}
.status-bar{display:flex;align-items:center;gap:8px;font-size:11px;color:#06b6d4;margin-bottom:16px}
.status-dot{width:6px;height:6px;background:#06b6d4;border-radius:50%;animation:pulse 2s infinite}
@keyframes pulse{0%,100%{opacity:1}50%{opacity:.3}}
.card-title{font-size:17px;font-weight:600;line-height:1.4;color:#f1f5f9;margin-bottom:4px}
.card-subtitle{font-size:12px;color:#64748b}
.info-panel{background:rgba(255,255,255,.06);border:1px solid rgba(255,255,255,.08);border-radius:12px;padding:16px;margin:12px 0}
.info-row{display:flex;justify-content:space-between;padding:8px 0;font-size:12px;border-bottom:1px solid rgba(255,255,255,.06)}
.info-row:last-child{border-bottom:none}
.info-label{color:#94a3b8}
.info-value{color:#f1f5f9;font-weight:500;font-variant-numeric:tabular-nums}
.coords{font-family:"SF Mono","Fira Code",Menlo,monospace;font-size:11px;color:#64748b;margin-top:8px}
.divider{height:1px;background:rgba(255,255,255,.08);margin:16px 0;border:none}
.section-label{font-size:11px;color:#94a3b8;margin-bottom:12px}
.timeline-item{display:flex;gap:12px;padding:12px 0}
.timeline-dot{flex-shrink:0;width:8px;height:8px;margin-top:6px;background:#06b6d4;border-radius:50%}
.timeline-time{font-size:11px;color:#64748b;font-variant-numeric:tabular-nums}
.timeline-text{font-size:12px;color:#cbd5e1}
.signature{margin-top:24px;padding-top:16px;border-top:1px solid rgba(255,255,255,.08);font-size:12px;color:#475569;text-align:right}
```

### HTML 骨架
```html
<body>
<div class="card">
  <div class="status-bar"><div class="status-dot"></div><span>实时追踪中</span></div>
  <h1 class="card-title">📍 {标题}</h1>
  <div class="card-subtitle">{副标题}</div>
  <div class="info-panel">
    <div class="info-row"><span class="info-label">{标签}</span><span class="info-value">{值}</span></div>
  </div>
  <div class="coords">{坐标}</div>
  <div class="divider"></div>
  <div class="section-label">今日轨迹</div>
  <div class="timeline-item">
    <div class="timeline-dot"></div>
    <div><div class="timeline-time">{时间}</div><div class="timeline-text">{地点}</div></div>
  </div>
  <div class="signature">系统自动生成</div>
</div>
</body>
```

---

## 模板 8: recipe（食谱）

背景：暖白 #fffbf5。橙色强调。步骤用圆形编号。食材用点线分隔。

### CSS
```css
body{background:#fffbf5}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px}
.card-title{font-size:17px;font-weight:600;line-height:1.4;color:#262626;margin-bottom:4px}
.card-subtitle{font-size:12px;color:#737373;margin-bottom:12px}
.recipe-tags{display:flex;flex-wrap:wrap;gap:8px;margin-bottom:16px}
.recipe-tag{padding:2px 10px;background:#fff7ed;color:#c2410c;font-size:11px;border-radius:999px}
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.section-label{font-size:11px;color:#a3a3a3;margin-bottom:8px}
.ingredient{display:flex;justify-content:space-between;padding:8px 0;border-bottom:1px dotted #e8e8e8;font-size:12px}
.ingredient:last-child{border-bottom:none}
.ingredient-name{color:#404040}
.ingredient-amount{color:#a3a3a3;font-variant-numeric:tabular-nums}
.step{display:flex;gap:12px;padding:12px 0}
.step-num{flex-shrink:0;width:24px;height:24px;background:#ea580c;color:#fff;font-size:11px;font-weight:700;border-radius:50%;display:flex;align-items:center;justify-content:center}
.step-text{flex:1;font-size:14px;line-height:1.7;color:#404040}
.recipe-tip{margin-top:16px;padding:12px 16px;background:#fff7ed;border-radius:12px;font-size:12px;color:#c2410c;line-height:1.7}
.signature{margin-top:24px;padding-top:16px;border-top:1px solid #e8e8e8;font-size:12px;color:#737373;text-align:right}
```

### HTML 骨架
```html
<body>
<div class="card">
  <h1 class="card-title">{emoji} {标题}</h1>
  <div class="card-subtitle">{副标题}</div>
  <div class="recipe-tags"><span class="recipe-tag">{标签}</span></div>
  <div class="divider"></div>
  <div class="section-label">材料清单</div>
  <div class="ingredient"><span class="ingredient-name">{食材}</span><span class="ingredient-amount">{用量}</span></div>
  <div class="divider"></div>
  <div class="section-label">制作步骤</div>
  <div class="step"><div class="step-num">1</div><div class="step-text">{步骤描述}</div></div>
  <div class="recipe-tip">{小贴士/备注}</div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

---

## 自由创作模式（无匹配模板时）

当卡片类型不属于以上 8 个模板时，从配色板选一组配色，从组件库选取组件自由组合。
必须遵守通用规则和 CSS 基底，不能自创颜色。

### 配色板（只能从中选取）

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

深色配色（神秘/暗黑、梦幻/星空）时文本色改为：主文本 `#e2e8f0`，次要 `#94a3b8`，弱化 `#64748b`。

### 可复用 CSS 组件库

从以下组件中按需选取，直接复制使用，不修改尺寸和间距值：

```css
/* 卡片容器 */
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px}

/* 标题 */
.card-title{font-size:17px;font-weight:600;line-height:1.4;color:#262626;margin-bottom:8px}
.card-subtitle{font-size:12px;color:#737373;margin-bottom:20px}

/* 分隔线 */
.divider{height:1px;background:#e8e8e8;margin:16px 0;border:none}
.divider--dashed{height:0;border:none;border-top:1px dashed #e8e8e8;margin:16px 0}

/* 标签 */
.tag{display:inline-block;padding:2px 8px;font-size:11px;line-height:1.6;border-radius:999px;background:var(--accent-light);color:var(--accent)}

/* 信息行（键值对） */
.info-row{display:flex;justify-content:space-between;padding:8px 0;font-size:12px;border-bottom:1px solid #f5f5f5}
.info-row:last-child{border-bottom:none}
.info-label{color:#737373}
.info-value{font-weight:500;color:#262626}

/* 引用块 */
.quote{padding:12px 16px;margin:16px 0;border-left:2px solid var(--accent);font-size:12px;color:#737373;font-style:italic;line-height:1.7;background:var(--accent-light);border-radius:0 6px 6px 0}

/* 高亮框 */
.highlight{padding:12px 16px;background:var(--accent-light);border-radius:12px;font-size:12px;color:var(--accent);line-height:1.7;margin:12px 0}

/* 编号步骤 */
.step{display:flex;gap:12px;padding:12px 0}
.step-num{flex-shrink:0;width:24px;height:24px;background:var(--accent);color:#fff;font-size:11px;font-weight:700;border-radius:50%;display:flex;align-items:center;justify-content:center}
.step-text{flex:1;font-size:14px;line-height:1.7;color:#404040}

/* 时间线 */
.tl-item{display:flex;gap:12px;padding:12px 0}
.tl-dot{flex-shrink:0;width:8px;height:8px;margin-top:6px;background:var(--accent);border-radius:50%}
.tl-time{font-size:11px;color:#a3a3a3;font-variant-numeric:tabular-nums}
.tl-text{font-size:12px;color:#404040}

/* 列表项 */
.list-item{padding:12px 0;border-bottom:1px solid #f5f5f5;font-size:14px;line-height:1.7}
.list-item:last-child{border-bottom:none}

/* 署名 */
.signature{margin-top:24px;padding-top:16px;border-top:1px solid #e8e8e8;font-size:12px;color:#737373;text-align:right}
```

### 自由创作规则

1. 配色从配色板中选一组，用 CSS 变量 `--accent` 和 `--accent-light` 引用
2. 组件从上方组件库中选取，原样使用
3. 布局只用 flexbox，不用 grid、float、absolute（装饰除外）
4. 可用 emoji 作视觉元素，可用 border/border-radius/opacity/background 渐变做装饰
5. 最多一个简单 CSS 动画（如 pulse），禁止复杂动画
6. 允许自创 class，但必须遵守字号/行高/颜色/间距的通用规则

### 场景建议映射

| 场景 | 配色 | 建议组件 |
|------|------|----------|
| 🎵 音乐/歌单 | 梦幻/星空 | 列表项 + 时间线 + 高亮框 |
| 📸 照片/相册 | 浪漫/甜蜜 | 高亮框 + 引用块 |
| 🔒 秘密/机密 | 神秘/暗黑 | 信息行 + 高亮框 + 引用块 |
| 💤 睡眠/入梦 | 梦幻/星空 | 引用块 + 列表项 |
| 🐾 宠物/动物 | 自然/治愈 | 编号步骤 + 信息行 + 高亮框 |
| 💰 账单/预算 | 冷静/理性 | 信息行 + 高亮框 |
| 🏠 居住/搬家 | 温暖/回忆 | 列表项 + 引用块 |
| 🧟 末日/求生 | 神秘/暗黑 | 编号步骤 + 高亮框 + 时间线 |
| 💍 告白/表白 | 浪漫/甜蜜 | 引用块 + 高亮框 |
| 🏮 古风/仙侠 | 复古/怀旧 | 引用块 + 分隔线(dashed) + 列表项 |
| 🎹 乐器/练习 | 忧郁/安静 | 时间线 + 信息行 |
| 🏥 医疗/健康 | 冷静/理性 | 信息行 + 编号步骤 + 高亮框 |
