---
title: As vs At
question: When should I use <code>as</code> or <code>at</code> in <code>execute</code>?
layout: faq
tags:
    - execute
summary:
    - as vs at execute
---

## [`execute as`](#as)

`execute as` changes the *executor* of the command, or the "who". After using it, `@s` will reference what was set. If you `execute as` multiple entities, the command will be run for each entity, with `@s` referring to the current entity being run as.

**Example**:
> Make every sheep become `NoAI:1b`
> 
> ```
> execute as @e[type=sheep] run data modify entity @s NoAI set value 1b
> ```

## [`execute at`](#at)

`execute at` changes the *location* of the command, or the "where". After using it, `~ ~ ~` will reference the position of the set entity. If you `execute at` multiple entities, the command will be run for each entity, at each's respective position.

**Example**:
> Set the block under every sheep to be a diamond block
> 
> ```
> execute at @e[type=sheep] run setblock ~ ~-1 ~ diamond_block
> ```

## Or, you could use both.

`execute as @selector at @s` is very common. Don't try to do `execute as @selector at @selector` because this runs the command for every entity specified; then runs the command *at* every entity specified. Remember,

```
execute as @e at @e
```
is equivalent to
```
execute as @e run execute at @e
```
(see [why you shouldn't do this though](runexecute.md))

which would mean:
- For every entity, run the following as `@s`
- For every entity, run the following with `~ ~ ~`

And thus commands are run way too many times; and not at the targeted entity's position. **Use `at @s`**.