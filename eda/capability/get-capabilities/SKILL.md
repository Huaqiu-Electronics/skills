---
name: capability-get-capabilities
metadata:
  category: capability
  service: CapabilityService
  method: GetCapabilities
  rpcKind: unary
description: >-
  Get Capabilities via CapabilityService.GetCapabilities
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - capability
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: GetCapabilitiesRequestSchema
  namespace: HqServicesV1CapabilityService
---

# Get Capabilities

Get Capabilities via CapabilityService.GetCapabilities

## Overview

This skill provides access to the **`CapabilityService.GetCapabilities`** RPC method on the Huaqiu EDA engine. It is part of the **capability** domain and executes against the `capability` client.

| Property | Value |
| --- | --- |
| Skill ID | `capability-get-capabilities` |
| Service | `CapabilityService` |
| Method | `GetCapabilities` |
| Transport | Unary (unary) |
| Domain | capability |
| Request type | `GetCapabilitiesRequest` |
| Response type | `GetCapabilitiesResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetCapabilitiesRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("capability-get-capabilities");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **capability** skills in the [`capability/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/capability/get-capabilities

# Or install the full runtime package
npm install @huaqiu/hqeda
```

