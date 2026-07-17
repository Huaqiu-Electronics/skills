---
name: selection-clear-selection
metadata:
  category: selection
  service: SelectionService
  method: ClearSelection
  rpcKind: unary
description: >-
  Clear Selection via SelectionService.ClearSelection
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ClearSelectionRequestSchema
  namespace: HqServicesV1SelectionService
---

# Clear Selection

Clear Selection via SelectionService.ClearSelection

## Overview

This skill provides access to the **`SelectionService.ClearSelection`** RPC method on the Huaqiu EDA engine. It is part of the **selection** domain and executes against the `selection` client.

| Property | Value |
| --- | --- |
| Skill ID | `selection-clear-selection` |
| Service | `SelectionService` |
| Method | `ClearSelection` |
| Transport | Unary (unary) |
| Domain | selection |
| Request type | `ClearSelectionRequest` |
| Response type | `ClearSelectionResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ClearSelectionRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("selection-clear-selection");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **selection** skills in the [`selection/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/selection/clear-selection

# Or install the full runtime package
npm install @huaqiu/hqeda
```

