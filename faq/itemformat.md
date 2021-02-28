---
title: Item Format
question: How is item NBT saved?
layout: faq
tags:
    - item
    - nbt
    - entity
summary:
    - item format nbt tag
    - item entity tag
    - item inventory tag
    - count slot id
---

## [In an inventory](#inventory)
In an inventory, items are stored in the format

```
{
    Slot: 0b,
    id: "minecraft:dirt",
    Count: 1b,
    tag: {...} 
}
```

- `Slot` represents the slot the item is in
- `id` is the item's type's id
- `Count` is the size of the item's stack
- `tag` contains other data for the item

## [As an entity](#entity)
As an entity, items are stored in the format

```
{
    Item: {
        id: "minecraft:dirt",
        Count: 1b,
        tag: {...}
    }
}
```

- `id` is the item's type's id
- `Count` is the size of the item's stack
- `tag` contains other data for the item

It's very similar to as an inventory.