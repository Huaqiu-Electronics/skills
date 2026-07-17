---
name: capability-get-capabilities
metadata:
  category: capability
  service: CapabilityService
  method: GetCapabilities
  rpcKind: unary
description: >-
  Get Capabilities via CapabilityService.GetCapabilities
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - capability
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetCapabilitiesRequestSchema
  namespace: HqServicesV1CapabilityService
---

# Get Capabilities

Get Capabilities via CapabilityService.GetCapabilities

## Overview

This skill provides access to the **`CapabilityService.GetCapabilities`** RPC method on the Huaqiu EDA engine. It is part of the **capability** domain and executes against the `capability` client.

| Property | Value |
| --- | --- |
| Skill ID | `capability-get-capabilities` |
| Service | `CapabilityService` |
| Method | `GetCapabilities` |
| Transport | Unary (unary) |
| Domain | capability |
| Request type | `GetCapabilitiesRequest` |
| Response type | `GetCapabilitiesResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## Response

Returns a `GetCapabilitiesResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `capabilities` | `Capability[]` | yes | Capabilities supported by this deployment.  Clients MUST treat
unknown enum values as "unsupported" to stay forward compatible
with server-side additions. |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "capabilities": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetCapabilitiesRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("capability-get-capabilities");
const result = await skill.execute(ctx, {
  context: {},
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

Browse other **capability** skills in the [`capability/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/capability/get-capabilities

# Or install the full runtime package
npm install @huaqiu/hqeda
```

