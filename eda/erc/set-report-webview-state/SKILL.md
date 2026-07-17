---
name: erc-set-report-webview-state
metadata:
  category: erc
  service: ERCService
  method: SetReportWebviewState
  rpcKind: unary
description: >-
  Set Report Webview State via ERCService.SetReportWebviewState
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: SetReportWebviewStateRequestSchema
  namespace: HqServicesV1ErcService
---

# Set Report Webview State

Set Report Webview State via ERCService.SetReportWebviewState

## Overview

This skill provides access to the **`ERCService.SetReportWebviewState`** RPC method on the Huaqiu EDA engine. It is part of the **erc** domain and executes against the `erc` client.

| Property | Value |
| --- | --- |
| Skill ID | `erc-set-report-webview-state` |
| Service | `ERCService` |
| Method | `SetReportWebviewState` |
| Transport | Unary (unary) |
| Domain | erc |
| Request type | `SetReportWebviewStateRequest` |
| Response type | `SetReportWebviewStateResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `visible` | `boolean` | no | no | Optional explicit state.
If omitted -> toggle current state.
If true -> show
If false -> hide |
| `reportId` | `string` | no | no | Optional: which report to focus (if multiple reports exist later) |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SetReportWebviewStateRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("erc-set-report-webview-state");
const result = await skill.execute(ctx, {
  context: {},
  visible: false,
  reportId: "<string>",
});
```

## Related Skills

Browse other **erc** skills in the [`erc/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/erc/set-report-webview-state

# Or install the full runtime package
npm install @huaqiu/hqeda
```

