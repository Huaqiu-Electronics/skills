---
name: project-open-project
metadata:
  category: project
  service: ProjectService
  method: OpenProject
  rpcKind: unary
description: >-
  Opens a project into the current HQ EDA editor process.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: OpenProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Open Project

Opens a project into the current HQ EDA editor process.

## Overview

This skill provides access to the **`ProjectService.OpenProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-open-project` |
| Service | `ProjectService` |
| Method | `OpenProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `OpenProjectRequest` |
| Response type | `OpenProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `EditorContext` | no | no | — |
| `location` | `string` | yes | no | File path, URI, object-store key, etc. |

## Usage Examples

### open a new project and save it

_Source: `integration.test.ts`_

```json
{
  "location": "poc-new-project"
}
```

### open a new project and save it

_Source: `integration.test.ts`_

```json
{
  "location": "poc-new-project"
}
```

### skill: open project

_Source: `open-project.test.ts`_

```json
{
  "location": "demo-project"
}
```

### opens a new project by location

_Source: `open-project.test.ts`_

```json
{
  "location": "poc-new-project"
}
```

### saves an open project

_Source: `open-project.test.ts`_

```json
{
  "location": "poc-new-project"
}
```

### toJson produces LLM-friendly JSON output

_Source: `open-project.test.ts`_

```json
{
  "location": "poc-skill-project"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `OpenProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("project-open-project");
const result = await skill.execute(ctx, {
  context: {},
  location: "<string>",
});
```

## Related Skills

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/open-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

