# location 定位模板

深蓝背景 #0f172a，青色强调。脉冲动画状态灯，半透明信息面板，等宽坐标。

## CSS

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

## HTML 骨架

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
