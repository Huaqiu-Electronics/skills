---
name: selection-get-selection
metadata:
  category: selection
  service: SelectionService
  method: GetSelection
  rpcKind: unary
description: >-
  Get Selection via SelectionService.GetSelection
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: GetSelectionRequestSchema
  namespace: HqServicesV1SelectionService
---

# Get Selection

Get Selection via SelectionService.GetSelection

## Overview

This skill provides access to the **`SelectionService.GetSelection`** RPC method on the Huaqiu EDA engine. It is part of the **selection** domain and executes against the `selection` client.

| Property | Value |
| --- | --- |
| Skill ID | `selection-get-selection` |
| Service | `SelectionService` |
| Method | `GetSelection` |
| Transport | Unary (unary) |
| Domain | selection |
| Request type | `GetSelectionRequest` |
| Response type | `GetSelectionResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `typeFilter` | `string[]` | no | yes | Optional filter.  If non-empty, the server returns only ids whose
domain type is listed.  This lets callers ask for "just symbols"
or "just nets" without post-processing. |

## Usage Examples

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

### set selection on a discovered project

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### sets selection and retrieves it back

_Source: `selection.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### toJson produces LLM-friendly JSON output

_Source: `selection.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetSelectionRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("selection-get-selection");
const result = await skill.execute(ctx, {
  context: {},
  typeFilter: [],
});
```

## Related Skills

Browse other **selection** skills in the [`selection/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/selection/get-selection

# Or install the full runtime package
npm install @huaqiu/hqeda
```

