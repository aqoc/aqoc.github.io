---
layout: faq
title: Tags
question: How can I select many types at once?
tags:
    - datapack
    - tags
summary:
    - many multiple or condition
    - types entities blocks id
    - select variety
    - hostile peaceful passive group
    - tag tags
---

You can use tags. These are json files in the `data/<namespace>/tags` folder in your [datapack](datapack.md). There are many different tag types that go in various sub-folders:
    - `entity_types` for entity tags
    - `items` for item tags
    - `blocks` for block tags
    - `functions` for function tags

For example, to define a hostile mob tag, you could make a file `data/<namespace>/tags/entity_types/hostile.json`. The format is fairly simple:
```json-doc
{
    "replace": false,   // Optional. Don't set to true.
    "values": [         // A list of values this tag holds
        "namespace:id", // Represents a fixed id
        "#namespace:id" // Includes another tag
    ]
}
```

For example, a simple hostile mob tag would start
```json-doc
{
    "values": [
        "minecraft:creeper",
        "minecraft:skeleton",
        "minecraft:zombie"
        // ...
    ]
}
```