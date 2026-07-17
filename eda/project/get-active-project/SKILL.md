---
name: project-get-active-project
metadata:
  category: project
  service: ProjectService
  method: GetActiveProject
  rpcKind: unary
description: >-
  Returns the project currently active in the editor UI.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: GetActiveProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Get Active Project

Returns the project currently active in the editor UI.

## Overview

This skill provides access to the **`ProjectService.GetActiveProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-get-active-project` |
| Service | `ProjectService` |
| Method | `GetActiveProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `GetActiveProjectRequest` |
| Response type | `GetActiveProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `EditorContext` | no | no | — |

## Usage Examples

### getActiveProject returns the active project

_Source: `discover-active-project.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

### list open projects and verify project metadata

_Source: `integration.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetActiveProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-get-active-project");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/get-active-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

