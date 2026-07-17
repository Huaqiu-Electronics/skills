---
name: project-get-project
metadata:
  category: project
  service: ProjectService
  method: GetProject
  rpcKind: unary
description: >-
  Returns one opened project.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: GetProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Get Project

Returns one opened project.

## Overview

This skill provides access to the **`ProjectService.GetProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-get-project` |
| Service | `ProjectService` |
| Method | `GetProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `GetProjectRequest` |
| Response type | `GetProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## Usage Examples

### getProject returns details for discovered project

_Source: `discover-active-project.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### list open projects and verify project metadata

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-get-project");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/get-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

