---
layout: faq
---
# Function tags

> How do I run a function every tick, or when my data pack loads?

You use *function tags*!

## Function tags
These go in the folder `data/minecraft/tags/functions` and are lists of functions, telling minecraft to do something special with them. Currently, there are only two (that have special behaviour): `tick.json` which runs functions every tick; and `load.json` which runs functions on `/reload`. One of these files looks something like

```json
{
    "values": [
        "<function identifier here>"
    ]
}
```

That's it! Note how they go in the minecraft namespace instead of your own; they won't work in another namespace (your functions should still be in your custom namespace however).

**Example**:
> Say hi every tick
>
> ```
#> data/hello/functions/hi.mcfunction
say hi
> ```
>
> ```json
// data/minecraft/tags/functions/tick.json
{
    "values": [
        "hello:hi"
    ]
}
> ```