---
name: discovery-get-server-info
metadata:
  category: discovery
  service: DiscoveryService
  method: GetServerInfo
  rpcKind: unary
description: >-
  Get Server Info via DiscoveryService.GetServerInfo
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - discovery
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: GetServerInfoRequestSchema
  namespace: HqDiscoveryV1Discovery
---

# Get Server Info

Get Server Info via DiscoveryService.GetServerInfo

## Overview

This skill provides access to the **`DiscoveryService.GetServerInfo`** RPC method on the Huaqiu EDA engine. It is part of the **discovery** domain and executes against the `discovery` client.

| Property | Value |
| --- | --- |
| Skill ID | `discovery-get-server-info` |
| Service | `DiscoveryService` |
| Method | `GetServerInfo` |
| Transport | Unary (unary) |
| Domain | discovery |
| Request type | `GetServerInfoRequest` |
| Response type | `GetServerInfoResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `EditorContext` | no | no | — |

## Usage Examples

### server is responsive on port 59999

_Source: `health-check.test.ts`_

```json
{}
```

### discover server info

_Source: `integration.test.ts`_

```json
{}
```

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `GetServerInfoRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("discovery-get-server-info");
const result = await skill.execute(ctx, {
  context: {},
});
```

## Related Skills

Browse other **discovery** skills in the [`discovery/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/discovery/get-server-info

# Or install the full runtime package
npm install @huaqiu/hqeda
```

