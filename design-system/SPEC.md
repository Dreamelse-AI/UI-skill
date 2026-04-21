# AIGC 角色聊天卡片 — HTML 生成规范 (Prompt Reference)

## 一、通用规则（所有模板必须遵守）

### 1.1 文档结构
```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <style>/* 内联所有样式，不依赖外部资源 */</style>
</head>
<body class="tpl-{类型}">
  <div class="card">
    <!-- 内容区 -->
  </div>
</body>
</html>
```

### 1.2 移动端字号规则
| 用途 | 字号 | 行高 | 说明 |
|------|------|------|------|
| 辅助标注 | 11px | 1.4 | 时间戳、编号、极小标注 |
| 次要文本 | 12px | 1.4 | 副标题、备注、标签 |
| 正文 | 14px | 1.7 | 默认阅读字号 |
| 强调正文 | 15px | 1.7 | 日记等需要沉浸阅读的场景 |
| 标题 | 17px | 1.4 | 卡片主标题 |
| 大标题 | 20px | 1.4 | 需要视觉冲击的标题 |
| 数据展示 | 24px | 1.2 | 报告中的核心数字 |

### 1.3 安全距离
- 卡片内边距：水平 20px，垂直 24px
- 段落间距：12px
- 模块间距：16-24px
- 列表项间距：12px（含分隔线）

### 1.4 颜色使用
- 主文本：#262626（不要用纯黑 #000）
- 次要文本：#737373
- 弱化文本：#a3a3a3
- 分隔线：#e8e8e8
- 背景：#ffffff 或模板指定的渐变色
- 每个模板有专属强调色，不要混用

### 1.5 字体栈
```css
font-family: -apple-system, BlinkMacSystemFont, "SF Pro Text",
  "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", sans-serif;
```

### 1.6 禁止事项
- ❌ 不要使用外部字体（Google Fonts 等）
- ❌ 不要使用外部图片 URL
- ❌ 不要使用 JavaScript
- ❌ 不要使用 position: fixed
- ❌ 不要使用超过 420px 的固定宽度
- ❌ 不要使用纯黑 #000000 作为文本色
- ❌ 不要使用小于 11px 的字号
- ❌ 不要使用小于 1.4 的行高
- ❌ 不要让文本直接贴边（必须有安全距离）

---

## 二、模板类型与风格定义

### 模板 1: 📝 备忘录 (tpl-memo)
**适用关键词**: 备忘录、笔记、纸条、便签、碎碎念
**覆盖占比**: ~20%

**视觉风格**: 手写感、纸张质感、温暖私密
- 背景：暖黄渐变 `#fffdf7 → #fff9ed`
- 强调色：`#f5a623`
- 有横线纹理（模拟笔记本纸张）
- 左侧红色装订线
- 内容区左缩进 48px（避开装订线）
- 正文行高固定 32px（对齐横线）

**HTML 结构**:
```html
<body class="tpl-memo">
  <div class="memo-lines"></div>   <!-- 横线纹理 -->
  <div class="memo-margin"></div>  <!-- 装订线 -->
  <div class="card">
    <div class="memo-date">日期</div>
    <h1 class="card-title">标题</h1>
    <div class="card-body"><p>正文段落...</p></div>
    <div class="signature">—— 角色名</div>
  </div>
</body>
```

---

### 模板 2: ✅ 清单 (tpl-checklist)
**适用关键词**: 清单、列表、待办、购物单、搬家清单
**覆盖占比**: ~13%

**视觉风格**: 结构化、勾选交互感、干净利落
- 背景：纯白
- 强调色：`#10b981`（绿色，完成感）
- 每项有勾选框（checked/unchecked 两种状态）
- 已完成项有删除线 + 灰色
- 底部可选统计条

**HTML 结构**:
```html
<body class="tpl-checklist">
  <div class="card">
    <div class="card-subtitle">日期</div>
    <h1 class="card-title">📦 标题</h1>
    <div class="divider"></div>
    <div class="check-item checked">
      <div class="check-box"></div>
      <div><div class="check-text">已完成项</div></div>
    </div>
    <div class="check-item">
      <div class="check-box"></div>
      <div>
        <div class="check-text">未完成项</div>
        <div class="check-note">可选备注</div>
      </div>
    </div>
    <div class="check-summary">已完成 X / Y 项</div>
    <div class="signature">—— 角色名</div>
  </div>
</body>
```

---

### 模板 3: 📊 报告 (tpl-report)
**适用关键词**: 报告、分析、数据、战报、心率、统计
**覆盖占比**: ~5%

**视觉风格**: 数据感、专业冷静、结构清晰
- 背景：`#f8fafc`，卡片白色带边框
- 强调色：`#6366f1`（靛蓝色）
- 标题下方有 2px 强调色粗线
- 核心数据用大号字居中展示
- 分析条目有维度标签 + 描述
- 结论区用左侧色条引用样式

**HTML 结构**:
```html
<body class="tpl-report">
  <div class="card">
    <div class="report-header">
      <h1 class="card-title">📊 标题</h1>
      <div class="report-meta"><span>时间</span><span>作者</span></div>
    </div>
    <div class="data-card">
      <div class="data-big">核心数字</div>
      <div class="data-desc">数字说明</div>
    </div>
    <div class="data-row">
      <span class="data-label">标签</span>
      <span class="data-value">值</span>
    </div>
    <div class="analysis-item">
      <div class="analysis-dim">维度名</div>
      <div class="analysis-desc">分析描述</div>
    </div>
    <div class="conclusion">结论引用</div>
    <div class="signature">—— 角色名</div>
  </div>
</body>
```

---

### 模板 4: 📔 日记 (tpl-diary)
**适用关键词**: 日记、日志、心声、独白、自白
**覆盖占比**: ~4%

