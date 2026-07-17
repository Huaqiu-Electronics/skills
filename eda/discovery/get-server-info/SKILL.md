---
name: discovery-get-server-info
metadata:
  category: discovery
  service: DiscoveryService
  method: GetServerInfo
  rpcKind: unary
description: >-
  Get Server Info via DiscoveryService.GetServerInfo
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - discovery
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetServerInfoRequestSchema
  namespace: HqDiscoveryV1Discovery
---

# Get Server Info

Get Server Info via DiscoveryService.GetServerInfo

## Overview

This skill provides access to the **`DiscoveryService.GetServerInfo`** RPC method on the Huaqiu EDA engine. It is part of the **discovery** domain and executes against the `discovery` client.

| Property | Value |
| --- | --- |
| Skill ID | `discovery-get-server-info` |
| Service | `DiscoveryService` |
| Method | `GetServerInfo` |
| Transport | Unary (unary) |
| Domain | discovery |
| Request type | `GetServerInfoRequest` |
| Response type | `GetServerInfoResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `EditorContext` | no | no | — |

## Response

Returns a `GetServerInfoResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `instanceId` | `string` | no | — |
| `version` | `string` | no | — |
| `pid` | `number` | no | — |
| `capabilities` | `Capability[]` | yes | — |

## Usage Examples

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{}
```

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "instanceId": "<string>",
  "version": "<string>",
  "pid": 0,
  "capabilities": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetServerInfoRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("discovery-get-server-info");
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

Browse other **discovery** skills in the [`discovery/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/discovery/get-server-info

# Or install the full runtime package
npm install @huaqiu/hqeda
```

