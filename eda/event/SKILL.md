---
name: eda-event
metadata:
  category: event
description: >-
  Event operations for Huaqiu EDA. Use this skill when you need to work with event-related operations including subscribe.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - event
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Event Skills

Event operations for Huaqiu EDA. Use this skill when you need to work with event-related operations including subscribe.

## Available Capabilities

Total: **1** skills in the **event** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`subscribe`](subscribe/SKILL.md) | Subscribe via EventService.Subscribe | yes |

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

