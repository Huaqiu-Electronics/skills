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
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
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

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `UndoRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("transaction-undo");
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
npx skills add Huaqiu-Electronics/skills --path eda/transaction/undo

# Or install the full runtime package
npm install @huaqiu/hqeda
```

