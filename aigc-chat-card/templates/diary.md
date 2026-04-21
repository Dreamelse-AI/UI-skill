# diary 日记模板

白到粉渐变背景。粉色强调。正文 15px 行高 1.9 沉浸阅读。内心独白用左侧粉色边线。

## CSS

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

## HTML 骨架

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
