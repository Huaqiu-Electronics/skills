---
name: eda-placement
metadata:
  category: placement
description: >-
  Placement operations for Huaqiu EDA. Use this skill when you need to work with placement-related operations including cancel block draw, clear net alias attach obj, handle block draw click.
version: 0.1.0
vendor: Huaqiu Electronics
tags:
  - eda
  - huaqiu
  - placement
entry: "@huaqiu/hqeda"
manifest: "@huaqiu/hqeda/skill.json"
---

# Placement Skills

Placement operations for Huaqiu EDA. Use this skill when you need to work with placement-related operations including cancel block draw, clear net alias attach obj, handle block draw click.

## Available Capabilities

Total: **9** skills in the **placement** domain.

| Skill | Description | Streaming |
| --- | --- | --- |
| [`cancel-block-draw`](cancel-block-draw/SKILL.md) | Cancel Block Draw via ComponentPlaceService.CancelBlockDraw | no |
| [`clear-net-alias-attach-obj`](clear-net-alias-attach-obj/SKILL.md) | Clear Net Alias Attach Obj via ComponentPlaceService.ClearNetAliasAttachObj | no |
| [`handle-block-draw-click`](handle-block-draw-click/SKILL.md) | Handle Block Draw Click via ComponentPlaceService.HandleBlockDrawClick | no |
| [`handle-part-draw-click`](handle-part-draw-click/SKILL.md) | Handle Part Draw Click via ComponentPlaceService.HandlePartDrawClick | no |
| [`handle-symbol-draw-click`](handle-symbol-draw-click/SKILL.md) | Handle Symbol Draw Click via ComponentPlaceService.HandleSymbolDrawClick | no |
| [`place-block`](place-block/SKILL.md) | block | no |
| [`place-part`](place-part/SKILL.md) | part | no |
| [`place-symbol`](place-symbol/SKILL.md) | symbol | no |
| [`set-net-alias-attach-obj`](set-net-alias-attach-obj/SKILL.md) | net alias attach | no |

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

