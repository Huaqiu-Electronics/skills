---
name: import-import-design
metadata:
  category: import
  service: ImportService
  method: ImportDesign
  rpcKind: unary
description: >-
  Import a design from an external EDA system
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - import
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ImportDesignRequestSchema
  namespace: HqServicesV1ImportService
---

# Import Design

Import a design from an external EDA system

## Overview

This skill provides access to the **`ImportService.ImportDesign`** RPC method on the Huaqiu EDA engine. It is part of the **import** domain and executes against the `import` client.

| Property | Value |
| --- | --- |
| Skill ID | `import-import-design` |
| Service | `ImportService` |
| Method | `ImportDesign` |
| Transport | Unary (unary) |
| Domain | import |
| Request type | `ImportDesignRequest` |
| Response type | `ImportDesignResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `sourceVendor` | `string` | yes | no | Source EDA vendor/tool |
| `sourceFormat` | `string` | yes | no | File format (e.g. "altium", "kicad", "odb++", "ipc2581") |
| `sourceUri` | `string` | yes | no | URL or uploaded file location |

## Response

Returns a `ImportDesignResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `designId` | `string` | no | Internal design ID after import |
| `status` | `string` | no | Status of import |
| `warnings` | `string[]` | yes | Optional warnings (unsupported layers, missing symbols, etc.) |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "designId": "<string>",
  "status": "<string>",
  "warnings": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ImportDesignRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("import-import-design");
const result = await skill.execute(ctx, {
  context: {},
  sourceVendor: "<string>",
  sourceFormat: "<string>",
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

Browse other **import** skills in the [`import/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/import/import-design

# Or install the full runtime package
npm install @huaqiu/hqeda
```

