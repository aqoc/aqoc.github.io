---
layout: faq
tags:
    - selector
    - nbt
    - function
    - advancement
---
# Optimization
> How can I optimize my functions?

Always remember the number one rule of optimization, and that is:

> don't.

This faq will cover how to optimize your functions, but be warned: **if you don't fully understand what you're doing, don't do it**. You're likely to hurt your program. Here's an example. Someone wants to optimize this command:
```
execute as @e[tag=foo] run data modify entity @s NoGravity set value 1b
```
and they think "What if we limited it to only select things with no gravity already?"
```
execute as @e[tag=foo,nbt={NoGravity:0b}] run data modify entity @s NoGravity set value 1b
```
The problem is, the second one *deserializes too*. It's far less efficient. As explained [here](playernbt.md), an entity doesn't store its nbt; it's dynamically created on the fly. Thus, selecting with the nbt predicate means the entity has to fully deserialize themselves, like saving a world.

The second version only requires the entity serialize themselves, like loading in a world (the first still requires this).

That aside, here are some optimization tips

## [NBT](#nbt)

Avoid NBT as much as possible. You can often replace nbt selectors with predicates, which don't operate on nbt. This avoids entity serialization. NBT modifications are a bit less avoidable, but try to limit them to one command only.

**Storage NBT** is not inefficient like normal nbt, so use it to help reduce operations. For example, you could turn
```
data modify entity @s Foo set from entity @p Foo
data modify entity @s Bar set from entity @p Bar
data modify entity @s Quux set from entity @p Quux
```
into
```
data modify storage foo Player set from entity @p {}
data modify storage foo Target set value {}
data modify storage foo Target.Foo set from storage Player.Foo
data modify storage foo Target.Bar set from storage Player.Bar
data modify storage foo Target.Quux set from storage Player.Quux
data modify entity @s {} merge from storage foo Target
```
It's more verbose, but only has one serializing and deserializing operation. *Remember, NBT isn't cached at all*.

As a note, multiple operations in a `copy_nbt` item modifier are fine, since they all act on the same NBT.

There are a few more things you can do, like replacing an item id check every tick with a tagged system (ask me about that, since that wasn't clear at all).

## [Ticking functions](#ticking)

Minimize commands in a ticking function. It's a simple as using advancement triggers instead.

## [Selectors](#selectors)
Every time you use a selector, it has to filter through the whole list of entities in the world. Here are some guidelines:

- Always include `type` if you can, and at the beginning. This significantly reduces the entities needed to check.
- Look at [this page](https://minecraftcommands.github.io/commanders-handbook/selector-argument-order) for a full list of optimal orders
- Don't use nbt selectors, where possible. Use predicates instead.

Also think about whether you need something extra on a selector! A common "optimization" I see is:
```
execute if entity @e[type=item,limit=1] run ...
```
Note the `limit=1`. Let's see how the game processes it without it:

- Get the list of all entities
- Make a new list, only containing the items
- Is the list empty?

Now with it:

- Get the list of all entities
- Make a new list, only containing the items
- **Make another new list, containing the first item**
- Is the list empty?

`limit=1` still is another filter step; passing items are transferred to a new list. As you can see, it's clearly less efficient; in fact, it requires an allocation, which is definitely inefficient.