# recipe 食谱模板

暖白背景 #fffbf5，橙色强调。步骤用圆形编号，食材用点线分隔。

## CSS

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

## HTML 骨架

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
  <div class="step"><div class="step-num">1</div><div class="step-text">{步骤}</div></div>
  <div class="recipe-tip">{小贴士}</div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```
