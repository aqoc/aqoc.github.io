---
layout: faq
title: How do I simulate knockback on an entity?
tags:
    - damage
    - movement
    - entity
summary:
    - knockback entity push back
---

## Explosions

This is by far the simplest method: causing an explosion. To avoid damaging the terrain you can set `mobGriefing` to false and use a creeper with `Fuse: 0s`. Also giving the player resistance is a good idea.

**Example**:
> Knock the player backwards
> 
> ```
#> foo:part1
gamerule mobGriefing false
effect give @s resistance 1 127 true
summon creeper ^ ^ ^1 {Fuse: 0s}
schedule function foo:part2 1t
> ```
>
> ```
#> foo:part2
gamerule mobGriefing true
effect clear @a resistance
> ```

Of course, this comes with many disadvantages.

## Teleportation

You could teleport the player to an aec that has `Motion` backwards. This works well but is a bit jittery (since commands run at 20tps).