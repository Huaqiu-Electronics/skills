---
name: event-subscribe
metadata:
  category: event
  service: EventService
  method: Subscribe
  rpcKind: server_streaming
description: >-
  Subscribe via EventService.Subscribe
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - event
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
inputSchema:
  name: SubscribeRequestSchema
  namespace: HqServicesV1EventService
---

# Subscribe

Subscribe via EventService.Subscribe

## Overview

This skill provides access to the **`EventService.Subscribe`** RPC method on the Huaqiu EDA engine. It is part of the **event** domain and executes against the `event` client.

| Property | Value |
| --- | --- |
| Skill ID | `event-subscribe` |
| Service | `EventService` |
| Method | `Subscribe` |
| Transport | Streaming (server_streaming) |
| Domain | event |
| Request type | `SubscribeRequest` |
| Response type | `EventEnvelope` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `sinceRevision` | `bigint` | yes | no | Start from this kernel revision.  If zero, the server starts
from the next event produced after the subscription was opened.
If non-zero, the server replays events from that revision onward
before switching to live events — this gives clients a deterministic
way to catch up after a reconnect. |
| `eventTypeFilter` | `string[]` | no | yes | Optional filter.  If non-empty, only events whose `event_type`
matches one of the supplied strings are delivered. |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `SubscribeRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("event-subscribe");
const result = await skill.execute(ctx, {
  context: {},
  sinceRevision: 0,
  eventTypeFilter: [],
});
```

## Related Skills

Browse other **event** skills in the [`event/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/event/subscribe

# Or install the full runtime package
npm install @huaqiu/hqeda
```