**视觉风格**: 私密感、情绪化、柔和色调
- 背景：白到粉渐变 `#fefcfb → #fdf2f8`
- 强调色：`#ec4899`（粉色）
- 日期大写展示（日期数字突出）
- 正文字号 15px，行高 1.9（沉浸阅读）
- 内心独白用左侧粉色边线引用
- 可选情绪标签

**HTML 结构**:
```html
<body class="tpl-diary">
  <div class="card">
    <div class="diary-date">
      <span class="day">18</span>四月 · 2026
    </div>
    <div class="mood">😔 情绪</div>
    <div class="card-body">
      <p>正文...</p>
      <div class="inner-voice">"内心独白"</div>
    </div>
    <div class="signature">—— 角色名</div>
  </div>
</body>
```

---

### 模板 5: ⚠️ 公告 (tpl-notice)
**适用关键词**: 公告、通知、声明、禁令、规则、预警
**覆盖占比**: ~3%

**视觉风格**: 正式感、醒目、层级分明
- 背景：纯白
- 强调色：`#ef4444`（红色，警示感）
- 顶部全宽红色警示条
- 条款用红色圆形编号
- 重点内容用红色浅底高亮框
- 底部签署区

**HTML 结构**:
```html
<body class="tpl-notice">
  <div class="card">
    <div class="notice-bar"><span class="icon">⚠️</span><span>公告类型</span></div>
    <h1 class="card-title">标题</h1>
    <div class="card-subtitle">副标题</div>
    <div class="divider"></div>
    <div class="clause"><span class="clause-num">1</span>条款内容</div>
    <div class="highlight-box">重点警告内容</div>
    <div class="stamp">
      <div class="stamp-name">角色名</div>
      <div>日期</div>
    </div>
  </div>
</body>
```

---

### 模板 6: 📑 合同 (tpl-contract)
**适用关键词**: 合同、契约、保证书、承诺、约定
**覆盖占比**: ~3%

**视觉风格**: 正式文书感、复古纸张、仪式感
- 背景：暖黄渐变 `#fefce8 → #fef9c3`
- 强调色：`#92400e`（棕色）
- 卡片有棕色边框
- 标题居中、字间距 4px
- 条款有加粗标签
- 底部双栏签署区（甲方/乙方）
- 装饰分隔符 `· · · · ·`

---

### 模板 7: 📍 定位 (tpl-location)
**适用关键词**: 定位、位置、日程、行程、天气
**覆盖占比**: ~4%

**视觉风格**: 工具感、实时数据、深色科技风
- 背景：深蓝 `#0f172a`
- 强调色：`#06b6d4`（青色）
- 状态指示灯（脉冲动画）
- 信息面板用半透明卡片
- 数据行左右对齐，等宽数字
- 坐标用等宽字体
- 时间线用圆点 + 竖线

---

### 模板 8: 🍳 食谱 (tpl-recipe)
**适用关键词**: 食谱、菜单、美食、烹饪、甜品
**覆盖占比**: ~2%

**视觉风格**: 温馨、食欲感、暖色调
- 背景：暖白 `#fffbf5`
- 强调色：`#ea580c`（橙色）
- 标签用圆角胶囊
- 食材列表用点线分隔
- 步骤用橙色圆形编号
- 底部小贴士用暖色浅底框

---

## 三、AI 生成 Prompt 模板

当 AI 需要生成 HTML 卡片时，在 system prompt 中加入以下指令：

```
你需要生成一个角色聊天互动卡片的 HTML。请严格遵循以下规范：

1. 根据内容类型选择对应模板：
   - 备忘录/笔记/纸条 → tpl-memo
   - 清单/列表/待办 → tpl-checklist
   - 报告/分析/数据 → tpl-report
   - 日记/日志/心声 → tpl-diary
   - 公告/通知/禁令 → tpl-notice
   - 合同/保证书/约定 → tpl-contract
   - 定位/位置/日程 → tpl-location
   - 食谱/菜单/美食 → tpl-recipe

2. 所有样式必须内联在 <style> 标签中，不引用任何外部资源。

3. 字号规则：辅助标注 11px，次要文本 12px，正文 14px，标题 17-20px。
   行高：正文 1.7，标题 1.4。绝不使用小于 11px 的字号。

4. 安全距离：卡片内边距水平 20px、垂直 24px。文本不得贴边。

5. 颜色：主文本 #262626，次要 #737373，弱化 #a3a3a3。禁用纯黑 #000。

6. 卡片最大宽度 420px，居中显示。

7. 必须包含角色署名区（.signature），格式为 "—— 角色名"。

8. 禁止使用 JavaScript、外部图片、外部字体、position:fixed。

9. 每个模板有固定的背景色、强调色和布局结构，不要自由发挥配色。
```

---

## 四、文件结构

```
aigc-html-design-system/
├── base.css                    # 通用设计 Token + Reset + 基础组件
├── templates/
│   ├── memo.css               # 备忘录模板
│   ├── checklist.css          # 清单模板
│   ├── report.css             # 报告模板
│   ├── diary.css              # 日记模板
│   ├── notice.css             # 公告模板
│   ├── contract.css           # 合同模板
│   ├── location.css           # 定位模板
│   └── recipe.css             # 食谱模板
├── examples/
│   ├── memo.html              # 备忘录示例
│   ├── checklist.html         # 清单示例
│   ├── report.html            # 报告示例
│   ├── diary.html             # 日记示例
│   ├── notice.html            # 公告示例
│   ├── contract.html          # 合同示例
│   ├── location.html          # 定位示例
│   └── recipe.html            # 食谱示例
├── index.html                 # 模板总览页
└── SPEC.md                    # 本规范文档
```
