---
name: placement-handle-symbol-draw-click
metadata:
  category: placement
  service: ComponentPlaceService
  method: HandleSymbolDrawClick
  rpcKind: unary
description: >-
  Handle Symbol Draw Click via ComponentPlaceService.HandleSymbolDrawClick
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: HandleSymbolDrawClickRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Handle Symbol Draw Click

Handle Symbol Draw Click via ComponentPlaceService.HandleSymbolDrawClick

## Overview

This skill provides access to the **`ComponentPlaceService.HandleSymbolDrawClick`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-handle-symbol-draw-click` |
| Service | `ComponentPlaceService` |
| Method | `HandleSymbolDrawClick` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `HandleSymbolDrawClickRequest` |
| Response type | `HandleSymbolDrawClickResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `windowX` | `number` | yes | no | — |
| `windowY` | `number` | yes | no | — |
| `localPos` | `Vector2i64` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `HandleSymbolDrawClickRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-handle-symbol-draw-click");
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
npx skills add Huaqiu-Electronics/skills --path eda/placement/handle-symbol-draw-click

# Or install the full runtime package
npm install @huaqiu/hqeda
```

