---
name: placement-place-block
metadata:
  category: placement
  service: ComponentPlaceService
  method: PlaceBlock
  rpcKind: unary
description: >-
  block
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: BoxPlaceRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Place Block

block

## Overview

This skill provides access to the **`ComponentPlaceService.PlaceBlock`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-place-block` |
| Service | `ComponentPlaceService` |
| Method | `PlaceBlock` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `BoxPlaceRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `box` | `Box2i64` | no | no | — |
| `snapToGrid` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `BoxPlaceRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-place-block");
const result = await skill.execute(ctx, {
  context: {},
  box: {},
  snapToGrid: false,
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/place-block

# Or install the full runtime package
npm install @huaqiu/hqeda
```

