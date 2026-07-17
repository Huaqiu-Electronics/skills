---
name: graph-query-graph
metadata:
  category: graph
  service: GraphService
  method: QueryGraph
  rpcKind: unary
description: >-
  Query Graph via GraphService.QueryGraph
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - graph
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: GraphQueryRequestSchema
  namespace: HqServicesV1GraphService
---

# Query Graph

Query Graph via GraphService.QueryGraph

## Overview

This skill provides access to the **`GraphService.QueryGraph`** RPC method on the Huaqiu EDA engine. It is part of the **graph** domain and executes against the `graph` client.

| Property | Value |
| --- | --- |
| Skill ID | `graph-query-graph` |
| Service | `GraphService` |
| Method | `QueryGraph` |
| Transport | Unary (unary) |
| Domain | graph |
| Request type | `GraphQueryRequest` |
| Response type | `GraphQueryResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `query` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GraphQueryRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("graph-query-graph");
const result = await skill.execute(ctx, {
  context: {},
  query: "<string>",
});
```

## Related Skills

Browse other **graph** skills in the [`graph/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/graph/query-graph

# Or install the full runtime package
npm install @huaqiu/hqeda
```

