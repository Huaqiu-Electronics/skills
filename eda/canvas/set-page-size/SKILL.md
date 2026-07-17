---
name: canvas-set-page-size
metadata:
  category: canvas
  service: CanvasOpsService
  method: SetPageSize
  rpcKind: unary
description: >-
  page
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: SetPageSizeRequestSchema
  namespace: HqServicesV1CanvasOpsService
---

# Set Page Size

page

## Overview

This skill provides access to the **`CanvasOpsService.SetPageSize`** RPC method on the Huaqiu EDA engine. It is part of the **canvas** domain and executes against the `canvasOps` client.

| Property | Value |
| --- | --- |
| Skill ID | `canvas-set-page-size` |
| Service | `CanvasOpsService` |
| Method | `SetPageSize` |
| Transport | Unary (unary) |
| Domain | canvas |
| Request type | `SetPageSizeRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `ltX` | `number` | yes | no | — |
| `ltY` | `number` | yes | no | — |
| `rbX` | `number` | yes | no | — |
| `rbY` | `number` | yes | no | — |
| `showBorder` | `boolean` | yes | no | — |
| `pageSizeLabel` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetPageSizeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("canvas-set-page-size");
const result = await skill.execute(ctx, {
  context: {},
  ltX: 0,
  ltY: 0,
});
```

## Related Skills

Browse other **canvas** skills in the [`canvas/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/canvas/set-page-size

# Or install the full runtime package
npm install @huaqiu/hqeda
```

