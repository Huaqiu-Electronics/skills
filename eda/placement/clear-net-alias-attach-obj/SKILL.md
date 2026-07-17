---
name: placement-clear-net-alias-attach-obj
metadata:
  category: placement
  service: ComponentPlaceService
  method: ClearNetAliasAttachObj
  rpcKind: unary
description: >-
  Clear Net Alias Attach Obj via ComponentPlaceService.ClearNetAliasAttachObj
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ContextOnlyRequestSchema
  namespace: HqServicesV1ObjPlaceService
---

# Clear Net Alias Attach Obj

Clear Net Alias Attach Obj via ComponentPlaceService.ClearNetAliasAttachObj

## Overview

This skill provides access to the **`ComponentPlaceService.ClearNetAliasAttachObj`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-clear-net-alias-attach-obj` |
| Service | `ComponentPlaceService` |
| Method | `ClearNetAliasAttachObj` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `ContextOnlyRequest` |
| Response type | `SuccessResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ContextOnlyRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-clear-net-alias-attach-obj");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/clear-net-alias-attach-obj

# Or install the full runtime package
npm install @huaqiu/hqeda
```

