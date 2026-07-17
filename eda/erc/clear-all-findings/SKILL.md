---
name: erc-clear-all-findings
metadata:
  category: erc
  service: ERCService
  method: ClearAllFindings
  rpcKind: unary
description: >-
  Clear All Findings via ERCService.ClearAllFindings
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: ClearAllFindingsRequestSchema
  namespace: HqServicesV1ErcService
---

# Clear All Findings

Clear All Findings via ERCService.ClearAllFindings

## Overview

This skill provides access to the **`ERCService.ClearAllFindings`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-clear-all-findings` |
| Service | `ERCService` |
| Method | `ClearAllFindings` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `ClearAllFindingsRequest` |
| Response type | `ClearFindingsResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ClearAllFindingsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("erc-clear-all-findings");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/clear-all-findings

# Or install the full runtime package
npm install @huaqiu/hqeda
```

