---
name: ai-execute-prompt
metadata:
  category: ai
  service: AIService
  method: ExecutePrompt
  rpcKind: unary
description: >-
  Execute Prompt via AIService.ExecutePrompt
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - ai
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: AIRequestSchema
  namespace: HqServicesV1AiService
---

# Execute Prompt

Execute Prompt via AIService.ExecutePrompt

## Overview

This skill provides access to the **`AIService.ExecutePrompt`** RPC method on the Huaqiu EDA engine. It is part of the **ai** domain and executes against the `ai` client.

| Property | Value |
| --- | --- |
| Skill ID | `ai-execute-prompt` |
| Service | `AIService` |
| Method | `ExecutePrompt` |
| Transport | Unary (unary) |
| Domain | ai |
| Request type | `AIRequest` |
| Response type | `AIResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `prompt` | `string` | yes | no | — |

## Response

Returns a `AIResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `commands` | `Command[]` | yes | — |
| `findings` | `ErcFinding[]` | yes | — |

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "commands": [
    {}
  ],
  "findings": [
    {}
  ]
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `AIRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("ai-execute-prompt");
const result = await skill.execute(ctx, {
  context: {},
  prompt: "<string>",
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

Browse other **ai** skills in the [`ai/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/ai/execute-prompt

# Or install the full runtime package
npm install @huaqiu/hqeda
```

