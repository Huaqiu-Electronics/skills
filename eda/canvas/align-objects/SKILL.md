---
name: canvas-align-objects
metadata:
  category: canvas
  service: CanvasOpsService
  method: AlignObjects
  rpcKind: unary
description: >-
  transform
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: AlignModeRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Align Objects

transform

## Overview

This skill provides access to the **`CanvasOpsService.AlignObjects`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-align-objects` |
| Service | `CanvasOpsService` |
| Method | `AlignObjects` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `AlignModeRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `mode` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `AlignModeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-align-objects");
const result = await skill.execute(ctx, {
  context: {},
  mode: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/align-objects

# Or install the full runtime package
npm install @huaqiu/hqeda
```

