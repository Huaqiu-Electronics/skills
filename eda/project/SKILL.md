---
name: eda-project
metadata:
  category: project
description: >-
  Project operations for Huaqiu EDA. Use this skill when you need to work with project-related operations including close project, get active project, get project.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - project
entry: @huaqiu/hqeda
manifest: @huaqiu/hqeda/skill.json
---

# Project Skills

Project operations for Huaqiu EDA. Use this skill when you need to work with project-related operations including close project, get active project, get project.

## Available Capabilities

Total: **6** skills in the **project** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`close-project`](close-project/SKILL.md) | Closes an opened project. | no |
| [`get-active-project`](get-active-project/SKILL.md) | Returns the project currently active in the editor UI. | no |
| [`get-project`](get-project/SKILL.md) | Returns one opened project. | no |
| [`list-open-projects`](list-open-projects/SKILL.md) | Returns all projects currently opened in this HQ EDA process. | no |
| [`open-project`](open-project/SKILL.md) | Opens a project into the current HQ EDA editor process. | no |
| [`save-project`](save-project/SKILL.md) | Persists an opened project. | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

