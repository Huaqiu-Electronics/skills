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
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
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

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `TransactionDiscardRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("transaction-rollback");
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
npx skills add Huaqiu-Electronics/skills --path eda/transaction/rollback

# Or install the full runtime package
npm install @huaqiu/hqeda
```

