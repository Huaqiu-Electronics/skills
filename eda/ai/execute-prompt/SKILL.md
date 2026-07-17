---
name: ai-execute-prompt
metadata:
  category: ai
  service: AIService
  method: ExecutePrompt
  rpcKind: unary
description: >-
  Execute Prompt via AIService.ExecutePrompt
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - ai
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
inputSchema:
  name: AIRequestSchema
  namespace: HqServicesV1AiService
---

# Execute Prompt

Execute Prompt via AIService.ExecutePrompt

## Overview

This skill provides access to the **`AIService.ExecutePrompt`** RPC method on the Huaqiu EDA engine. It is part of the **ai** domain and executes against the `ai` client.

| Property | Value |
| --- | --- |
| Skill ID | `ai-execute-prompt` |
| Service | `AIService` |
| Method | `ExecutePrompt` |
| Transport | Unary (unary) |
| Domain | ai |
| Request type | `AIRequest` |
| Response type | `AIResponse` |

## Parameters

| Name | Type | Required | Repeated | Description |
| --- | --- | --- | --- | --- |
| `context` | `ProjectContext` | no | no | — |
| `prompt` | `string` | yes | no | — |

## How to Use

The skill is executed by the HQ EDA skill runtime, which provides a `SkillContext` with a connected `EditorClient`. The runtime calls `skill.execute(ctx, input)` where `input` must match the `AIRequestSchema` protobuf message shape.

```typescript
import { getSkill } from "@huaqiu/hqeda";

const skill = getSkill("ai-execute-prompt");
const result = await skill.execute(ctx, {
  context: {},
  prompt: "<string>",
});
```

## Related Skills

Browse other **ai** skills in the [`ai/`](../) directory, or see the full capability registry in the `@huaqiu/hqeda` npm package.

## Installation

```bash
# Install from the skills repo
npx skills add Huaqiu-Electronics/skills --path eda/ai/execute-prompt

# Or install the full runtime package
npm install @huaqiu/hqeda
```

