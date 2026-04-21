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

### 方式三：后端 API 调用 LLM 自动生成

适用于自动化链路，后端服务调用 LLM API 按规范生成卡片 HTML。

**推荐：按需加载模板（省 token）**

先判断卡片类型，只加载对应模板，拼装精简 system prompt：

```python
import httpx

REPO_BASE = "https://raw.githubusercontent.com/Dreamelse-AI/UI-skill/小手机html"

# 关键词 → 模板类型映射
KEYWORD_MAP = {
    "memo": ["备忘录", "笔记", "纸条", "便签", "碎碎念"],
    "checklist": ["清单", "列表", "待办", "购物", "搬家"],
    "report": ["报告", "分析", "数据", "战报", "心率", "统计"],
    "diary": ["日记", "日志", "心声", "独白", "自白"],
    "notice": ["公告", "通知", "声明", "禁令", "规则", "预警"],
    "contract": ["合同", "契约", "保证书", "承诺", "约定"],
    "location": ["定位", "位置", "日程", "行程", "天气"],
    "recipe": ["食谱", "菜单", "美食", "烹饪", "甜品"],
}

def classify_card_type(card_name: str) -> str:
    for tpl, keywords in KEYWORD_MAP.items():
        if any(kw in card_name for kw in keywords):
            return tpl
    return "freeform"

def load_template(card_type: str) -> str:
    url = f"{REPO_BASE}/aigc-chat-card/templates/{card_type}.md"
    return httpx.get(url).text

def generate_card(card_name: str, role_name: str, content: str) -> str:
    card_type = classify_card_type(card_name)
    template = load_template(card_type)

    system_prompt = f"""你需要生成一个移动端 HTML 互动卡片。
规则：
- 输出完整 HTML（含 <!DOCTYPE html>），CSS 内联在 <style> 中
- 禁止外部资源（字体/图片/CSS）、JavaScript、position:fixed
- 卡片 max-width:420px 居中，内边距水平 20px 垂直 24px
- 字号：标注 11px / 次要 12px / 正文 14px / 标题 17px
- 颜色：主文本 #262626 / 次要 #737373 / 弱化 #a3a3a3，禁止纯黑 #000
- 必须包含角色署名：—— {role_name}

以下是模板参考（严格遵循其 CSS 和 HTML 结构）：
{template}"""

    response = client.chat.completions.create(
        model="gpt-4o",
        messages=[
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": f"卡片名称：{card_name}\n角色：{role_name}\n内容：{content}"},
        ],
    )
    return response.choices[0].message.content

# 调用示例
html = generate_card("今日备忘录", "小狐狸", "今天要去超市买菜，记得带环保袋")
```

**备选：完整 Prompt 一次性加载**

如果不想做类型判断，可以直接加载 `PROMPT.md` 作为 system prompt（包含全部 8 个模板，token 较多）：

```python
system_prompt = httpx.get(f"{REPO_BASE}/design-system/PROMPT.md").text
```

**生产环境建议**

- 将模板文件缓存到本地或 Redis，避免每次请求都拉 GitHub
- 也可以用 git submodule 将仓库集成到业务代码中，直接读本地文件：
  ```bash
  git submodule add git@github.com:Dreamelse-AI/UI-skill.git lib/ui-skill
  ```
- LLM 返回的 HTML 建议做一次 sanitize，过滤掉可能的 `<script>` 标签

### 方式四：仅参考设计规范

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
