---
name: export-export-bom
metadata:
  category: export
  service: ExportService
  method: ExportBOM
  rpcKind: unary
description: >-
  Export Bom via ExportService.ExportBOM
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - export
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ExportBOMRequestSchema
  namespace: HqServicesV1ExportService
---

# Export Bom

Export Bom via ExportService.ExportBOM

## Overview

This skill provides access to the **`ExportService.ExportBOM`** RPC method on the Huaqiu EDA engine. It is part of the **export** domain and executes against the `export` client.

| Property | Value |
| --- | --- |
| Skill ID | `export-export-bom` |
| Service | `ExportService` |
| Method | `ExportBOM` |
| Transport | Unary (unary) |
| Domain | export |
| Request type | `ExportBOMRequest` |
| Response type | `ExportBOMResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ExportBOMRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("export-export-bom");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **export** skills in the [`export/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/export/export-bom

# Or install the full runtime package
npm install @huaqiu/hqeda
```

