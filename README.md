# UI-skill：AIGC 角色聊天卡片生成

AI 驱动的移动端 HTML 互动卡片生成系统。包含 8 个核心模板 + 自由创作模式，适用于角色聊天场景。

## 仓库结构

```
├── aigc-chat-card/          # Cursor Skill（AI 自动加载）
│   ├── SKILL.md             # Skill 入口定义
│   └── templates/           # 8 个模板 + 自由创作指南
├── design-system/           # 设计系统源文件
│   ├── SPEC.md              # 完整设计规范
│   ├── PROMPT.md            # 可直接用的 System Prompt
│   ├── base.css             # 通用 Reset + Token
│   ├── templates/           # 各模板 CSS
│   └── examples/            # 各模板示例 HTML
```

## 使用方式

### 方式一：Cursor Skill（推荐）

适用于使用 Cursor IDE 的同事，AI 会自动识别并调用。

1. Clone 仓库到本地：
   ```bash
   git clone git@github.com:Dreamelse-AI/UI-skill.git
   ```

2. 将 `aigc-chat-card` 文件夹复制到你的 Cursor skills 目录：
   ```bash
   cp -r UI-skill/aigc-chat-card ~/.cursor/skills/
   ```

3. 在 Cursor 中对话时，提到"生成卡片"、"角色聊天卡片"、"HTML 卡片"等关键词，AI 会自动加载 Skill 并按规范生成。

### 方式二：System Prompt 接入

适用于任何支持自定义 system prompt 的 AI 工具（ChatGPT、Claude、通义千问等）。

1. 打开 `design-system/PROMPT.md`
2. 将其中的全部内容复制到你的 system prompt 中
3. 然后正常对话，让 AI 生成对应类型的卡片即可

### 方式三：仅参考设计规范

如果只需要了解设计约束（字号、间距、配色等），阅读 `design-system/SPEC.md`。

## 支持的卡片类型

| 模板 | 关键词 | 强调色 |
|------|--------|--------|
| 备忘录 memo | 备忘录、笔记、纸条、便签 | #f5a623 |
| 清单 checklist | 清单、列表、待办、购物 | #10b981 |
| 报告 report | 报告、分析、数据、战报 | #6366f1 |
| 日记 diary | 日记、日志、心声、独白 | #ec4899 |
| 公告 notice | 公告、通知、声明、禁令 | #ef4444 |
| 合同 contract | 合同、契约、保证书、约定 | #92400e |
| 定位 location | 定位、位置、日程、行程 | #06b6d4 |
| 食谱 recipe | 食谱、菜单、美食、烹饪 | #ea580c |

不属于以上类型时，AI 会进入自由创作模式，从 10 组配色板 + 可复用组件库中自由组合。

## 预览示例

用浏览器打开 `design-system/examples/` 下的任意 HTML 文件即可预览效果。

打开 `design-system/index.html` 可查看所有模板的总览页。
