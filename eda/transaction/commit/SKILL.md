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

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `TransactionCommitRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("transaction-commit");
const result = await skill.execute(ctx, {
  context: {},
  transactionId: "<string>",
});
```

## Related Skills

Browse other **transaction** skills in the [`transaction/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/transaction/commit

# Or install the full runtime package
npm install @huaqiu/hqeda
```

