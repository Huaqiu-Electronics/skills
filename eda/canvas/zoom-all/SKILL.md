---
name: canvas-zoom-all
metadata:
  category: canvas
  service: CanvasOpsService
  method: ZoomAll
  rpcKind: unary
description: >-
  Zoom All via CanvasOpsService.ZoomAll
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: CanvasContextRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Zoom All

Zoom All via CanvasOpsService.ZoomAll

## Overview

This skill provides access to the **`CanvasOpsService.ZoomAll`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-zoom-all` |
| Service | `CanvasOpsService` |
| Method | `ZoomAll` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `CanvasContextRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `CanvasContextRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-zoom-all");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/zoom-all

# Or install the full runtime package
npm install @huaqiu/hqeda
```

