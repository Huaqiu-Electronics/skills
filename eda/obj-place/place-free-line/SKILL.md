---
name: obj-place-place-free-line
metadata:
  category: obj-place
  service: ObjPlaceService
  method: PlaceFreeLine
  rpcKind: unary
description: >-
  free line
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: PlaceFreeLineRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Place Free Line

free line

## Overview

This skill provides access to the **`ObjPlaceService.PlaceFreeLine`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-place-free-line` |
| Service | `ObjPlaceService` |
| Method | `PlaceFreeLine` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `PlaceFreeLineRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `geometry` | `Line2i64` | no | no | — |
| `snapToGrid` | `boolean` | yes | no | — |
| `orthoConstrain` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlaceFreeLineRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-place-free-line");
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
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/place-free-line

# Or install the full runtime package
npm install @huaqiu/hqeda
```

