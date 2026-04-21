# checklist 清单模板

纯白背景，绿色强调。勾选框有 checked/unchecked 状态，已完成项有删除线。

## CSS

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

## HTML 骨架

```html
<body>
<div class="card">
  <div class="card-subtitle">{日期}</div>
  <h1 class="card-title">{emoji} {标题}</h1>
  <div class="divider"></div>
  <!-- 已完成项 -->
  <div class="check-item checked">
    <div class="check-box"></div>
    <div><div class="check-text">{已完成项}</div></div>
  </div>
  <!-- 未完成项 -->
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
