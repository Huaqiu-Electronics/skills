---
name: eda-selection
metadata:
  category: selection
description: >-
  Selection operations for Huaqiu EDA. Use this skill when you need to work with selection-related operations including clear selection, get selection, set selection.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - selection
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Selection Skills

Selection operations for Huaqiu EDA. Use this skill when you need to work with selection-related operations including clear selection, get selection, set selection.

## Available Capabilities

Total: **3** skills in the **selection** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`clear-selection`](clear-selection/SKILL.md) | Clear Selection via SelectionService.ClearSelection | no |
| [`get-selection`](get-selection/SKILL.md) | Get Selection via SelectionService.GetSelection | no |
| [`set-selection`](set-selection/SKILL.md) | Set Selection via SelectionService.SetSelection | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

