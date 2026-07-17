---
name: canvas-zoom-area-by-double-box
metadata:
  category: canvas
  service: CanvasOpsService
  method: ZoomAreaByDoubleBox
  rpcKind: unary
description: >-
  Zoom Area By Double Box via CanvasOpsService.ZoomAreaByDoubleBox
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ZoomAreaDoubleBoxRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Zoom Area By Double Box

Zoom Area By Double Box via CanvasOpsService.ZoomAreaByDoubleBox

## Overview

This skill provides access to the **`CanvasOpsService.ZoomAreaByDoubleBox`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-zoom-area-by-double-box` |
| Service | `CanvasOpsService` |
| Method | `ZoomAreaByDoubleBox` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `ZoomAreaDoubleBoxRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `left` | `number` | yes | no | — |
| `top` | `number` | yes | no | — |
| `right` | `number` | yes | no | — |
| `bottom` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ZoomAreaDoubleBoxRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-zoom-area-by-double-box");
const result = await skill.execute(ctx, {
  context: {},
  left: 0,
  top: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/zoom-area-by-double-box

# Or install the full runtime package
npm install @huaqiu/hqeda
```

