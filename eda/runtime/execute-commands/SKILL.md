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
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
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

## Response

Returns a `ExecuteCommandsResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `success` | `boolean` | no | — |
| `results` | `CommandResult[]` | yes | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "success": false,
  "results": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ExecuteCommandsRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("runtime-execute-commands");
const result = await skill.execute(ctx, {
  context: {},
  commands: [],
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
npx skills add Huaqiu-Electronics/skills --path eda/runtime/execute-commands

# Or install the full runtime package
npm install @huaqiu/hqeda
```

