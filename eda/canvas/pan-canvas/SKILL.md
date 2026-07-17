---
name: canvas-pan-canvas
metadata:
  category: canvas
  service: CanvasOpsService
  method: PanCanvas
  rpcKind: unary
description: >-
  viewport
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: PanCanvasRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Pan Canvas

viewport

## Overview

This skill provides access to the **`CanvasOpsService.PanCanvas`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-pan-canvas` |
| Service | `CanvasOpsService` |
| Method | `PanCanvas` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `PanCanvasRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `deltaX` | `number` | yes | no | — |
| `deltaY` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PanCanvasRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-pan-canvas");
const result = await skill.execute(ctx, {
  context: {},
  deltaX: 0,
  deltaY: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/pan-canvas

# Or install the full runtime package
npm install @huaqiu/hqeda
```

