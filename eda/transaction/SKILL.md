---
name: eda-transaction
metadata:
  category: transaction
description: >-
  Transaction operations for Huaqiu EDA. Use this skill when you need to work with transaction-related operations including commit, open, redo.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Transaction Skills

Transaction operations for Huaqiu EDA. Use this skill when you need to work with transaction-related operations including commit, open, redo.

## Available Capabilities

Total: **5** skills in the **transaction** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`commit`](commit/SKILL.md) | Commit via TransactionService.Commit | no |
| [`open`](open/SKILL.md) | Open via TransactionService.Open | no |
| [`redo`](redo/SKILL.md) | Redo via TransactionService.Redo | no |
| [`rollback`](rollback/SKILL.md) | Rollback via TransactionService.Rollback | no |
| [`undo`](undo/SKILL.md) | Undo via TransactionService.Undo | no |

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

