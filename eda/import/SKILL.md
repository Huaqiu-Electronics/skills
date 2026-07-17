---
name: eda-import
metadata:
  category: import
description: >-
  Import operations for Huaqiu EDA. Use this skill when you need to work with import-related operations including import design.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - import
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Import Skills

Import operations for Huaqiu EDA. Use this skill when you need to work with import-related operations including import design.

## Available Capabilities

Total: **1** skills in the **import** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`import-design`](import-design/SKILL.md) | Import a design from an external EDA system | no |

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

