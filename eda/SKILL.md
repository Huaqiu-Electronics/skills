---
name: eda
metadata:
  category: eda
description: >-
  Full Huaqiu EDA skill collection — 110 executable capabilities across 18 domains including BOM, ERC, schematic, canvas, and project management.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - kicad
  - electronics
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Huaqiu EDA Skills

The official Huaqiu EDA skill collection — **110** executable capabilities across **18** domains. Each skill is a self-contained folder so you only load the capability you need.

## Skill Domains

| Domain | Skills | Description |
| --- | --- | --- |
| [ai](ai/SKILL.md) | 1 | Ai operations |
| [bom](bom/SKILL.md) | 1 | Bom operations |
| [canvas](canvas/SKILL.md) | 28 | Canvas operations |
| [capability](capability/SKILL.md) | 1 | Capability operations |
| [context](context/SKILL.md) | 1 | Context operations |
| [discovery](discovery/SKILL.md) | 1 | Discovery operations |
| [erc](erc/SKILL.md) | 6 | Erc operations |
| [event](event/SKILL.md) | 1 | Event operations |
| [export](export/SKILL.md) | 2 | Export operations |
| [graph](graph/SKILL.md) | 2 | Graph operations |
| [import](import/SKILL.md) | 1 | Import operations |
| [kernel](kernel/SKILL.md) | 2 | Kernel operations |
| [obj-place](obj-place/SKILL.md) | 38 | Obj Place operations |
| [placement](placement/SKILL.md) | 9 | Placement operations |
| [project](project/SKILL.md) | 6 | Project operations |
| [runtime](runtime/SKILL.md) | 2 | Runtime operations |
| [selection](selection/SKILL.md) | 3 | Selection operations |
| [transaction](transaction/SKILL.md) | 5 | Transaction operations |

## Installation

Install a single skill:

```bash
npx skills add Huaqiu-Electronics/skills --path eda/bom/get-bom
```

Or install the full runtime package:

```bash
npm install @huaqiu/hqeda
```

## Best Practices

### Serializing Protobuf Messages

Skill responses are protobuf message objects. **Never use `JSON.stringify()` directly** — it throws on `BigInt` fields and produces empty objects for oneof ADT fields.

Use `toJson()` or `toJsonString()` from `@huaqiu/hqeda` instead:

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const skill = getSkill('bom-get-bom');
const result = await skill.execute(ctx, { project: 'my-project' });

// Correct: uses toJsonString which handles BigInt, oneof, WKTs, etc.
console.log(toJsonString(result, { prettySpaces: 2 }));

// Wrong: JSON.stringify(result) — throws on BigInt fields!
```

## Related Resources

- [`@huaqiu/hqeda`](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime npm package with all capabilities
- [Capability registry](https://www.npmjs.com/package/@huaqiu/hqeda) — machine-readable manifest inside the npm package
- [Playbooks](https://www.npmjs.com/package/@huaqiu/hqeda) — human-authored engineering review playbooks inside the npm package

