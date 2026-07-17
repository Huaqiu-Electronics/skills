---
name: eda-export
metadata:
  category: export
description: >-
  Export operations for Huaqiu EDA. Use this skill when you need to work with export-related operations including export bom, export target.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - export
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Export Skills

Export operations for Huaqiu EDA. Use this skill when you need to work with export-related operations including export bom, export target.

## Available Capabilities

Total: **2** skills in the **export** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`export-bom`](export-bom/SKILL.md) | Export Bom via ExportService.ExportBOM | no |
| [`export-target`](export-target/SKILL.md) | Export Target via ExportService.ExportTarget | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

