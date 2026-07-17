---
name: eda-discovery
metadata:
  category: discovery
description: >-
  Discovery operations for Huaqiu EDA. Use this skill when you need to work with discovery-related operations including get server info.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - discovery
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Discovery Skills

Discovery operations for Huaqiu EDA. Use this skill when you need to work with discovery-related operations including get server info.

## Available Capabilities

Total: **1** skills in the **discovery** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`get-server-info`](get-server-info/SKILL.md) | Get Server Info via DiscoveryService.GetServerInfo | no |

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

