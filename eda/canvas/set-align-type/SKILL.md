---
name: canvas-set-align-type
metadata:
  category: canvas
  service: CanvasOpsService
  method: SetAlignType
  rpcKind: unary
description: >-
  grid align
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SetAlignTypeRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Set Align Type

grid align

## Overview

This skill provides access to the **`CanvasOpsService.SetAlignType`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-set-align-type` |
| Service | `CanvasOpsService` |
| Method | `SetAlignType` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `SetAlignTypeRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `alignType` | `number` | yes | no | — |
| `alignStyle` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetAlignTypeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-set-align-type");
const result = await skill.execute(ctx, {
  context: {},
  alignType: 0,
  alignStyle: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/set-align-type

# Or install the full runtime package
npm install @huaqiu/hqeda
```

