---
layout: faq
title: Raycasting
question: How do I get the block/entity an entity is looking at?
tags:
    - coordinates
    - rotation
    - entity
summary:
    - raycasting ray cast
    - looking seeing cursor
    - target block entity player mob
---

*This assumes knowledge of [local coordinates](local.md)*

Raycasting is a method of "drawing" a line from the head of a mob to detect where it's looking. We start at the mob's head, then gradually go forwards using local coordinates. We keep going forwards until we find the target, accomplished using recursion. It's best explained in an example:

**Example**:
> Set the block a player is looking at to a diamond block
> 
> ```
#> foo:start_raycast
execute as @a anchored eyes positioned ^ ^ ^ run function foo:raycast
> ```
> 
> ```
#> foo:raycast
execute unless block ~ ~ ~ #air run setblock ~ ~ ~ diamond_block
execute if block ~ ~ ~ #air positioned ^ ^ ^0.1 run function foo:raycast
> ```

You can fine-tune the `0.1`; a larger value is less accurate, and a smaller value makes more function calls. 0.1 is usually a good step but you might want to try 0.05.

Give up? You can use [vdvman's raycast generator](https://skylinerw.com/vdvman1/raycast/)