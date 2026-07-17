---
name: obj-place-cancel-free-line-draw
metadata:
  category: obj-place
  service: ObjPlaceService
  method: CancelFreeLineDraw
  rpcKind: unary
description: >-
  Cancel Free Line Draw via ObjPlaceService.CancelFreeLineDraw
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ContextOnlyRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Cancel Free Line Draw

Cancel Free Line Draw via ObjPlaceService.CancelFreeLineDraw

## Overview

This skill provides access to the **`ObjPlaceService.CancelFreeLineDraw`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-cancel-free-line-draw` |
| Service | `ObjPlaceService` |
| Method | `CancelFreeLineDraw` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `ContextOnlyRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ContextOnlyRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-cancel-free-line-draw");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/cancel-free-line-draw

# Or install the full runtime package
npm install @huaqiu/hqeda
```

