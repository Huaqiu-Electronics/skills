---
name: eda-graph
metadata:
  category: graph
description: >-
  Graph operations for Huaqiu EDA. Use this skill when you need to work with graph-related operations including get connectivity, query graph.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - graph
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Graph Skills

Graph operations for Huaqiu EDA. Use this skill when you need to work with graph-related operations including get connectivity, query graph.

## Available Capabilities

Total: **2** skills in the **graph** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`get-connectivity`](get-connectivity/SKILL.md) | Get Connectivity via GraphService.GetConnectivity | no |
| [`query-graph`](query-graph/SKILL.md) | Query Graph via GraphService.QueryGraph | no |

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

