---
name: placement-cancel-block-draw
metadata:
  category: placement
  service: ComponentPlaceService
  method: CancelBlockDraw
  rpcKind: unary
description: >-
  Cancel Block Draw via ComponentPlaceService.CancelBlockDraw
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ContextOnlyRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Cancel Block Draw

Cancel Block Draw via ComponentPlaceService.CancelBlockDraw

## Overview

This skill provides access to the **`ComponentPlaceService.CancelBlockDraw`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-cancel-block-draw` |
| Service | `ComponentPlaceService` |
| Method | `CancelBlockDraw` |
| Transport | Unary (unary) |
| Domain | placement |
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

const skill = getSkill("placement-cancel-block-draw");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/cancel-block-draw

# Or install the full runtime package
npm install @huaqiu/hqeda
```

