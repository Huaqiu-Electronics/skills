---
name: obj-place-place-text
metadata:
  category: obj-place
  service: ObjPlaceService
  method: PlaceText
  rpcKind: unary
description: >-
  text
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - obj-place
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ObjDataPlaceRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Place Text

text

## Overview

This skill provides access to the **`ObjPlaceService.PlaceText`** RPC method on the Huaqiu EDA engine. It is part of the **obj-place** domain and executes against the `objPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `obj-place-place-text` |
| Service | `ObjPlaceService` |
| Method | `PlaceText` |
| Transport | Unary (unary) |
| Domain | obj-place |
| Request type | `ObjDataPlaceRequest` |
| Response type | `ObjectPlaceResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `objDataJson` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ObjDataPlaceRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("obj-place-place-text");
const result = await skill.execute(ctx, {
  context: {},
  objDataJson: "<string>",
});
```

## Related Skills

Browse other **obj-place** skills in the [`obj-place/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/obj-place/place-text

# Or install the full runtime package
npm install @huaqiu/hqeda
```

