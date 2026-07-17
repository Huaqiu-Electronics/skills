---
name: canvas-zoom-area-by-points
metadata:
  category: canvas
  service: CanvasOpsService
  method: ZoomAreaByPoints
  rpcKind: unary
description: >-
  Zoom Area By Points via CanvasOpsService.ZoomAreaByPoints
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ZoomAreaPointsRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Zoom Area By Points

Zoom Area By Points via CanvasOpsService.ZoomAreaByPoints

## Overview

This skill provides access to the **`CanvasOpsService.ZoomAreaByPoints`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-zoom-area-by-points` |
| Service | `CanvasOpsService` |
| Method | `ZoomAreaByPoints` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `ZoomAreaPointsRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `start` | `Vector2i64` | no | no | — |
| `end` | `Vector2i64` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ZoomAreaPointsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-zoom-area-by-points");
const result = await skill.execute(ctx, {
  context: {},
  start: {},
  end: {},
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/zoom-area-by-points

# Or install the full runtime package
npm install @huaqiu/hqeda
```

