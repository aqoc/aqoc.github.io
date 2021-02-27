---
title: Scheduling
question: How can I run a command after a delay?
layout: faq
tags:
    - function
    - score
---

## [The `schedule` command](#schedule)

This is by far the simplest method. Put your second command into a new function, and use the `schedule` command:
```
schedule function <function> <time>
```
The time can either be ticks (`5t`), seconds (`10s`), or in-game days (`1d`). As you can see, the unit indicates which type it is.

**Example**:
> Say "hello", then "world" 10 seconds later
>
> ```
#> foo:function1.mcfunction
say hello
schedule function foo:function2 10s
> ```
>
> ```
#> foo:function2.mcfunction
say world
> ```

## [Scoreboard timers](#score)

If, for whatever reason, you don't want to schedule a command, you can use a scoreboard timer. To make one, you

- Define an objective
- Set a time score to 0 (e.g `scoreboard players set #time <objective> 0`)
- Then, every tick, add 1 to the time score (e.g `scoreboard players add #time <objective> 1`)
- You then check every tick if the time matches the target number

**Example**:
> Say "hello", then "world" 10 seconds `(=200 ticks)` later
>
> ```
#> foo:function1.mcfunction
say hello
# Initialise the timer
scoreboard players set #time global 0
> ```
>
> ```
#> foo:tick.mcfunction
# Increment the timer
scoreboard players add #time global 1
# Run the second command
execute if score #time global matches 200 run say world
> ```