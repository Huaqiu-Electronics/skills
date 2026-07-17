---
name: erc-run-checks
metadata:
  category: erc
  service: ERCService
  method: RunChecks
  rpcKind: unary
description: >-
  Run erc check with the eda's built-in engine
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: RunChecksRequestSchema
  namespace: HqServicesV1ErcService
---

# Run Checks

Run erc check with the eda's built-in engine

## Overview

This skill provides access to the **`ERCService.RunChecks`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-run-checks` |
| Service | `ERCService` |
| Method | `RunChecks` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `RunChecksRequest` |
| Response type | `RunChecksResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `RunChecksRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("erc-run-checks");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/run-checks

# Or install the full runtime package
npm install @huaqiu/hqeda
```

