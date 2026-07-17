---
name: kernel-get-snapshot
metadata:
  category: kernel
  service: KernelService
  method: GetSnapshot
  rpcKind: unary
description: >-
  Get Snapshot via KernelService.GetSnapshot
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - kernel
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetSnapshotRequestSchema
  namespace: HqServicesV1KernelService
---

# Get Snapshot

Get Snapshot via KernelService.GetSnapshot

## Overview

This skill provides access to the **`KernelService.GetSnapshot`** RPC method on the Huaqiu EDA engine. It is part of the **kernel** domain and executes against the `kernel` client.

| Property | Value |
| --- | --- |
| Skill ID | `kernel-get-snapshot` |
| Service | `KernelService` |
| Method | `GetSnapshot` |
| Transport | Unary (unary) |
| Domain | kernel |
| Request type | `GetSnapshotRequest` |
| Response type | `GetSnapshotResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `atRevision` | `bigint` | yes | no | — |

## Usage Examples

### get kernel snapshot for a discovered project

_Source: `integration.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### retrieves snapshot for a discovered project

_Source: `kernel-snapshot.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### snapshot contains symbol definitions

_Source: `kernel-snapshot.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

### toJson produces LLM-friendly JSON output

_Source: `kernel-snapshot.test.ts`_

```json
{
  "context": "<createProjectContext>"
}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetSnapshotRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("kernel-get-snapshot");
const result = await skill.execute(ctx, {
  context: {},
  atRevision: 0,
});
```

## Related Skills

Browse other **kernel** skills in the [`kernel/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/kernel/get-snapshot

# Or install the full runtime package
npm install @huaqiu/hqeda
```

