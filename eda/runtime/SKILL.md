---
name: eda-runtime
metadata:
  category: runtime
description: >-
  Runtime operations for Huaqiu EDA. Use this skill when you need to work with runtime-related operations including execute commands, validate commands.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - runtime
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
---

# Runtime Skills

Runtime operations for Huaqiu EDA. Use this skill when you need to work with runtime-related operations including execute commands, validate commands.

## Available Capabilities

Total: **2** skills in the **runtime** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`execute-commands`](execute-commands/SKILL.md) | Execute Commands via RuntimeService.ExecuteCommands | no |
| [`validate-commands`](validate-commands/SKILL.md) | Validate Commands via RuntimeService.ValidateCommands | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

