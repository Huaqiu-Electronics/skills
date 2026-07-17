---
name: graph-get-connectivity
metadata:
  category: graph
  service: GraphService
  method: GetConnectivity
  rpcKind: unary
description: >-
  Get Connectivity via GraphService.GetConnectivity
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - graph
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ConnectivityRequestSchema
  namespace: HqServicesV1GraphService
---

# Get Connectivity

Get Connectivity via GraphService.GetConnectivity

## Overview

This skill provides access to the **`GraphService.GetConnectivity`** RPC method on the Huaqiu EDA engine. It is part of the **graph** domain and executes against the `graph` client.

| Property | Value |
| --- | --- |
| Skill ID | `graph-get-connectivity` |
| Service | `GraphService` |
| Method | `GetConnectivity` |
| Transport | Unary (unary) |
| Domain | graph |
| Request type | `ConnectivityRequest` |
| Response type | `ConnectivityResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `netIds` | `string[]` | no | yes | — |
| `symbolIds` | `string[]` | no | yes | — |

## Response

Returns a `ConnectivityResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `connectivity` | `ConnectivityGraph` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "connectivity": {}
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ConnectivityRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("graph-get-connectivity");
const result = await skill.execute(ctx, {
  context: {},
  netIds: [],
  symbolIds: [],
});

// Always use toJsonString() to serialize protobuf messages —
// never use JSON.stringify() directly (it fails on BigInt fields).
console.log(toJsonString(result, { prettySpaces: 2 }));
```

## Serializing Protobuf Messages

Skill responses are protobuf message objects. **Do NOT use `JSON.stringify()` directly** — it will throw `Do not know how to serialize a BigInt` on 64-bit integer fields and produce empty objects for oneof ADT fields.

Instead, use the `toJson()` or `toJsonString()` helpers:

```typescript
import { toJson, toJsonString } from "@huaqiu/hqeda";

// Plain JSON object (BigInts converted to strings)
const jsonObj = toJson(result);

// Formatted JSON string
const jsonStr = toJsonString(result, { prettySpaces: 2 });

// Include zero-valued fields in output
const full = toJsonString(result, { alwaysEmitImplicit: true });
```

These helpers correctly handle:

- **BigInt fields** — converted to strings (protobuf JSON convention)
- **oneof fields** — serialized as `{ case, value }` ADT objects
- **Well-known types** — `Timestamp` → ISO string, `Duration` → `"Ns"` format, `Struct` → plain object
- **bytes fields** — base64-encoded strings
- **Zero-value omission** — empty fields are excluded (protobuf default)

## Related Skills

Browse other **graph** skills in the [`graph/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/graph/get-connectivity

# Or install the full runtime package
npm install @huaqiu/hqeda
```

