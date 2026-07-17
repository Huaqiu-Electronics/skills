---
name: canvas-get-align-type
metadata:
  category: canvas
  service: CanvasOpsService
  method: GetAlignType
  rpcKind: unary
description: >-
  Get Align Type via CanvasOpsService.GetAlignType
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetAlignTypeRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Get Align Type

Get Align Type via CanvasOpsService.GetAlignType

## Overview

This skill provides access to the **`CanvasOpsService.GetAlignType`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-get-align-type` |
| Service | `CanvasOpsService` |
| Method | `GetAlignType` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `GetAlignTypeRequest` |
| Response type | `GetAlignTypeResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `alignStyle` | `number` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetAlignTypeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-get-align-type");
const result = await skill.execute(ctx, {
  context: {},
  alignStyle: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/get-align-type

# Or install the full runtime package
npm install @huaqiu/hqeda
```

