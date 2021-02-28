---
layout: faq
title: Local Coordinates
question: How can I target locations relative to the player's rotation?
tags:
    - coordinates
    - rotation
summary:
    - local coordinates coords caret ^
    - direction entity player facing rotation rotate
---

Local coordinates are represented by a caret: `^`. You use them to indicate a position *relative to the way an entity is facing*. They go

```
^left ^up ^forward
```

**Example**:
> Target the block 3 blocks in front of the player
>
> ```
execute as @a at @s positioned ^ ^ ^3
> ```

## [Eyes and feet](#anchor)

You can use `execute anchored eyes` or `execute anchored feet` to align local coordinates to an entity's eyes and feet, respectively. Much of the time you want to anchor to the eyes. Note that this only affects local coordinates; doing `execute anchored eyes positioned ~ ~ ~` is positioned at the entity's feet.

## [Mixing](#mixing)

These cannot be combined with other coordinates (e.g `~ ~ ^` is invalid). If you need to do so, use something like

**Example**:
> Target the block 3 blocks up relative to the player, but at x 0.
>
> ```
execute as @a at @s positioned ^ ^3 ^ positioned 0 ~ ~
> ```