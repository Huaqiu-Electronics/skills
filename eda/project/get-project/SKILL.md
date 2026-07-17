---
name: project-get-project
metadata:
  category: project
  service: ProjectService
  method: GetProject
  rpcKind: unary
description: >-
  Returns one opened project.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetProjectRequestSchema
  namespace: HqServicesV1ProjectService
---

# Get Project

Returns one opened project.

## Overview

This skill provides access to the **`ProjectService.GetProject`** RPC method on the Huaqiu EDA engine. It is part of the **project** domain and executes against the `project` client.

| Property | Value |
| --- | --- |
| Skill ID | `project-get-project` |
| Service | `ProjectService` |
| Method | `GetProject` |
| Transport | Unary (unary) |
| Domain | project |
| Request type | `GetProjectRequest` |
| Response type | `GetProjectResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## Response

Returns a `GetProjectResponse` message with the following fields:

| Name | Type | Repeated | Description |
| --- | --- | --- | --- |
| `project` | `ProjectMetadata` | no | — |

## Usage Examples

### getProject returns details for discovered project

_Source: `discover-active-project.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## Response Example

Representative response structure (field values are placeholders):

```json
{
  "project": {}
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetProjectRequestSchema` protobuf message shape.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill("project-get-project");
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

Browse other **project** skills in the [`project/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/project/get-project

# Or install the full runtime package
npm install @huaqiu/hqeda
```

