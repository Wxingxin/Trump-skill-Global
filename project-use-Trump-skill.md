# 案例 在nextjs中可以通过 chatgpt claude deepseek等的api 使用

整个集成方案分三层：

```
skill 文件（.md）→ 读取内容 → 拼接成 system prompt → 发给 API
```

---

## 推荐的项目结构

```
your-nextjs-app/
├── skills/
│   └── trump/                     ← 把整个 skill 文件夹放进来
│       ├── SKILL.md
│       └── references/
│           ├── routing.md
│           ├── worldview.md
│           ├── qa-examples.md
│           ├── zh/style-rules.md
│           └── en/style-rules.md
├── lib/
│   └── skills.ts                  ← 读取和组装 skill 的工具函数（新增）
└── app/
    └── api/
        └── chat/
            └── route.ts           ← 你现有的 API 路由（修改）
```

---

## 第一步：写 `lib/skills.ts`

这个文件负责读取 skill 文件、检测语言、拼接 system prompt：

```ts
import fs from "fs";
import path from "path";

// 检测语言
function detectLanguage(message: string): "zh" | "en" {
  const chineseChars = message.match(/[\u4e00-\u9fa5]/g);
  const ratio = (chineseChars?.length ?? 0) / message.length;
  return ratio > 0.1 ? "zh" : "en";
}

// 读取 skill 文件
function readSkillFile(skillName: string, filePath: string): string {
  const fullPath = path.join(process.cwd(), "skills", skillName, filePath);
  if (!fs.existsSync(fullPath)) return "";
  return fs.readFileSync(fullPath, "utf-8");
}

// 组装完整 system prompt
export function buildSkillPrompt(
  skillName: string,
  userMessage: string,
): string {
  const lang = detectLanguage(userMessage);

  const core = readSkillFile(skillName, "SKILL.md");
  const worldview = readSkillFile(skillName, "references/worldview.md");
  const styleRules = readSkillFile(
    skillName,
    `references/${lang}/style-rules.md`,
  );
  const examples = readSkillFile(skillName, "references/qa-examples.md");

  return [core, worldview, styleRules, examples]
    .filter(Boolean)
    .join("\n\n---\n\n");
}
```

---

## 第二步：在 API 路由里注入 system prompt

你的 `app/api/chat/route.ts` 大概长这样，只需要加几行：

```ts
import { buildSkillPrompt } from "@/lib/skills";

export async function POST(req: Request) {
  const { messages, skill } = await req.json();
  // skill 由前端传过来，比如 'trump'，没传就走普通模式

  // 获取最后一条用户消息用于语言检测
  const lastUserMessage =
    messages.findLast((m: any) => m.role === "user")?.content ?? "";

  // 组装 system prompt
  const systemPrompt = skill
    ? buildSkillPrompt(skill, lastUserMessage)
    : "You are a helpful assistant.";

  // ---- OpenAI ----
  const openaiRes = await openai.chat.completions.create({
    model: "gpt-4o",
    messages: [{ role: "system", content: systemPrompt }, ...messages],
    stream: true,
  });

  // ---- Anthropic ----
  const anthropicRes = await anthropic.messages.create({
    model: "claude-sonnet-4-20250514",
    system: systemPrompt, // Anthropic 的 system 是单独字段
    messages,
    max_tokens: 1024,
    stream: true,
  });

  // ---- DeepSeek（兼容 OpenAI 格式）----
  const deepseekRes = await deepseek.chat.completions.create({
    model: "deepseek-chat",
    messages: [{ role: "system", content: systemPrompt }, ...messages],
    stream: true,
  });
}
```

---

## 第三步：前端传入 skill 参数

在你的聊天组件里，发请求时带上 `skill` 字段：

```ts
// 普通模式
fetch("/api/chat", {
  body: JSON.stringify({ messages }),
});

// 开启 Trump skill
fetch("/api/chat", {
  body: JSON.stringify({ messages, skill: "trump" }),
});
```

UI 上可以加一个切换按钮，比如：

```tsx
<button onClick={() => setSkill(skill === "trump" ? null : "trump")}>
  {skill === "trump" ? "🇺🇸 Trump 模式 ON" : "普通模式"}
</button>
```

---

## 要点总结

以后再加新 skill（比如马斯克、乔布斯），只需要：

1. 在 `skills/` 下新建文件夹
2. 前端传对应的 `skill` 名字

`lib/skills.ts` 和 API 路由**完全不用改**。
