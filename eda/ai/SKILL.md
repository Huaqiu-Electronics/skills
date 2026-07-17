---
name: eda-ai
metadata:
  category: ai
description: >-
  Ai operations for Huaqiu EDA. Use this skill when you need to work with ai-related operations including execute prompt.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - ai
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Ai Skills

Ai operations for Huaqiu EDA. Use this skill when you need to work with ai-related operations including execute prompt.

## Available Capabilities

Total: **1** skills in the **ai** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`execute-prompt`](execute-prompt/SKILL.md) | Execute Prompt via AIService.ExecutePrompt | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

## Best Practices

**Always use `toJsonString()` (not `JSON.stringify()`) to serialize protobuf responses.** `JSON.stringify()` throws on `BigInt` fields and mishandles oneof ADT fields.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const result = await skill.execute(ctx, input);
console.log(toJsonString(result, { prettySpaces: 2 }));
```

