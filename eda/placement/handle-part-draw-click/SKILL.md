---
name: placement-handle-part-draw-click
metadata:
  category: placement
  service: ComponentPlaceService
  method: HandlePartDrawClick
  rpcKind: unary
description: >-
  Handle Part Draw Click via ComponentPlaceService.HandlePartDrawClick
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: HandlePartDrawClickRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Handle Part Draw Click

Handle Part Draw Click via ComponentPlaceService.HandlePartDrawClick

## Overview

This skill provides access to the **`ComponentPlaceService.HandlePartDrawClick`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-handle-part-draw-click` |
| Service | `ComponentPlaceService` |
| Method | `HandlePartDrawClick` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `HandlePartDrawClickRequest` |
| Response type | `HandlePartDrawClickResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `windowX` | `number` | yes | no | — |
| `windowY` | `number` | yes | no | — |
| `localPos` | `Vector2i64` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `HandlePartDrawClickRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-handle-part-draw-click");
const result = await skill.execute(ctx, {
  context: {},
  windowX: 0,
  windowY: 0,
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/handle-part-draw-click

# Or install the full runtime package
npm install @huaqiu/hqeda
```

