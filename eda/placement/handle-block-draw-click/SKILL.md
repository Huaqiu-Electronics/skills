---
name: placement-handle-block-draw-click
metadata:
  category: placement
  service: ComponentPlaceService
  method: HandleBlockDrawClick
  rpcKind: unary
description: >-
  Handle Block Draw Click via ComponentPlaceService.HandleBlockDrawClick
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: LocalClickRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Handle Block Draw Click

Handle Block Draw Click via ComponentPlaceService.HandleBlockDrawClick

## Overview

This skill provides access to the **`ComponentPlaceService.HandleBlockDrawClick`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-handle-block-draw-click` |
| Service | `ComponentPlaceService` |
| Method | `HandleBlockDrawClick` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `LocalClickRequest` |
| Response type | `HandleBlockDrawClickResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |

## Response

Returns a `HandleBlockDrawClickResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `result` | `BlockDrawClickResult` | no | — |
| `objectId` | `bigint` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "result": {},
  "objectId": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `LocalClickRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("placement-handle-block-draw-click");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
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

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/handle-block-draw-click

# Or install the full runtime package
npm install @huaqiu/hqeda
```

