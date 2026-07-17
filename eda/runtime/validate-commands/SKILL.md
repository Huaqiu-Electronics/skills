---
name: runtime-validate-commands
metadata:
  category: runtime
  service: RuntimeService
  method: ValidateCommands
  rpcKind: unary
description: >-
  Validate Commands via RuntimeService.ValidateCommands
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - runtime
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ValidationRequestSchema
  namespace: HqRuntimeV1Validator
---

# Validate Commands

Validate Commands via RuntimeService.ValidateCommands

## Overview

This skill provides access to the **`RuntimeService.ValidateCommands`** RPC method on the Huaqiu EDA engine. It is part of the **runtime** domain and executes against the `runtime` client.

| Property | Value |
| --- | --- |
| Skill ID | `runtime-validate-commands` |
| Service | `RuntimeService` |
| Method | `ValidateCommands` |
| Transport | Unary (unary) |
| Domain | runtime |
| Request type | `ValidationRequest` |
| Response type | `ValidationResult` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `commands` | `Command[]` | no | yes | — |
| `baseRevision` | `bigint` | yes | no | — |

## Response

Returns a `ValidationResult` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `isValid` | `boolean` | no | — |
| `violations` | `ValidationViolation[]` | yes | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "isValid": false,
  "violations": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ValidationRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("runtime-validate-commands");
const result = await skill.execute(ctx, {
  context: {},
  commands: [],
  baseRevision: 0,
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

Browse other **runtime** skills in the [`runtime/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/runtime/validate-commands

# Or install the full runtime package
npm install @huaqiu/hqeda
```

