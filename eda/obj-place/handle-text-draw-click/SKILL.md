---
name: obj-place-handle-text-draw-click
metadata:
  category: obj-place
  service: ObjPlaceService
  method: HandleTextDrawClick
  rpcKind: unary
description: >-
  Handle Text Draw Click via ObjPlaceService.HandleTextDrawClick
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: LocalClickRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Handle Text Draw Click

Handle Text Draw Click via ObjPlaceService.HandleTextDrawClick

## Overview

This skill provides access to the **`ObjPlaceService.HandleTextDrawClick`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-handle-text-draw-click` |
| Service | `ObjPlaceService` |
| Method | `HandleTextDrawClick` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `LocalClickRequest` |
| Response type | `HandleTextDrawClickResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `LocalClickRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-handle-text-draw-click");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
});
```

## Related Skills

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/handle-text-draw-click

# Or install the full runtime package
npm install @huaqiu/hqeda
```

