# Huaqiu EDA Agent Skills

[![Install via skills.sh](https://img.shields.io/badge/skills.sh-install-green)](https://skills.sh/Huaqiu-Electronics/skills)

This repository contains [Agent Skills](https://agentskills.io/home) for Huaqiu EDA (Electronic Design Automation) products and technologies.

## Installation

```bash
npx skills add Huaqiu-Electronics/skills
```

Install a specific skill:

```bash
npx skills add Huaqiu-Electronics/skills --path eda/bom/get-bom
```

## Available Skills

Total: **109** capabilities across **17** domains.

- **Bom**
  - [**Get Bom**](./eda/bom/get-bom/SKILL.md)

- **Canvas**
  - [**Align Objects**](./eda/canvas/align-objects/SKILL.md)
  - [**Can Paste**](./eda/canvas/can-paste/SKILL.md)
  - [**Clear All Sel**](./eda/canvas/clear-all-sel/SKILL.md)
  - [**Copy Selected**](./eda/canvas/copy-selected/SKILL.md)
  - [**Delete Selected**](./eda/canvas/delete-selected/SKILL.md)
  - [**Distribute Objects**](./eda/canvas/distribute-objects/SKILL.md)
  - [**Get Align Type**](./eda/canvas/get-align-type/SKILL.md)
  - [**Get Selected Object Json**](./eda/canvas/get-selected-object-json/SKILL.md)
  - [**Get Selected Objects Json**](./eda/canvas/get-selected-objects-json/SKILL.md)
  - [**Mirror Objects**](./eda/canvas/mirror-objects/SKILL.md)
  - [**Move Selected Objs**](./eda/canvas/move-selected-objs/SKILL.md)
  - [**On Canvas Escape**](./eda/canvas/on-canvas-escape/SKILL.md)
  - [**Pan Canvas**](./eda/canvas/pan-canvas/SKILL.md)
  - [**Paste Selected**](./eda/canvas/paste-selected/SKILL.md)
  - [**Rotate Objects**](./eda/canvas/rotate-objects/SKILL.md)
  - [**Screen To Canvas Local**](./eda/canvas/screen-to-canvas-local/SKILL.md)
  - [**Select All**](./eda/canvas/select-all/SKILL.md)
  - [**Select Object At**](./eda/canvas/select-object-at/SKILL.md)
  - [**Set Align Type**](./eda/canvas/set-align-type/SKILL.md)
  - [**Set Page Size**](./eda/canvas/set-page-size/SKILL.md)
  - [**Set Page Size Rect**](./eda/canvas/set-page-size-rect/SKILL.md)
  - [**Zoom All**](./eda/canvas/zoom-all/SKILL.md)
  - [**Zoom Area By Double Box**](./eda/canvas/zoom-area-by-double-box/SKILL.md)
  - [**Zoom Area By Int Box**](./eda/canvas/zoom-area-by-int-box/SKILL.md)
  - [**Zoom Area By Points**](./eda/canvas/zoom-area-by-points/SKILL.md)
  - [**Zoom In**](./eda/canvas/zoom-in/SKILL.md)
  - [**Zoom Out**](./eda/canvas/zoom-out/SKILL.md)
  - [**Zoom Selected**](./eda/canvas/zoom-selected/SKILL.md)

- **Capability**
  - [**Get Capabilities**](./eda/capability/get-capabilities/SKILL.md)

- **Context**
  - [**Get Context**](./eda/context/get-context/SKILL.md)

- **Discovery**
  - [**Get Server Info**](./eda/discovery/get-server-info/SKILL.md)

- **Erc**
  - [**Clear All Findings**](./eda/erc/clear-all-findings/SKILL.md)
  - [**Clear Findings**](./eda/erc/clear-findings/SKILL.md)
  - [**Run Checks**](./eda/erc/run-checks/SKILL.md)
  - [**Set Erc Report Webview Visibility**](./eda/erc/set-erc-report-webview-visibility/SKILL.md)
  - [**Set Report Webview State**](./eda/erc/set-report-webview-state/SKILL.md)
  - [**Show Findings**](./eda/erc/show-findings/SKILL.md)

- **Event**
  - [**Subscribe**](./eda/event/subscribe/SKILL.md)

- **Export**
  - [**Export Bom**](./eda/export/export-bom/SKILL.md)
  - [**Export Target**](./eda/export/export-target/SKILL.md)

- **Graph**
  - [**Get Connectivity**](./eda/graph/get-connectivity/SKILL.md)
  - [**Query Graph**](./eda/graph/query-graph/SKILL.md)

- **Import**
  - [**Import Design**](./eda/import/import-design/SKILL.md)

- **Kernel**
  - [**Get Entity**](./eda/kernel/get-entity/SKILL.md)
  - [**Get Snapshot**](./eda/kernel/get-snapshot/SKILL.md)

- **Obj Place**
  - [**Add Bus Segment**](./eda/obj-place/add-bus-segment/SKILL.md)
  - [**Add Ellipse**](./eda/obj-place/add-ellipse/SKILL.md)
  - [**Add Free Line Segment**](./eda/obj-place/add-free-line-segment/SKILL.md)
  - [**Add Line**](./eda/obj-place/add-line/SKILL.md)
  - [**Add Rect**](./eda/obj-place/add-rect/SKILL.md)
  - [**Add Wire Segment**](./eda/obj-place/add-wire-segment/SKILL.md)
  - [**Cancel Bus Draw**](./eda/obj-place/cancel-bus-draw/SKILL.md)
  - [**Cancel Ellipse Arc Draw**](./eda/obj-place/cancel-ellipse-arc-draw/SKILL.md)
  - [**Cancel Ellipse Draw**](./eda/obj-place/cancel-ellipse-draw/SKILL.md)
  - [**Cancel Free Line Draw**](./eda/obj-place/cancel-free-line-draw/SKILL.md)
  - [**Cancel Line Draw**](./eda/obj-place/cancel-line-draw/SKILL.md)
  - [**Cancel Rect Draw**](./eda/obj-place/cancel-rect-draw/SKILL.md)
  - [**Cancel Wire Draw**](./eda/obj-place/cancel-wire-draw/SKILL.md)
  - [**Handle Bus Draw Click**](./eda/obj-place/handle-bus-draw-click/SKILL.md)
  - [**Handle Ellipse Arc Draw Click**](./eda/obj-place/handle-ellipse-arc-draw-click/SKILL.md)
  - [**Handle Ellipse Draw Click**](./eda/obj-place/handle-ellipse-draw-click/SKILL.md)
  - [**Handle Free Line Draw Click**](./eda/obj-place/handle-free-line-draw-click/SKILL.md)
  - [**Handle Image Draw Click**](./eda/obj-place/handle-image-draw-click/SKILL.md)
  - [**Handle Line Draw Click**](./eda/obj-place/handle-line-draw-click/SKILL.md)
  - [**Handle Net Alias Draw Click**](./eda/obj-place/handle-net-alias-draw-click/SKILL.md)
  - [**Handle Rect Draw Click**](./eda/obj-place/handle-rect-draw-click/SKILL.md)
  - [**Handle Table Draw Click**](./eda/obj-place/handle-table-draw-click/SKILL.md)
  - [**Handle Text Draw Click**](./eda/obj-place/handle-text-draw-click/SKILL.md)
  - [**Handle Wire Draw Click**](./eda/obj-place/handle-wire-draw-click/SKILL.md)
  - [**Place Bus**](./eda/obj-place/place-bus/SKILL.md)
  - [**Place Ellipse**](./eda/obj-place/place-ellipse/SKILL.md)
  - [**Place Ellipse Arc**](./eda/obj-place/place-ellipse-arc/SKILL.md)
  - [**Place Ellipse Arc From Virtual**](./eda/obj-place/place-ellipse-arc-from-virtual/SKILL.md)
  - [**Place Free Line**](./eda/obj-place/place-free-line/SKILL.md)
  - [**Place Image**](./eda/obj-place/place-image/SKILL.md)
  - [**Place Line**](./eda/obj-place/place-line/SKILL.md)
  - [**Place Net Alias**](./eda/obj-place/place-net-alias/SKILL.md)
  - [**Place Rect**](./eda/obj-place/place-rect/SKILL.md)
  - [**Place Table**](./eda/obj-place/place-table/SKILL.md)
  - [**Place Table From Virtual**](./eda/obj-place/place-table-from-virtual/SKILL.md)
  - [**Place Text**](./eda/obj-place/place-text/SKILL.md)
  - [**Place Text From Virtual**](./eda/obj-place/place-text-from-virtual/SKILL.md)
  - [**Place Wire**](./eda/obj-place/place-wire/SKILL.md)

- **Placement**
  - [**Cancel Block Draw**](./eda/placement/cancel-block-draw/SKILL.md)
  - [**Clear Net Alias Attach Obj**](./eda/placement/clear-net-alias-attach-obj/SKILL.md)
  - [**Handle Block Draw Click**](./eda/placement/handle-block-draw-click/SKILL.md)
  - [**Handle Part Draw Click**](./eda/placement/handle-part-draw-click/SKILL.md)
  - [**Handle Symbol Draw Click**](./eda/placement/handle-symbol-draw-click/SKILL.md)
  - [**Place Block**](./eda/placement/place-block/SKILL.md)
  - [**Place Part**](./eda/placement/place-part/SKILL.md)
  - [**Place Symbol**](./eda/placement/place-symbol/SKILL.md)
  - [**Set Net Alias Attach Obj**](./eda/placement/set-net-alias-attach-obj/SKILL.md)

- **Project**
  - [**Close Project**](./eda/project/close-project/SKILL.md)
  - [**Get Active Project**](./eda/project/get-active-project/SKILL.md)
  - [**Get Project**](./eda/project/get-project/SKILL.md)
  - [**List Open Projects**](./eda/project/list-open-projects/SKILL.md)
  - [**Open Project**](./eda/project/open-project/SKILL.md)
  - [**Save Project**](./eda/project/save-project/SKILL.md)

- **Runtime**
  - [**Execute Commands**](./eda/runtime/execute-commands/SKILL.md)
  - [**Validate Commands**](./eda/runtime/validate-commands/SKILL.md)

- **Selection**
  - [**Clear Selection**](./eda/selection/clear-selection/SKILL.md)
  - [**Get Selection**](./eda/selection/get-selection/SKILL.md)
  - [**Set Selection**](./eda/selection/set-selection/SKILL.md)

- **Transaction**
  - [**Commit**](./eda/transaction/commit/SKILL.md)
  - [**Open**](./eda/transaction/open/SKILL.md)
  - [**Redo**](./eda/transaction/redo/SKILL.md)
  - [**Rollback**](./eda/transaction/rollback/SKILL.md)
  - [**Undo**](./eda/transaction/undo/SKILL.md)

## Runtime Package

The [`@huaqiu/hqeda`](./hqeda/) npm package provides the shared TypeScript runtime that powers all skills. Each per-skill `SKILL.md` references the runtime via the `entry` field in its frontmatter.

```bash
npm install @huaqiu/hqeda
```

## License

Apache License 2.0 — see [LICENSE](./LICENSE).

## Feedback

Report issues or request new skills at [https://github.com/Huaqiu-Electronics/skills/issues](https://github.com/Huaqiu-Electronics/skills/issues).
