---
name: placement-set-net-alias-attach-obj
metadata:
  category: placement
  service: ComponentPlaceService
  method: SetNetAliasAttachObj
  rpcKind: unary
description: >-
  net alias attach
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SetNetAliasAttachObjRequestSchema
  namespace: HqServicesV1ComponentPlaceService
---

# Set Net Alias Attach Obj

net alias attach

## Overview

This skill provides access to the **`ComponentPlaceService.SetNetAliasAttachObj`** RPC method on the Huaqiu EDA engine. It is part of the **placement** domain and executes against the `componentPlace` client.

| Property | Value |
| --- | --- |
| Skill ID | `placement-set-net-alias-attach-obj` |
| Service | `ComponentPlaceService` |
| Method | `SetNetAliasAttachObj` |
| Transport | Unary (unary) |
| Domain | placement |
| Request type | `SetNetAliasAttachObjRequest` |
| Response type | `SetNetAliasAttachObjResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `objectId` | `bigint` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetNetAliasAttachObjRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("placement-set-net-alias-attach-obj");
const result = await skill.execute(ctx, {
  context: {},
  objectId: 0,
});
```

## Related Skills

Browse other **placement** skills in the [`placement/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/placement/set-net-alias-attach-obj

# Or install the full runtime package
npm install @huaqiu/hqeda
```

