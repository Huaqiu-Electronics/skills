---
name: canvas-move-selected-objs
metadata:
  category: canvas
  service: CanvasOpsService
  method: MoveSelectedObjs
  rpcKind: unary
description: >-
  Move Selected Objs via CanvasOpsService.MoveSelectedObjs
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: MoveSelectedObjsRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Move Selected Objs

Move Selected Objs via CanvasOpsService.MoveSelectedObjs

## Overview

This skill provides access to the **`CanvasOpsService.MoveSelectedObjs`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-move-selected-objs` |
| Service | `CanvasOpsService` |
| Method | `MoveSelectedObjs` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `MoveSelectedObjsRequest` |
| Response type | `BoolResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `windowX` | `number` | yes | no | — |
| `windowY` | `number` | yes | no | — |
| `prevWindowX` | `number` | yes | no | — |
| `prevWindowY` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `MoveSelectedObjsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-move-selected-objs");
const result = await skill.execute(ctx, {
  context: {},
  windowX: 0,
  windowY: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/move-selected-objs

# Or install the full runtime package
npm install @huaqiu/hqeda
```

