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
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
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

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetContextRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("context-get-context");
const result = await skill.execute(ctx, {
  context: {},
  includeGraph: false,
  includeSelection: false,
});
```

## Related Skills

Browse other **context** skills in the [`context/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/context/get-context

# Or install the full runtime package
npm install @huaqiu/hqeda
```

