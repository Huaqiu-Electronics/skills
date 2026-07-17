---
name: transaction-commit
metadata:
  category: transaction
  service: TransactionService
  method: Commit
  rpcKind: unary
description: >-
  Commit via TransactionService.Commit
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: TransactionCommitRequestSchema
  namespace: HqRuntimeV1Transaction
---

# Commit

Commit via TransactionService.Commit

## Overview

This skill provides access to the **`TransactionService.Commit`** RPC method on the Huaqiu EDA engine. It is part of the **transaction** domain and executes against the `transaction` client.

| Property | Value |
| --- | --- |
| Skill ID | `transaction-commit` |
| Service | `TransactionService` |
| Method | `Commit` |
| Transport | Unary (unary) |
| Domain | transaction |
| Request type | `TransactionCommitRequest` |
| Response type | `TransactionCommitResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `transactionId` | `string` | yes | no | — |

## Response

Returns a `TransactionCommitResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `newRevision` | `bigint` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "newRevision": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `TransactionCommitRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("transaction-commit");
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
npx skills add Huaqiu-Electronics/skills --path eda/transaction/commit

# Or install the full runtime package
npm install @huaqiu/hqeda
```

