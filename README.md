# 🇺🇸 Trump Style AI Skill

Let AI speak like Donald J. Trump. Supports Chinese and English. Compatible with Claude Skill and OpenAI Custom GPT.

---

## Demo

**English**

> Q: Vue or React for frontend?
>
> A: Look — many people ask me this. Very smart people. The answer is simple. React. Facebook uses it. You know how much money they make? Tremendous money. Winners use React. Use it. Believe me.

**中文**

> 问：前端用 Vue 还是 React？
>
> 答：我跟你说，这个问题——很多人问我，非常非常聪明的人。答案很简单。React。Facebook 用它，赚了多少钱？巨额的钱。赢家用 React。选它。相信我。

---

## File Structure

```
trump-skill/
├── README.md                      ← This file
├── SKILL.md                       ← Claude Skill core instructions
├── openai-gpt-config.md           ← OpenAI Custom GPT configuration guide
└── references/
    ├── routing.md                 ← Language routing rules
    ├── worldview.md               ← Trump's worldview (shared across all languages)
    ├── qa-examples.md             ← Q&A examples in Chinese and English
    ├── zh/
    │   └── style-rules.md        ← Chinese style rules
    └── en/
        └── style-rules.md        ← English style rules
```

**To add a new language:** just create `references/{lang}/style-rules.md`. No other files need to change.

---

## Usage

### Claude Skill

1. Add the project folder to your Claude Skill directory
2. Trigger in conversation:
   - English: "Answer in Trump style", "What would Trump say"
   - Chinese: 「用特朗普的风格回答」「川普口吻」
3. AI auto-detects your language and loads the matching style rules

### OpenAI Custom GPT

Open [chatgpt.com/create](https://chatgpt.com/create), follow `openai-gpt-config.md` to fill in each field, and upload the `references/` files as Knowledge.

### As a System Prompt

Paste `SKILL.md` content as a system prompt. Works with any platform that supports custom system prompts.

---

## Language Support

| Language | Status | Style File                     |
| -------- | ------ | ------------------------------ |
| English  | ✅     | `references/en/style-rules.md` |
| Chinese  | ✅     | `references/zh/style-rules.md` |
| Japanese | 🔜     | `references/ja/style-rules.md` |
| Korean   | 🔜     | `references/ko/style-rules.md` |

---

## Platform Compatibility

| Platform           | Support | File                        |
| ------------------ | ------- | --------------------------- |
| Claude (claude.ai) | ✅      | `SKILL.md`                  |
| OpenAI ChatGPT     | ✅      | `openai-gpt-config.md`      |
| Others (API)       | ✅      | `SKILL.md` as system prompt |

---

## Disclaimer

- This project imitates language style only and does not represent any political position
- Does not fabricate specific policy data or historical events
- Does not generate insulting content targeting real individuals

---

## License

MIT

---

---

# 🇺🇸 Trump 风格 AI Skill

让 AI 用特朗普（Donald J. Trump）的口吻说话。支持中文和英文，兼容 Claude Skill 和 OpenAI Custom GPT。

---

## 效果示例

**英文**

> Q: Vue or React for frontend?
>
> A: Look — many people ask me this. Very smart people. The answer is simple. React. Facebook uses it. You know how much money they make? Tremendous money. Winners use React. Use it. Believe me.

**中文**

> 问：前端用 Vue 还是 React？
>
> 答：我跟你说，这个问题——很多人问我，非常非常聪明的人。答案很简单。React。Facebook 用它，赚了多少钱？巨额的钱。赢家用 React。选它。相信我。

---

## 文件结构

```
trump-skill/
├── README.md                      ← 当前文件
├── SKILL.md                       ← Claude Skill 核心指令
├── openai-gpt-config.md           ← OpenAI Custom GPT 配置指南
└── references/
    ├── routing.md                 ← 语言路由规则
    ├── worldview.md               ← Trump 世界观（语言无关，所有语言共用）
    ├── qa-examples.md             ← 中英文问答示例
    ├── zh/
    │   └── style-rules.md        ← 中文风格规则
    └── en/
        └── style-rules.md        ← 英文风格规则
```

**扩展新语言只需一步：** 新建 `references/{语言代码}/style-rules.md`，其余文件不用动。

---

## 使用方式

### Claude Skill

1. 将整个项目文件夹配置到 Claude Skill 目录
2. 对话中触发：
   - 中文：「用特朗普的风格回答」「川普口吻」「Trump 风格」
   - 英文：「Answer in Trump style」「What would Trump say」
3. AI 自动检测用户语言，加载对应风格规则

### OpenAI Custom GPT

打开 [chatgpt.com/create](https://chatgpt.com/create)，按照 `openai-gpt-config.md` 的说明填写各字段，上传 `references/` 下的文件作为 Knowledge。

### 直接用作 System Prompt

将 `SKILL.md` 的内容粘贴为 system prompt，兼容任何支持自定义 system prompt 的平台。

---

## 语言支持

| 语言 | 状态      | 风格文件                       |
| ---- | --------- | ------------------------------ |
| 中文 | ✅ 支持   | `references/zh/style-rules.md` |
| 英文 | ✅ 支持   | `references/en/style-rules.md` |
| 日文 | 🔜 待扩展 | `references/ja/style-rules.md` |
| 韩文 | 🔜 待扩展 | `references/ko/style-rules.md` |

---

## 平台兼容

| 平台               | 兼容 | 使用文件                          |
| ------------------ | ---- | --------------------------------- |
| Claude (claude.ai) | ✅   | `SKILL.md`                        |
| OpenAI ChatGPT     | ✅   | `openai-gpt-config.md`            |
| 其他（API/自定义） | ✅   | `SKILL.md` 内容作为 system prompt |

---

## 注意事项

- 本项目仅模仿语言风格，不代表任何政治立场
- 不捏造具体政策数据或历史事件
- 不生成针对真实个人的侮辱性内容

---

## License

MIT
