---
name: canvas-rotate-objects
metadata:
  category: canvas
  service: CanvasOpsService
  method: RotateObjects
  rpcKind: unary
description: >-
  Rotate Objects via CanvasOpsService.RotateObjects
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

# Rotate Objects

Rotate Objects via CanvasOpsService.RotateObjects

## Overview

This skill provides access to the **`CanvasOpsService.RotateObjects`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-rotate-objects` |
| Service | `CanvasOpsService` |
| Method | `RotateObjects` |
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

const skill = getSkill("canvas-rotate-objects");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/rotate-objects

# Or install the full runtime package
npm install @huaqiu/hqeda
```

