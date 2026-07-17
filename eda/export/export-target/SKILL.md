---
name: export-export-target
metadata:
  category: export
  service: ExportService
  method: ExportTarget
  rpcKind: unary
description: >-
  Export Target via ExportService.ExportTarget
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - export
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ExportTargetRequestSchema
  namespace: HqServicesV1ExportService
---

# Export Target

Export Target via ExportService.ExportTarget

## Overview

This skill provides access to the **`ExportService.ExportTarget`** RPC method on the Huaqiu EDA engine. It is part of the **export** domain and executes against the `export` client.

| Property | Value |
| --- | --- |
| Skill ID | `export-export-target` |
| Service | `ExportService` |
| Method | `ExportTarget` |
| Transport | Unary (unary) |
| Domain | export |
| Request type | `ExportTargetRequest` |
| Response type | `ExportTargetResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `targetFormat` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ExportTargetRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("export-export-target");
const result = await skill.execute(ctx, {
  context: {},
  targetFormat: "<string>",
});
```

## Related Skills

Browse other **export** skills in the [`export/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/export/export-target

# Or install the full runtime package
npm install @huaqiu/hqeda
```

