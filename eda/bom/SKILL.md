---
name: eda-bom
metadata:
  category: bom
description: >-
  Bom operations for Huaqiu EDA. Use this skill when you need to work with bom-related operations including get bom.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - bom
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Bom Skills

Bom operations for Huaqiu EDA. Use this skill when you need to work with bom-related operations including get bom.

## Available Capabilities

Total: **1** skills in the **bom** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`get-bom`](get-bom/SKILL.md) | Get full BOM snapshot from current schematic state | no |

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

