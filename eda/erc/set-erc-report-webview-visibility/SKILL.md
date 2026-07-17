---
name: erc-set-erc-report-webview-visibility
metadata:
  category: erc
  service: ERCService
  method: SetErcReportWebviewVisibility
  rpcKind: unary
description: >-
  ONLY controls report webview visibility
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SetErcReportWebviewVisibilityRequestSchema
  namespace: HqServicesV1ErcService
---

# Set Erc Report Webview Visibility

ONLY controls report webview visibility

## Overview

This skill provides access to the **`ERCService.SetErcReportWebviewVisibility`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-set-erc-report-webview-visibility` |
| Service | `ERCService` |
| Method | `SetErcReportWebviewVisibility` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `SetErcReportWebviewVisibilityRequest` |
| Response type | `SetErcReportWebviewVisibilityResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `visible` | `boolean` | no | no | If omitted -> treat as toggle
true  -> show report webview
false -> hide report webview |

## Response

Returns a `SetErcReportWebviewVisibilityResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `visible` | `boolean` | no | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "visible": false
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetErcReportWebviewVisibilityRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("erc-set-erc-report-webview-visibility");
const result = await skill.execute(ctx, {
  context: {},
  visible: false,
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

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/set-erc-report-webview-visibility

# Or install the full runtime package
npm install @huaqiu/hqeda
```

