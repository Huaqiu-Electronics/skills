---
name: obj-place-add-line
metadata:
  category: obj-place
  service: ObjPlaceService
  method: AddLine
  rpcKind: unary
description: >-
  Add Line via ObjPlaceService.AddLine
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: AddLineRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Add Line

Add Line via ObjPlaceService.AddLine

## Overview

This skill provides access to the **`ObjPlaceService.AddLine`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-add-line` |
| Service | `ObjPlaceService` |
| Method | `AddLine` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `AddLineRequest` |
| Response type | `AddLineResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `geometry` | `Line2i64` | no | no | — |
| `snapToGrid` | `boolean` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `AddLineRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-add-line");
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
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/add-line

# Or install the full runtime package
npm install @huaqiu/hqeda
```

