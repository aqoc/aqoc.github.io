---
layout: faq
title: Scoreboards
question: What is a scoreboard?
tags:
    - score
    - player
summary:
    - scoreboard track values store data per player entity maths
---

Scoreboards are a way to keep track of numbers for different players separately. You can use them in many many different ways, one obvious one being...a score board.

## [Creating a scoreboard](#creation)

```
scoreboard objectives add <objective> <criterion>
```

`<objective>` is the name of the scoreboard you want to create, which is referred to as an objective.  
`<crierion>` is the criterion used to add to this scoreboard. There are many special ones like `health` that make the board represent a player's health; but **most use `dummy`**, which gives you the most control.

## [Setting a player's value](#setting)

To set a player's value:

```
scoreboard players set <target> <objective> <value>
```

Pretty self explanatory.

You can also add/remove:

```
scoreboard players <add|remove> <target> <objective> <value>
```

You can delete an entry:

```
scoreboard players reset <target> <objective>
```

## [Displaying](#display)

Use `scoreboard objectives setdisplay <location>` to display a score. There are 3 common locations:
- `sidebar` - puts it on the side of the screen
- `belowName` - shows each player's score under their name
- `list` - puts it next to each player's name in the tab list

(see [displaying multiple scores](multiplescores.md))

## [Fake players](#fakeplayers)

Often people use scoreboards to do maths and hold non-player-specific values. This is where fake players come in! You can use any name to store a scoreboard entry, even if it's not a valid username. Many people thus prefix names with a `$` or a `#`. `#` has slightly special behaviour in that it's hidden from the sidebar.

Also note that not only players can have scoreboard entries; other entities can, too.