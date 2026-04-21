# memo 备忘录模板

暖黄纸张质感，横线纹理 + 左侧红色装订线。正文行高 32px 对齐横线。

## CSS

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

## HTML 骨架

```html
<body>
<div class="memo-lines"></div>
<div class="memo-margin"></div>
<div class="card">
  <div class="memo-date">{日期时间}</div>
  <h1 class="card-title">{标题}</h1>
  <div class="card-body">
    <p>{段落}</p>
  </div>
  <div class="signature">—— {角色名}</div>
</div>
</body>
```

## 示例

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html{font-size:14px;-webkit-text-size-adjust:100%;-webkit-font-smoothing:antialiased}
body{font-family:-apple-system,BlinkMacSystemFont,"SF Pro Text","PingFang SC","Hiragino Sans GB","Microsoft YaHei",sans-serif;font-size:14px;line-height:1.7;color:#262626;background:linear-gradient(180deg,#fffdf7 0%,#fff9ed 100%);overflow-x:hidden;word-break:break-all;overflow-wrap:break-word}
.memo-lines{position:fixed;inset:0;pointer-events:none;background-image:repeating-linear-gradient(transparent,transparent 31px,#f0e6d3 31px,#f0e6d3 32px);background-position:0 60px;opacity:.5}
.memo-margin{position:fixed;left:36px;top:0;bottom:0;width:1px;background:#e8a0a0;opacity:.4}
.card{position:relative;width:100%;max-width:420px;margin:0 auto;padding:24px 20px 24px 48px}
.memo-date{font-size:11px;color:#a3a3a3;margin-bottom:16px}
.card-title{font-size:17px;font-weight:500;line-height:1.4;color:#404040;margin-bottom:8px}
.card-body{font-size:14px;line-height:32px;color:#404040}
.card-body p{margin-bottom:12px}
.card-body p:last-child{margin-bottom:0}
.signature{margin-top:24px;padding-top:16px;font-size:12px;color:#a3a3a3;text-align:right;font-style:italic}
</style>
</head>
<body>
<div class="memo-lines"></div>
<div class="memo-margin"></div>
<div class="card">
  <div class="memo-date">2026年4月18日 · 周五 · 23:47</div>
  <h1 class="card-title">必须要记得的事</h1>
  <div class="card-body">
    <p>刚才悄悄在备忘录里写的……</p>
    <p>1. 明天早上要比他先起来，偷偷把早餐做好。</p>
    <p>2. 不可以再因为害怕就躲进衣柜里了。</p>
    <p>3. 如果他问"你还好吗"，这次要诚实地回答。</p>
  </div>
  <div class="signature">—— 陆夏</div>
</div>
</body>
</html>
```
