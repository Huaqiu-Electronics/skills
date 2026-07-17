---
name: bom-get-bom
metadata:
  category: bom
  service: EdaBomService
  method: GetBom
  rpcKind: unary
description: >-
  Get full BOM snapshot from current schematic state
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - bom
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetBomRequestSchema
  namespace: HqFabV1GetEdaBom
---

# Get Bom

Get full BOM snapshot from current schematic state

## Overview

This skill provides access to the **`EdaBomService.GetBom`** RPC method on the Huaqiu EDA engine. It is part of the **bom** domain and executes against the `edaBom` client.

| Property | Value |
| --- | --- |
| Skill ID | `bom-get-bom` |
| Service | `EdaBomService` |
| Method | `GetBom` |
| Transport | Unary (unary) |
| Domain | bom |
| Request type | `GetBomRequest` |
| Response type | `EdaBom` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `projectId` | `string` | yes | no | — |

## Usage Examples

### retrieves BOM for a discovered project

_Source: `bom.test.ts`_

```json
{
  "projectId": "<projectId>"
}
```

### BOM rows contain references

_Source: `bom.test.ts`_

```json
{
  "projectId": "<projectId>"
}
```

### toJson produces LLM-friendly JSON output

_Source: `bom.test.ts`_

```json
{
  "projectId": "<projectId>"
}
```

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{
  "projectId": "<BinaryExpression>"
}
```

### get BOM for a discovered project

_Source: `integration.test.ts`_

```json
{
  "projectId": "<projectId>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetBomRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("bom-get-bom");
const result = await skill.execute(ctx, {
  projectId: "<string>",
});
```

## Related Skills

Browse other **bom** skills in the [`bom/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/bom/get-bom

# Or install the full runtime package
npm install @huaqiu/hqeda
```

