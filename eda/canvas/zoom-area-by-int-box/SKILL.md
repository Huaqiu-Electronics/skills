---
name: canvas-zoom-area-by-int-box
metadata:
  category: canvas
  service: CanvasOpsService
  method: ZoomAreaByIntBox
  rpcKind: unary
description: >-
  Zoom Area By Int Box via CanvasOpsService.ZoomAreaByIntBox
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ZoomAreaIntBoxRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Zoom Area By Int Box

Zoom Area By Int Box via CanvasOpsService.ZoomAreaByIntBox

## Overview

This skill provides access to the **`CanvasOpsService.ZoomAreaByIntBox`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-zoom-area-by-int-box` |
| Service | `CanvasOpsService` |
| Method | `ZoomAreaByIntBox` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `ZoomAreaIntBoxRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `startX` | `number` | yes | no | — |
| `startY` | `number` | yes | no | — |
| `endX` | `number` | yes | no | — |
| `endY` | `number` | yes | no | — |

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

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ZoomAreaIntBoxRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("canvas-zoom-area-by-int-box");
const result = await skill.execute(ctx, {
  context: {},
  startX: 0,
  startY: 0,
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
npx skills add Huaqiu-Electronics/skills --path eda/canvas/zoom-area-by-int-box

# Or install the full runtime package
npm install @huaqiu/hqeda
```

