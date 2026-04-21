---
name: aigc-chat-card
description: >-
  生成 AIGC 角色聊天互动卡片的 HTML。根据卡片类型（备忘录、清单、报告、
  日记、公告、合同、定位、食谱）选择对应模板，输出符合移动端规范的自包含
  HTML 文件。当需要生成角色聊天卡片、互动卡片、HTML 卡片，或涉及
  role_chat_html 时使用此 skill。
---

# AIGC 角色聊天卡片生成

根据角色对话场景生成移动端 HTML 互动卡片。所有卡片遵循统一设计规范，按内容类型套用对应模板。

## 类型判断

根据卡片名称关键词选择模板：

| 模板 | 关键词 | 强调色 |
|------|--------|--------|
| memo | 备忘录、笔记、纸条、便签、碎碎念 | #f5a623 |
| checklist | 清单、列表、待办、购物、搬家 | #10b981 |
| report | 报告、分析、数据、战报、心率、统计 | #6366f1 |
| diary | 日记、日志、心声、独白、自白 | #ec4899 |
| notice | 公告、通知、声明、禁令、规则、预警 | #ef4444 |
| contract | 合同、契约、保证书、承诺、约定 | #92400e |
| location | 定位、位置、日程、行程、天气 | #06b6d4 |
| recipe | 食谱、菜单、美食、烹饪、甜品 | #ea580c |

如果能明确归类，使用对应模板。如果无法归类，进入自由创作模式（见下方）。

## 通用规则

1. 输出完整 HTML（含 `<!DOCTYPE html>`），CSS 内联在 `<style>` 中
2. 禁止：外部资源（字体/图片/CSS）、JavaScript、`position:fixed`
3. 卡片 `max-width:420px` 居中，内边距水平 20px 垂直 24px
4. 字号：标注 11px / 次要 12px / 正文 14px / 标题 17px / 大标题 20px / 数据 24px
5. 行高：标题 1.4 / 正文 1.7 / 沉浸阅读 1.9。禁止 <1.4
6. 颜色：主文本 #262626 / 次要 #737373 / 弱化 #a3a3a3 / 分隔线 #e8e8e8。禁止纯黑 #000
7. 必须包含角色署名 `<div class="signature">—— {角色名}</div>`

## 通用 CSS 基底

每个 HTML 的 `<style>` 必须以此开头：

```css
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box;-webkit-tap-highlight-color:transparent}
html{font-size:14px;-webkit-text-size-adjust:100%;-webkit-font-smoothing:antialiased}
body{font-family:-apple-system,BlinkMacSystemFont,"SF Pro Text","PingFang SC","Hiragino Sans GB","Microsoft YaHei",sans-serif;font-size:14px;line-height:1.7;color:#262626;overflow-x:hidden;word-break:break-all;overflow-wrap:break-word}
```

## 模板 CSS 与骨架

每个模板的完整 CSS 和 HTML 结构见对应参考文件：

- [memo 备忘录](templates/memo.md)
- [checklist 清单](templates/checklist.md)
- [report 报告](templates/report.md)
- [diary 日记](templates/diary.md)
- [notice 公告](templates/notice.md)
- [contract 合同](templates/contract.md)
- [location 定位](templates/location.md)
- [recipe 食谱](templates/recipe.md)

## 生成流程

1. 读取卡片名称，匹配模板类型
2. **有匹配模板** → 读取对应模板参考文件获取 CSS + HTML 骨架
3. **无匹配模板** → 进入自由创作模式，读取 [freeform 自由创作指南](templates/freeform.md)
4. 将通用 CSS 基底 + 模板/自由创作 CSS 合并写入 `<style>`
5. 按骨架结构填充角色内容
6. 输出完整自包含 HTML
