---
name: transaction-open
metadata:
  category: transaction
  service: TransactionService
  method: Open
  rpcKind: unary
description: >-
  Open via TransactionService.Open
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: TransactionOpenRequestSchema
  namespace: HqRuntimeV1Transaction
---

# Open

Open via TransactionService.Open

## Overview

This skill provides access to the **`TransactionService.Open`** RPC method on the Huaqiu EDA engine. It is part of the **transaction** domain and executes against the `transaction` client.

| Property | Value |
| --- | --- |
| Skill ID | `transaction-open` |
| Service | `TransactionService` |
| Method | `Open` |
| Transport | Unary (unary) |
| Domain | transaction |
| Request type | `TransactionOpenRequest` |
| Response type | `TransactionOpenResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `branchName` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `TransactionOpenRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("transaction-open");
const result = await skill.execute(ctx, {
  context: {},
  branchName: "<string>",
});
```

## Related Skills

Browse other **transaction** skills in the [`transaction/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/transaction/open

# Or install the full runtime package
npm install @huaqiu/hqeda
```

