---
name: eda-context
metadata:
  category: context
description: >-
  Context operations for Huaqiu EDA. Use this skill when you need to work with context-related operations including get context.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - context
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Context Skills

Context operations for Huaqiu EDA. Use this skill when you need to work with context-related operations including get context.

## Available Capabilities

Total: **1** skills in the **context** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`get-context`](get-context/SKILL.md) | Get Context via ContextService.GetContext | no |

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

