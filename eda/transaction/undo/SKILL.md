---
name: transaction-undo
metadata:
  category: transaction
  service: TransactionService
  method: Undo
  rpcKind: unary
description: >-
  Undo via TransactionService.Undo
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: UndoRequestSchema
  namespace: HqRuntimeV1Undo
---

# Undo

Undo via TransactionService.Undo

## Overview

This skill provides access to the **`TransactionService.Undo`** RPC method on the Huaqiu EDA engine. It is part of the **transaction** domain and executes against the `transaction` client.

| Property | Value |
| --- | --- |
| Skill ID | `transaction-undo` |
| Service | `TransactionService` |
| Method | `Undo` |
| Transport | Unary (unary) |
| Domain | transaction |
| Request type | `UndoRequest` |
| Response type | `UndoResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `steps` | `number` | yes | no | default = 1 |

## Response

Returns a `UndoResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `success` | `boolean` | no | — |
| `newRevision` | `bigint` | no | — |
| `appliedSteps` | `number` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "success": false,
  "newRevision": "0",
  "appliedSteps": 0
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `UndoRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("transaction-undo");
const result = await skill.execute(ctx, {
  context: {},
  steps: 0,
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

Browse other **transaction** skills in the [`transaction/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/transaction/undo

# Or install the full runtime package
npm install @huaqiu/hqeda
```

