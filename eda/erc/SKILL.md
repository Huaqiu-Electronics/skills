---
name: eda-erc
metadata:
  category: erc
description: >-
  Erc operations for Huaqiu EDA. Use this skill when you need to work with erc-related operations including clear all findings, clear findings, run checks.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - erc
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Erc Skills

Erc operations for Huaqiu EDA. Use this skill when you need to work with erc-related operations including clear all findings, clear findings, run checks.

## Available Capabilities

Total: **6** skills in the **erc** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`clear-all-findings`](clear-all-findings/SKILL.md) | Clear All Findings via ERCService.ClearAllFindings | no |
| [`clear-findings`](clear-findings/SKILL.md) | Clear Findings via ERCService.ClearFindings | no |
| [`run-checks`](run-checks/SKILL.md) | Run erc check with the eda's built-in engine | no |
| [`set-erc-report-webview-visibility`](set-erc-report-webview-visibility/SKILL.md) | ONLY controls report webview visibility | no |
| [`set-report-webview-state`](set-report-webview-state/SKILL.md) | Set Report Webview State via ERCService.SetReportWebviewState | no |
| [`show-findings`](show-findings/SKILL.md) | Canvas interaction (row click → highlight in EDA view) | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

