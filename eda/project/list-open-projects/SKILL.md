---
name: project-list-open-projects
metadata:
  category: project
  service: ProjectService
  method: ListOpenProjects
  rpcKind: unary
description: >-
  Returns all projects currently opened in this HQ EDA process.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ListOpenProjectsRequestSchema
  namespace: HqServicesV1ProjectService
---

# List Open Projects

Returns all projects currently opened in this HQ EDA process.

## Overview

This skill provides access to the **`ProjectService.ListOpenProjects`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-list-open-projects` |
| Service | `ProjectService` |
| Method | `ListOpenProjects` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `ListOpenProjectsRequest` |
| Response type | `ListOpenProjectsResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `EditorContext` | no | no | — |

## Usage Examples

### lists open projects via editor context

_Source: `discover-active-project.test.ts`_

```json
{
  "context": "<createEditorContext>"
}
```

### toJson produces LLM-friendly JSON output

_Source: `discover-active-project.test.ts`_

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

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ListOpenProjectsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-list-open-projects");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/list-open-projects

# Or install the full runtime package
npm install @huaqiu/hqeda
```

