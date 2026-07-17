---
name: canvas-on-canvas-escape
metadata:
  category: canvas
  service: CanvasOpsService
  method: OnCanvasEscape
  rpcKind: unary
description: >-
  state
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: OnCanvasEscapeRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# On Canvas Escape

state

## Overview

This skill provides access to the **`CanvasOpsService.OnCanvasEscape`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-on-canvas-escape` |
| Service | `CanvasOpsService` |
| Method | `OnCanvasEscape` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `OnCanvasEscapeRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `needClearSelect` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `OnCanvasEscapeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-on-canvas-escape");
const result = await skill.execute(ctx, {
  context: {},
  needClearSelect: false,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/on-canvas-escape

# Or install the full runtime package
npm install @huaqiu/hqeda
```

