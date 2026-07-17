---
name: placement-place-part
metadata:
  category: placement
  service: ComponentPlaceService
  method: PlacePart
  rpcKind: unary
description: >-
  part
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: PlacePartRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Place Part

part

## Overview

This skill provides access to the **`ComponentPlaceService.PlacePart`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-place-part` |
| Service | `ComponentPlaceService` |
| Method | `PlacePart` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `PlacePartRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |
| `jsonPartInst` | `string` | yes | no | — |
| `jsonPart` | `string` | yes | no | — |

## Response

Returns a `ObjectPlaceResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `success` | `boolean` | no | — |
| `objectId` | `bigint` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "success": false,
  "objectId": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlacePartRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("placement-place-part");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
  jsonPartInst: "<string>",
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
npx skills add Huaqiu-Electronics/skills --path eda/placement/place-part

# Or install the full runtime package
npm install @huaqiu/hqeda
```

