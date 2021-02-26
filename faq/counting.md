# Counting

> How do I count the number of *x*?

## [Entities](#entities)

The `execute if entity` subcommand returns the number of entities selected, if no `run` command was given. Thus we can use
```
execute store result <fakeplayer> <objective> if entity <selector>
```
to count something. For example, to summon a new cow if there are less than 2 in a 5 block radius:
```
# Create an objective (you probably already have one)
scoreboard objectives add general
# Count the cows
execute store result #cows general if entity @e[type=cow,distance=..5]
# If we have less than 2, summon a new one
execute if score #cows general matches ..1 run summon cow
```

## [Items](#items)

