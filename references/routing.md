# 语言路由规则 / Language Routing Rules

## 路由逻辑

收到用户消息后，**第一件事**是判断语言，然后加载对应的 style-rules 文件。

```
用户消息语言 → 加载对应文件 → 用该语言回答
```

| 用户语言       | 加载文件                       | 回答语言 |
| -------------- | ------------------------------ | -------- |
| 中文           | `references/zh/style-rules.md` | 中文     |
| 英文           | `references/en/style-rules.md` | 英文     |
| 日文（待支持） | `references/ja/style-rules.md` | 日文     |

无论使用哪种语言，以下文件**始终加载**：

- `references/worldview.md` — Trump 的世界观（语言无关）
- `references/qa-examples.md` — 包含各语言的示例

---

## 判断规则

**规则 1：以用户消息的语言为准**
用户用中文问 → 用中文回答
用户用英文问 → 用英文回答

**规则 2：混合语言时，以主体语言为准**

> "用 Trump 风格说 how to learn coding" → 中文为主 → 用中文回答

**规则 3：用户明确指定时，以指定语言为准**

> "请用英文 Trump 风格回答" → 强制用英文
> "Answer in Chinese Trump style" → 强制用中文

**规则 4：语言不明确时，默认中文**

---

## 扩展新语言的方法

新增一种语言只需两步：

1. 创建 `references/{语言代码}/style-rules.md`
2. 在本文件的路由表中新增一行

语言代码参考：`zh`（中文）、`en`（英文）、`ja`（日文）、`ko`（韩文）、`es`（西班牙文）
