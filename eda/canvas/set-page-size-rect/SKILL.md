---
name: canvas-set-page-size-rect
metadata:
  category: canvas
  service: CanvasOpsService
  method: SetPageSizeRect
  rpcKind: unary
description: >-
  Set Page Size Rect via CanvasOpsService.SetPageSizeRect
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SetPageSizeRectRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Set Page Size Rect

Set Page Size Rect via CanvasOpsService.SetPageSizeRect

## Overview

This skill provides access to the **`CanvasOpsService.SetPageSizeRect`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-set-page-size-rect` |
| Service | `CanvasOpsService` |
| Method | `SetPageSizeRect` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `SetPageSizeRectRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `x` | `number` | yes | no | — |
| `y` | `number` | yes | no | — |
| `sx` | `number` | yes | no | — |
| `sy` | `number` | yes | no | — |

## Response

Returns a `SuccessResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `success` | `boolean` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "success": false
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetPageSizeRectRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("canvas-set-page-size-rect");
const result = await skill.execute(ctx, {
  context: {},
  x: 0,
  y: 0,
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

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/set-page-size-rect

# Or install the full runtime package
npm install @huaqiu/hqeda
```

