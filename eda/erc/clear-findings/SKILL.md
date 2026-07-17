---
name: erc-clear-findings
metadata:
  category: erc
  service: ERCService
  method: ClearFindings
  rpcKind: unary
description: >-
  Clear Findings via ERCService.ClearFindings
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ClearFindingsRequestSchema
  namespace: HqServicesV1ErcService
---

# Clear Findings

Clear Findings via ERCService.ClearFindings

## Overview

This skill provides access to the **`ERCService.ClearFindings`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-clear-findings` |
| Service | `ERCService` |
| Method | `ClearFindings` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `ClearFindingsRequest` |
| Response type | `ClearFindingsResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `findingIds` | `string[]` | no | yes | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ClearFindingsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("erc-clear-findings");
const result = await skill.execute(ctx, {
  context: {},
  findingIds: [],
});
```

## Related Skills

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/clear-findings

# Or install the full runtime package
npm install @huaqiu/hqeda
```

