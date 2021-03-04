---
layout: faq
title: "@s in command blocks"
question: Why isn't <code>@s</code> working in a command block?
tags:
    - commandblock
    - execute
summary:
    - s command block broken not working
---

A command block runs as the server, so `@s` doesn't reference an entity. Perhaps you meant

```
execute as @a at @s run ...
```

(see [here](asvat.md) for info on exactly what you need here)