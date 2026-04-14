# 🇺🇸 Trump 风格 AI Skill

> 用特朗普（Donald J. Trump）的口吻和思维方式回答任何问题、撰写演讲稿、写社交媒体内容。
> 支持 **中文 / 英文**，后续可扩展更多语言。
> 同时兼容 **Claude Skill** 和 **OpenAI Custom GPT** 两个平台。

---

## 示例效果

**问：** 前端开发用 Vue 还是 React？

**答：**

> 我跟你说，Vue、React——都是工具。好工具。但你知道谁用 React 吗？Facebook。赚了多少钱？巨额的钱。赢家用 React。说真的，没有人比我更懂选择工具。关键不是工具，是执行力。选 React。相信我。

---

## 文件结构

```
trump-skill/
├── README.md                  ← 你正在看的这个
├── SKILL.md                   ← Claude Skill 核心文件
├── openai-gpt-config.md       ← OpenAI Custom GPT 配置指南
└── references/
    ├── routing.md             ← 语言路由规则
    ├── worldview.md           ← 世界观与核心信念（语言无关，共用）
    ├── qa-examples.md         ← 各语言问答示例（Few-shot）
    ├── zh/
    │   └── style-rules.md    ← 中文专属风格规则
    └── en/
        └── style-rules.md    ← 英文专属风格规则
```

> 以后新增日语，只需创建 `references/ja/style-rules.md`，其他文件无需改动。

---

## 快速上手

### 方式一：Claude Skill

1. 将整个 `trump-skill/` 文件夹上传或配置到你的 Claude Skill 目录
2. 触发方式：
   - 中文：「用 Trump 的风格回答」、「特朗普口吻」、「川普来说说」
   - 英文：「Answer in Trump style」、「What would Trump say」
3. AI 会自动检测用户语言，加载对应的 `references/{语言}/style-rules.md`

### 方式二：OpenAI Custom GPT

打开 [chatgpt.com/create](https://chatgpt.com/create)，参照 `openai-gpt-config.md` 填写：

| GPT 字段              | 对应文件                          |
| --------------------- | --------------------------------- |
| Name                  | 见配置文件第 1 节                 |
| Description           | 见配置文件第 2 节                 |
| Instructions          | 见配置文件第 3 节（直接粘贴）     |
| Conversation Starters | 见配置文件第 4 节                 |
| Knowledge 上传文件    | `references/` 下的三个 `.md` 文件 |

---

## 核心风格特征

这个 skill 基于对 Trump 语言模式的学术分析构建，捕捉了以下关键特征：

- **极端化表达** — 只有最好和最坏，没有中间地带
- **重复强调** — 重要词语重复 2-3 次，用于替代逻辑论证
- **短句直击** — 小学级别词汇，一句一个意思
- **永远是主角** — 任何话题都会拉回自己的成就
- **"The Weave"跑题法** — 说着说着跑到别的话题，再绕回来
- **引用"很多人"** — 用虚指的群体背书自己的观点

---

## 适用场景

- 用 Trump 风格写演讲稿或社交媒体帖子
- 用 Trump 口吻回答日常问题（娱乐向）
- 研究政治人物的语言风格与修辞学
- 创意写作、内容创作的风格练习

---

## 注意事项

- 本 skill 仅模仿语言**风格和思维方式**，不捏造具体政策数据或历史事件
- 不生成针对具体真实个人的侮辱性内容
- 内容仅供娱乐和创意写作，不代表任何政治立场

---

## 平台兼容性

| 平台               | 支持 | 说明                                 |
| ------------------ | ---- | ------------------------------------ |
| Claude (claude.ai) | ✅   | 使用 `SKILL.md`                      |
| OpenAI ChatGPT     | ✅   | 使用 `openai-gpt-config.md`          |
| API 调用           | ✅   | 将 `SKILL.md` 内容作为 system prompt |

---

## License

MIT — 自由使用、修改、分发。
