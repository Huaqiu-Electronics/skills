---
name: selection-clear-selection
metadata:
  category: selection
  service: SelectionService
  method: ClearSelection
  rpcKind: unary
description: >-
  Clear Selection via SelectionService.ClearSelection
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ClearSelectionRequestSchema
  namespace: HqServicesV1SelectionService
---

# Clear Selection

Clear Selection via SelectionService.ClearSelection

## Overview

This skill provides access to the **`SelectionService.ClearSelection`** RPC method on the Huaqiu EDA engine. It is part of the **selection** domain and executes against the `selection` client.

| Property | Value |
| --- | --- |
| Skill ID | `selection-clear-selection` |
| Service | `SelectionService` |
| Method | `ClearSelection` |
| Transport | Unary (unary) |
| Domain | selection |
| Request type | `ClearSelectionRequest` |
| Response type | `ClearSelectionResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## Response

Returns a `ClearSelectionResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `selectionRevision` | `bigint` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "selectionRevision": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ClearSelectionRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("selection-clear-selection");
const result = await skill.execute(ctx, {
  context: {},
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

Browse other **selection** skills in the [`selection/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/selection/clear-selection

# Or install the full runtime package
npm install @huaqiu/hqeda
```

