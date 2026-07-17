---
name: runtime-execute-commands
metadata:
  category: runtime
  service: RuntimeService
  method: ExecuteCommands
  rpcKind: unary
description: >-
  Execute Commands via RuntimeService.ExecuteCommands
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - runtime
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ExecuteCommandsRequestSchema
  namespace: HqRuntimeV1Command
---

# Execute Commands

Execute Commands via RuntimeService.ExecuteCommands

## Overview

This skill provides access to the **`RuntimeService.ExecuteCommands`** RPC method on the Huaqiu EDA engine. It is part of the **runtime** domain and executes against the `runtime` client.

| Property | Value |
| --- | --- |
| Skill ID | `runtime-execute-commands` |
| Service | `RuntimeService` |
| Method | `ExecuteCommands` |
| Transport | Unary (unary) |
| Domain | runtime |
| Request type | `ExecuteCommandsRequest` |
| Response type | `ExecuteCommandsResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `commands` | `Command[]` | no | yes | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ExecuteCommandsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("runtime-execute-commands");
const result = await skill.execute(ctx, {
  context: {},
  commands: [],
});
```

## Related Skills

Browse other **runtime** skills in the [`runtime/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/runtime/execute-commands

# Or install the full runtime package
npm install @huaqiu/hqeda
```

