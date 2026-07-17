---
name: obj-place-handle-text-draw-click
metadata:
  category: obj-place
  service: ObjPlaceService
  method: HandleTextDrawClick
  rpcKind: unary
description: >-
  Handle Text Draw Click via ObjPlaceService.HandleTextDrawClick
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: LocalClickRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Handle Text Draw Click

Handle Text Draw Click via ObjPlaceService.HandleTextDrawClick

## Overview

This skill provides access to the **`ObjPlaceService.HandleTextDrawClick`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-handle-text-draw-click` |
| Service | `ObjPlaceService` |
| Method | `HandleTextDrawClick` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `LocalClickRequest` |
| Response type | `HandleTextDrawClickResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |

## Response

Returns a `HandleTextDrawClickResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `result` | `TextDrawClickResult` | no | — |
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

const skill = getSkill("obj-place-handle-text-draw-click");
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

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/handle-text-draw-click

# Or install the full runtime package
npm install @huaqiu/hqeda
```

