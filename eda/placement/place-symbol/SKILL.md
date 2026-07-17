---
name: placement-place-symbol
metadata:
  category: placement
  service: ComponentPlaceService
  method: PlaceSymbol
  rpcKind: unary
description: >-
  symbol
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: PlaceSymbolRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Place Symbol

symbol

## Overview

This skill provides access to the **`ComponentPlaceService.PlaceSymbol`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-place-symbol` |
| Service | `ComponentPlaceService` |
| Method | `PlaceSymbol` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `PlaceSymbolRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `localPos` | `Vector2i64` | no | no | — |
| `jsonSymbolInst` | `string` | yes | no | — |
| `jsonSymbol` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `PlaceSymbolRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-place-symbol");
const result = await skill.execute(ctx, {
  context: {},
  localPos: {},
  jsonSymbolInst: "<string>",
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/place-symbol

# Or install the full runtime package
npm install @huaqiu/hqeda
```

