---
name: project-close-project
metadata:
  category: project
  service: ProjectService
  method: CloseProject
  rpcKind: unary
description: >-
  Closes an opened project.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: CloseProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Close Project

Closes an opened project.

## Overview

This skill provides access to the **`ProjectService.CloseProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-close-project` |
| Service | `ProjectService` |
| Method | `CloseProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `CloseProjectRequest` |
| Response type | `CloseProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `requireSaved` | `boolean` | yes | no | Refuse to close if the project contains unsaved changes. |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `CloseProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-close-project");
const result = await skill.execute(ctx, {
  context: {},
  requireSaved: false,
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/close-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

