---
name: transaction-redo
metadata:
  category: transaction
  service: TransactionService
  method: Redo
  rpcKind: unary
description: >-
  Redo via TransactionService.Redo
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - transaction
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: RedoRequestSchema
  namespace: HqRuntimeV1Undo
---

# Redo

Redo via TransactionService.Redo

## Overview

This skill provides access to the **`TransactionService.Redo`** RPC method on the Huaqiu EDA engine. It is part of the **transaction** domain and executes against the `transaction` client.

| Property | Value |
| --- | --- |
| Skill ID | `transaction-redo` |
| Service | `TransactionService` |
| Method | `Redo` |
| Transport | Unary (unary) |
| Domain | transaction |
| Request type | `RedoRequest` |
| Response type | `RedoResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `steps` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `RedoRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("transaction-redo");
const result = await skill.execute(ctx, {
  context: {},
  steps: 0,
});
```

## Related Skills

Browse other **transaction** skills in the [`transaction/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/transaction/redo

# Or install the full runtime package
npm install @huaqiu/hqeda
```

