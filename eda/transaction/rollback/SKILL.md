---
name: transaction-rollback
metadata:
  category: transaction
  service: TransactionService
  method: Rollback
  rpcKind: unary
description: >-
  Rollback via TransactionService.Rollback
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: TransactionDiscardRequestSchema
  namespace: HqRuntimeV1Transaction
---

# Rollback

Rollback via TransactionService.Rollback

## Overview

This skill provides access to the **`TransactionService.Rollback`** RPC method on the Huaqiu EDA engine. It is part of the **transaction** domain and executes against the `transaction` client.

| Property | Value |
| --- | --- |
| Skill ID | `transaction-rollback` |
| Service | `TransactionService` |
| Method | `Rollback` |
| Transport | Unary (unary) |
| Domain | transaction |
| Request type | `TransactionDiscardRequest` |
| Response type | `TransactionDiscardResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `transactionId` | `string` | yes | no | — |

## Response

Returns a `TransactionDiscardResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `discarded` | `boolean` | no | — |
| `newRevision` | `bigint` | no | main-graph revision post-discard (unchanged) |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "discarded": false,
  "newRevision": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `TransactionDiscardRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("transaction-rollback");
const result = await skill.execute(ctx, {
  context: {},
  transactionId: "<string>",
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
npx skills add Huaqiu-Electronics/skills --path eda/transaction/rollback

# Or install the full runtime package
npm install @huaqiu/hqeda
```

