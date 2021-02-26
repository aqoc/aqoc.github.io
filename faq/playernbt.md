---
layout: faq
---
# Player NBT Modification
> Why can't I modify a player's nbt?

The main thing to understand here is that NBT isn't how the game remembers entities; it's how they're stored in files. While the game's running, entities are stored as actual java objects. This means that accessing and modifying an entity's nbt goes something like:

Command: "Hey, can you pretend you're saving yourself?"  
Entity: "Sure. Here's my NBT."  
Command: "Thanks"  
Command: Modifies NBT  
Command: "Can you reload yourself in with this nbt?"  
Entity: "Sure"  
Entity: **Is reloaded into the game**  

Thus, if we wanted to modify a player's NBT, we'd need to kick the player out of the game and rejoin them. Which isn't a very good idea.

## [Alternatives](#alternatives)

Mojang is trying to allow us to do operations to the player, adding more commands every version. These commands act on the player object themselves and not the nbt; thus allowing the player to remain in the game.

There are some obvious ones:

- Effects: we can use `/effect`
- Advancements: we can use `/advancement`
- Tags: we can use `/tag`
- Scoreboards: we can use `/scoreboard`

But generally people figure out those on their own. One thing people struggle with a lot is *item modification*.

Of course, to give an item you can use `/give`. In 1.16, there's `/replaceitem`, which is slightly better but not useful if you want to *modify* an item. So you have some options (still 1.16):

- Use a loot table. This can work in some situations, using `loot replace` and `copy_nbt` functions inside of it.
- Use the [shulker box loot trick.](https://discord.com/channels/154777837382008833/689290423407083535/814970304098336809)

In 1.17, we have the lovely `/item` command, where we can define item modifiers! **Use it**.