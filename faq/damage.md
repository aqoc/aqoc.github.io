---
title: Health manipulation
question: How can I damage/heal the player?
layout: faq
tags:
    - player
    - attribute
    - effect
    - damage
summary:
    - damage hurt heal modify health player
    - effect instant damage health
    - attribute max health
---

## [Instant health/damage](#instant)
The simplest way is through instant health / damage.

**Example**:
> Deal 6 hearts of damage to the player
>
> ```
effect give @s instant_damage 1 1
> ```

## [Attributes](#attributes)
This is slightly more complex but allows far more precise manipulation.

1. Set the target's `generic.max_health` attribute to the desired value
2. Give the target instant health
3. Reset the target's `generic.max_health`

**Example**:
> Deal 2 hearts of damage to the player
>
> ```
attribute @s generic.max_health base set 16
effect give @s instant_health 1 10 true
attribute @s generic.max_health base set 20
> ```