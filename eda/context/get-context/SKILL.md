---
name: context-get-context
metadata:
  category: context
  service: ContextService
  method: GetContext
  rpcKind: unary
description: >-
  Get Context via ContextService.GetContext
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - context
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetContextRequestSchema
  namespace: HqServicesV1ContextService
---

# Get Context

Get Context via ContextService.GetContext

## Overview

This skill provides access to the **`ContextService.GetContext`** RPC method on the Huaqiu EDA engine. It is part of the **context** domain and executes against the `context` client.

| Property | Value |
| --- | --- |
| Skill ID | `context-get-context` |
| Service | `ContextService` |
| Method | `GetContext` |
| Transport | Unary (unary) |
| Domain | context |
| Request type | `GetContextRequest` |
| Response type | `GetContextResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `includeGraph` | `boolean` | yes | no | Bitfield-ish flags.  Each flag turns on a sub-facet of the response. |
| `includeSelection` | `boolean` | yes | no | — |
| `includeSymbols` | `boolean` | yes | no | — |
| `includeNets` | `boolean` | yes | no | — |
| `includeViewport` | `boolean` | yes | no | — |
| `includeOpenDocuments` | `boolean` | yes | no | — |
| `includeCursor` | `boolean` | yes | no | — |

## Response

Returns a `GetContextResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `graph` | `KernelSnapshot` | no | Populated if `include_graph` was true. |
| `selectionIds` | `string[]` | yes | Populated if `include_selection` was true. |
| `symbolInstanceIds` | `string[]` | yes | Populated if `include_symbols` was true — subset of the graph. |
| `netIds` | `string[]` | yes | Populated if `include_nets` was true — subset of the graph. |
| `viewport` | `ContextViewport` | no | Populated if `include_viewport` was true. |
| `openDocuments` | `ContextOpenDocument[]` | yes | Populated if `include_open_documents` was true. |
| `cursor` | `Vector2i64` | no | Populated if `include_cursor` was true — cursor cad-unit position
in the currently active document. |
| `revision` | `bigint` | no | Monotonic revision of the kernel at the time the snapshot was
taken.  Callers can use this to correlate with event streams. |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "graph": {},
  "selectionIds": [
    {}
  ],
  "symbolInstanceIds": [
    {}
  ],
  "netIds": [
    {}
  ],
  "viewport": {},
  "openDocuments": [
    {}
  ],
  "cursor": {},
  "revision": "0"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetContextRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("context-get-context");
const result = await skill.execute(ctx, {
  context: {},
  includeGraph: false,
  includeSelection: false,
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

Browse other **context** skills in the [`context/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/context/get-context

# Or install the full runtime package
npm install @huaqiu/hqeda
```

