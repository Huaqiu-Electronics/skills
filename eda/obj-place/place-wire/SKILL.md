---
name: obj-place-place-wire
metadata:
  category: obj-place
  service: ObjPlaceService
  method: PlaceWire
  rpcKind: unary
description: >-
  Place Wire via ObjPlaceService.PlaceWire
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: PlaceLineRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Place Wire

Place Wire via ObjPlaceService.PlaceWire

## Overview

This skill provides access to the **`ObjPlaceService.PlaceWire`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-place-wire` |
| Service | `ObjPlaceService` |
| Method | `PlaceWire` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `PlaceLineRequest` |
| Response type | `PlaceLineResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `geometry` | `Line2i64` | no | no | — |
| `snapToGrid` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlaceLineRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-place-wire");
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
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/place-wire

# Or install the full runtime package
npm install @huaqiu/hqeda
```

