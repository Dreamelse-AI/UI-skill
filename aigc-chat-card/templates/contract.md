# contract 合同模板

暖黄渐变背景，棕色边框。标题居中字间距 4px，底部双栏签署区。

## CSS

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

## HTML 骨架

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
