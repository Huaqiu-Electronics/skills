---
name: obj-place-add-free-line-segment
metadata:
  category: obj-place
  service: ObjPlaceService
  method: AddFreeLineSegment
  rpcKind: unary
description: >-
  Add Free Line Segment via ObjPlaceService.AddFreeLineSegment
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: AddFreeLineSegmentRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Add Free Line Segment

Add Free Line Segment via ObjPlaceService.AddFreeLineSegment

## Overview

This skill provides access to the **`ObjPlaceService.AddFreeLineSegment`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-add-free-line-segment` |
| Service | `ObjPlaceService` |
| Method | `AddFreeLineSegment` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `AddFreeLineSegmentRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `geometry` | `Line2i64` | no | no | — |
| `snapToGrid` | `boolean` | yes | no | — |
| `orthoConstrain` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `AddFreeLineSegmentRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-add-free-line-segment");
const result = await skill.execute(ctx, {
  context: {},
  geometry: {},
  snapToGrid: false,
});
```

## Related Skills

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/add-free-line-segment

# Or install the full runtime package
npm install @huaqiu/hqeda
```

