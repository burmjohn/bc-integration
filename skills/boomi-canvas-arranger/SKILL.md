---
name: boomi-canvas-arranger
description: Arrange Boomi process component XML after process creation or modification. Use when a Boomi process canvas needs step-path integrity checks, orphaned shape review, or readable shape and dragpoint layout without deleting process shapes.
---

# Boomi Canvas Arranger

Use this skill after a Boomi process has been created or modified and the
process XML needs readable canvas layout or step-path integrity review.

## Critical rules

- Never delete shapes.
- Be conservative about auto-wiring disconnected shapes.
- Preserve existing structure where possible.
- Use "step-path" for dragpoint linkages between shapes. In Boomi, "connection"
  usually means connector connection components.

## Step-path integrity

Check these issues before changing layout:

- Non-terminal shapes with no outbound dragpoint path.
- Orphaned shapes that are not reachable from the Start shape.
- Branch, Decision, or Route outputs that still have `toShape="unset"`.

Terminal shapes that do not require outbound paths include `stop`,
`returndocuments`, and Process Call shapes with no return path configured.

## Layout guidance

- Main flow should move left to right.
- Start shape typically begins near `x="48.0"` and `y="46.0"`.
- Use about `192px` horizontal spacing between sequential shapes.
- Use `128px` to `224px` vertical spacing between major branches.
- Use about `112px` vertical offset for smaller sub-branches.
- Put merge points to the right of all branch endpoints and vertically toward
  shorter branches to avoid confusing connector lines.

## Working process

1. Read the process component XML.
2. Map all shapes and dragpoint `toShape` references.
3. Report broken paths, orphaned shapes, or incomplete branch outputs.
4. If layout needs improvement, update shape `x` and `y` positions and
   dragpoint coordinates with minimal changes.
5. Report integrity findings and layout changes.

## XML reference

```xml
<shape name="shape1" shapetype="start" x="48.0" y="46.0">
  <dragpoints>
    <dragpoint name="shape1.dragpoint1" toShape="shape2" x="224.0" y="56.0"/>
  </dragpoints>
</shape>
```
