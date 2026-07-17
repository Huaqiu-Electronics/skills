---
name: selection-get-selection
metadata:
  category: selection
  service: SelectionService
  method: GetSelection
  rpcKind: unary
description: >-
  Get Selection via SelectionService.GetSelection
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetSelectionRequestSchema
  namespace: HqServicesV1SelectionService
---

# Get Selection

Get Selection via SelectionService.GetSelection

## Overview

This skill provides access to the **`SelectionService.GetSelection`** RPC method on the Huaqiu EDA engine. It is part of the **selection** domain and executes against the `selection` client.

| Property | Value |
| --- | --- |
| Skill ID | `selection-get-selection` |
| Service | `SelectionService` |
| Method | `GetSelection` |
| Transport | Unary (unary) |
| Domain | selection |
| Request type | `GetSelectionRequest` |
| Response type | `GetSelectionResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `typeFilter` | `string[]` | no | yes | Optional filter.  If non-empty, the server returns only ids whose
domain type is listed.  This lets callers ask for "just symbols"
or "just nets" without post-processing. |

## Response

Returns a `GetSelectionResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `entityIds` | `string[]` | yes | Entity ids from the kernel graph (symbol_instance_id, net_id, …). |

## Usage Examples

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

### set selection on a discovered project

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "entityIds": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetSelectionRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("selection-get-selection");
const result = await skill.execute(ctx, {
  context: {},
  typeFilter: [],
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
npx skills add Huaqiu-Electronics/skills --path eda/selection/get-selection

# Or install the full runtime package
npm install @huaqiu/hqeda
```

