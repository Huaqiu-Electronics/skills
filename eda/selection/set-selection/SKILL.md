---
name: selection-set-selection
metadata:
  category: selection
  service: SelectionService
  method: SetSelection
  rpcKind: unary
description: >-
  Set Selection via SelectionService.SetSelection
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SetSelectionRequestSchema
  namespace: HqServicesV1SelectionService
---

# Set Selection

Set Selection via SelectionService.SetSelection

## Overview

This skill provides access to the **`SelectionService.SetSelection`** RPC method on the Huaqiu EDA engine. It is part of the **selection** domain and executes against the `selection` client.

| Property | Value |
| --- | --- |
| Skill ID | `selection-set-selection` |
| Service | `SelectionService` |
| Method | `SetSelection` |
| Transport | Unary (unary) |
| Domain | selection |
| Request type | `SetSelectionRequest` |
| Response type | `SetSelectionResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `entityIds` | `string[]` | no | yes | Replaces the current selection set. |

## Usage Examples

### set selection on a discovered project

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>",
  "entityIds": [
    "<targetId>"
  ]
}
```

### sets selection and retrieves it back

_Source: `selection.test.ts`_

```json
{
  "context": "<createProjectContext>",
  "entityIds": [
    "<targetId>"
  ]
}
```

### toJson produces LLM-friendly JSON output

_Source: `selection.test.ts`_

```json
{
  "context": "<createProjectContext>",
  "entityIds": [
    "<targetId>"
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetSelectionRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("selection-set-selection");
const result = await skill.execute(ctx, {
  context: {},
  entityIds: [],
});
```

## Related Skills

Browse other **selection** skills in the [`selection/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/selection/set-selection

# Or install the full runtime package
npm install @huaqiu/hqeda
```

