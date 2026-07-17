---
name: kernel-get-entity
metadata:
  category: kernel
  service: KernelService
  method: GetEntity
  rpcKind: unary
description: >-
  Get Entity via KernelService.GetEntity
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - kernel
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetEntityRequestSchema
  namespace: HqServicesV1KernelService
---

# Get Entity

Get Entity via KernelService.GetEntity

## Overview

This skill provides access to the **`KernelService.GetEntity`** RPC method on the Huaqiu EDA engine. It is part of the **kernel** domain and executes against the `kernel` client.

| Property | Value |
| --- | --- |
| Skill ID | `kernel-get-entity` |
| Service | `KernelService` |
| Method | `GetEntity` |
| Transport | Unary (unary) |
| Domain | kernel |
| Request type | `GetEntityRequest` |
| Response type | `GetEntityResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `entityId` | `string` | yes | no | — |

## Response

Returns a `GetEntityResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `entity` | `Any` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "entity": {}
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetEntityRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("kernel-get-entity");
const result = await skill.execute(ctx, {
  context: {},
  entityId: "<string>",
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

Browse other **kernel** skills in the [`kernel/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/kernel/get-entity

# Or install the full runtime package
npm install @huaqiu/hqeda
```

