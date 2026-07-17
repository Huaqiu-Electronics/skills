---
name: obj-place-place-image
metadata:
  category: obj-place
  service: ObjPlaceService
  method: PlaceImage
  rpcKind: unary
description: >-
  image
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: PlaceImageRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Place Image

image

## Overview

This skill provides access to the **`ObjPlaceService.PlaceImage`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-place-image` |
| Service | `ObjPlaceService` |
| Method | `PlaceImage` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `PlaceImageRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |
| `imagePath` | `string` | yes | no | — |
| `snapToGrid` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlaceImageRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-place-image");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
  imagePath: "<string>",
});
```

## Related Skills

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/place-image

# Or install the full runtime package
npm install @huaqiu/hqeda
```

