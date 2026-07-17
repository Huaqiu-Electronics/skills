---
name: placement-place-part
metadata:
  category: placement
  service: ComponentPlaceService
  method: PlacePart
  rpcKind: unary
description: >-
  part
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: PlacePartRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Place Part

part

## Overview

This skill provides access to the **`ComponentPlaceService.PlacePart`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-place-part` |
| Service | `ComponentPlaceService` |
| Method | `PlacePart` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `PlacePartRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |
| `jsonPartInst` | `string` | yes | no | — |
| `jsonPart` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlacePartRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-place-part");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
  jsonPartInst: "<string>",
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/place-part

# Or install the full runtime package
npm install @huaqiu/hqeda
```

