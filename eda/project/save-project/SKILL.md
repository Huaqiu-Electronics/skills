---
name: project-save-project
metadata:
  category: project
  service: ProjectService
  method: SaveProject
  rpcKind: unary
description: >-
  Persists an opened project.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SaveProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Save Project

Persists an opened project.

## Overview

This skill provides access to the **`ProjectService.SaveProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-save-project` |
| Service | `ProjectService` |
| Method | `SaveProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `SaveProjectRequest` |
| Response type | `SaveProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `destination` | `string` | no | no | Optional alternative save destination.
Empty means "save in place". |

## Usage Examples

### open a new project and save it

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### saves an open project

_Source: `open-project.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SaveProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-save-project");
const result = await skill.execute(ctx, {
  context: {},
  destination: "<string>",
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/save-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

