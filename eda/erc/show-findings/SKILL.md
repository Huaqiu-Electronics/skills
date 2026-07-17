---
name: erc-show-findings
metadata:
  category: erc
  service: ERCService
  method: ShowFindings
  rpcKind: unary
description: >-
  Canvas interaction (row click → highlight in EDA view)
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: ShowFindingsRequestSchema
  namespace: HqServicesV1ErcService
---

# Show Findings

Canvas interaction (row click → highlight in EDA view)

## Overview

This skill provides access to the **`ERCService.ShowFindings`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-show-findings` |
| Service | `ERCService` |
| Method | `ShowFindings` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `ShowFindingsRequest` |
| Response type | `ShowFindingsResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `findings` | `ErcFinding[]` | no | yes | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `ShowFindingsRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("erc-show-findings");
const result = await skill.execute(ctx, {
  context: {},
  findings: [],
});
```

## Related Skills

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/show-findings

# Or install the full runtime package
npm install @huaqiu/hqeda
```

