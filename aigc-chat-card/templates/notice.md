# notice 公告模板

纯白背景，红色强调。顶部全宽红色警示条，条款用红色圆形编号。

## CSS

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

## HTML 骨架

```html
<body>
<div class="card">
  <div class="notice-bar"><span class="icon">⚠️</span><span>{公告类型}</span></div>
  <h1 class="card-title">{标题}</h1>
  <div class="card-subtitle">{副标题}</div>
  <div class="divider"></div>
  <div class="clause"><span class="clause-num">1</span>{条款}</div>
  <div class="clause"><span class="clause-num">2</span>{条款}</div>
  <div class="highlight-box">{重点警告}</div>
  <div class="stamp">
    <div class="stamp-name">{角色名}</div>
    <div>{日期}</div>
  </div>
</div>
</body>
```
