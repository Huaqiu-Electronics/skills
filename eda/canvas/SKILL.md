---
name: eda-canvas
metadata:
  category: canvas
description: >-
  Canvas operations for Huaqiu EDA. Use this skill when you need to work with canvas-related operations including align objects, can paste, clear all sel.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - canvas
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Canvas Skills

Canvas operations for Huaqiu EDA. Use this skill when you need to work with canvas-related operations including align objects, can paste, clear all sel.

## Available Capabilities

Total: **28** skills in the **canvas** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`align-objects`](align-objects/SKILL.md) | transform | no |
| [`can-paste`](can-paste/SKILL.md) | Can Paste via CanvasOpsService.CanPaste | no |
| [`clear-all-sel`](clear-all-sel/SKILL.md) | selection | no |
| [`copy-selected`](copy-selected/SKILL.md) | Copy Selected via CanvasOpsService.CopySelected | no |
| [`delete-selected`](delete-selected/SKILL.md) | edit | no |
| [`distribute-objects`](distribute-objects/SKILL.md) | Distribute Objects via CanvasOpsService.DistributeObjects | no |
| [`get-align-type`](get-align-type/SKILL.md) | Get Align Type via CanvasOpsService.GetAlignType | no |
| [`get-selected-object-json`](get-selected-object-json/SKILL.md) | Get Selected Object Json via CanvasOpsService.GetSelectedObjectJson | no |
| [`get-selected-objects-json`](get-selected-objects-json/SKILL.md) | Get Selected Objects Json via CanvasOpsService.GetSelectedObjectsJson | no |
| [`mirror-objects`](mirror-objects/SKILL.md) | Mirror Objects via CanvasOpsService.MirrorObjects | no |
| [`move-selected-objs`](move-selected-objs/SKILL.md) | Move Selected Objs via CanvasOpsService.MoveSelectedObjs | no |
| [`on-canvas-escape`](on-canvas-escape/SKILL.md) | state | no |
| [`pan-canvas`](pan-canvas/SKILL.md) | viewport | no |
| [`paste-selected`](paste-selected/SKILL.md) | Paste Selected via CanvasOpsService.PasteSelected | no |
| [`rotate-objects`](rotate-objects/SKILL.md) | Rotate Objects via CanvasOpsService.RotateObjects | no |
| [`screen-to-canvas-local`](screen-to-canvas-local/SKILL.md) | coordinate | no |
| [`select-all`](select-all/SKILL.md) | Select All via CanvasOpsService.SelectAll | no |
| [`select-object-at`](select-object-at/SKILL.md) | Select Object At via CanvasOpsService.SelectObjectAt | no |
| [`set-align-type`](set-align-type/SKILL.md) | grid align | no |
| [`set-page-size`](set-page-size/SKILL.md) | page | no |
| [`set-page-size-rect`](set-page-size-rect/SKILL.md) | Set Page Size Rect via CanvasOpsService.SetPageSizeRect | no |
| [`zoom-all`](zoom-all/SKILL.md) | Zoom All via CanvasOpsService.ZoomAll | no |
| [`zoom-area-by-double-box`](zoom-area-by-double-box/SKILL.md) | Zoom Area By Double Box via CanvasOpsService.ZoomAreaByDoubleBox | no |
| [`zoom-area-by-int-box`](zoom-area-by-int-box/SKILL.md) | Zoom Area By Int Box via CanvasOpsService.ZoomAreaByIntBox | no |
| [`zoom-area-by-points`](zoom-area-by-points/SKILL.md) | Zoom Area By Points via CanvasOpsService.ZoomAreaByPoints | no |
| [`zoom-in`](zoom-in/SKILL.md) | zoom | no |
| [`zoom-out`](zoom-out/SKILL.md) | Zoom Out via CanvasOpsService.ZoomOut | no |
| [`zoom-selected`](zoom-selected/SKILL.md) | Zoom Selected via CanvasOpsService.ZoomSelected | no |

## See Also

- [All EDA skills](../SKILL.md)
- [`@huaqiu/hqeda` npm package](https://www.npmjs.com/package/@huaqiu/hqeda) — shared runtime + capability registry

## Best Practices

**Always use `toJsonString()` (not `JSON.stringify()`) to serialize protobuf responses.** `JSON.stringify()` throws on `BigInt` fields and mishandles oneof ADT fields.

```typescript
import { getSkill, toJsonString } from "@huaqiu/hqeda";

const result = await skill.execute(ctx, input);
console.log(toJsonString(result, { prettySpaces: 2 }));
```

