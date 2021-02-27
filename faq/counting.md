---
title: Counting
question: How do I count the number of <i>x</i>?
layout: faq
tags:
    - score
    - entity
    - item
summary:
    - count entities entity score
    - count items item score
---

## [Entities](#entities)

The `execute if entity` subcommand returns the number of entities selected, if no `run` command was given. Thus we can use
```
execute store result score <fakeplayer> <objective> if entity <selector>
```
to count something.

**Example**:
> Summon a new cow if there are less than 2 in a 5 block radius:
>
> ```
# Create an objective (you probably already have one)
scoreboard objectives add general
# Count the cows
execute store result score #cows general if entity @e[type=cow,distance=..5]
# If we have less than 2, summon a new one
execute if score #cows general matches ..1 run summon cow
> ```

## [Items](#items)

The `clear` command, when used with a `0` count, has special behaviour; it clears no items but returns how many there are in the inventory. So we can do something like
```
execute store result score <fakeplayer> <objective> run clear @s diamond_shovel 0
```
We can even check for nbt tags:
```
execute store result score <fakeplayer> <objective> run clear @s diamond_shovel{Unbreakable:1b} 0
```

**Example**:
> Count how much sand a player has
> ```
# Create an objective
scoreboard objectives add general
# Count the sand
execute store result #sand general run clear @s sand 0
> ```