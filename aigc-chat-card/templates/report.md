# report 报告模板

浅灰背景 #f8fafc，白色卡片带边框。靛蓝强调色。标题下 2px 粗线，核心数据大号居中。

## CSS

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

## HTML 骨架

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
    <span class="data-value">{值或tag}</span>
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
