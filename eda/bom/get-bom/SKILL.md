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

## Response

Returns a `EdaBom` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `projectId` | `string` | no | Project / schematic identifier |
| `revision` | `string` | no | Versioning for SaaS sync |
| `rows` | `EdaBomRow[]` | yes | BOM rows |

## Usage Examples

### retrieves BOM for a discovered project

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

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "projectId": "<string>",
  "revision": "<string>",
  "rows": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetBomRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("bom-get-bom");
const result = await skill.execute(ctx, {
  projectId: "<string>",
});

// Always use toJsonString() to serialize protobuf messages —
// never use JSON.stringify() directly (it fails on BigInt fields).
console.log(toJsonString(result, { prettySpaces: 2 }));
```

## Serializing Protobuf Messages

Skill responses are protobuf message objects. **Do NOT use `JSON.stringify()` directly** — it will throw `Do not know how to serialize a BigInt` on 64-bit integer fields and produce empty objects for oneof ADT fields.

Instead, use the `toJson()` or `toJsonString()` helpers:

```typescript
import { toJson, toJsonString } from "@huaqiu/hqeda";

// Plain JSON object (BigInts converted to strings)
const jsonObj = toJson(result);

// Formatted JSON string
const jsonStr = toJsonString(result, { prettySpaces: 2 });

// Include zero-valued fields in output
const full = toJsonString(result, { alwaysEmitImplicit: true });
```

These helpers correctly handle:

- **BigInt fields** — converted to strings (protobuf JSON convention)
- **oneof fields** — serialized as `{ case, value }` ADT objects
- **Well-known types** — `Timestamp` → ISO string, `Duration` → `"Ns"` format, `Struct` → plain object
- **bytes fields** — base64-encoded strings
- **Zero-value omission** — empty fields are excluded (protobuf default)

## Related Skills

Browse other **bom** skills in the [`bom/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/bom/get-bom

# Or install the full runtime package
npm install @huaqiu/hqeda
```

