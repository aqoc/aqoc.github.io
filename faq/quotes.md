---
layout: faq
title: Escaping Quotes
question: Why is my string giving an error?
tags:
    - string
    - nbt
summary:
    - quotes strings
    - unexpected invalid
    - escape backslash
---

Say you have a string like `"{Tags: ["aqoc"]}"`. It's not working. Why? Because when minecraft sees `"aqoc`, it sees the quote and ends the string. Thus it starts reading `aqoc` not as a string and is confused. You have two ways to fix this:

- Put a backslash `\` before the quote. This will indicate to take the quote literally and not end the string.
- Use single quotes `'`. Since you started the string with double quotes `"`, it won't end the string.

So in our example, we get either `"{Tags: [\"aqoc\"]}"` or `"{Tags: ['aqoc']}"`.

## [Nesting](#nesting)

Sometimes you can have nested quote sets, e.g `"{display: {Name: "{"text":"Hello!"}"}}"`. In this case, you need to remember to escape at each string level. In this case you could do `"{display: {Name: '{\"text\":\"Hello!\"}'}}"`:

- At the top level, `"{display: {Name: '{\"text\":\"Hello!\"}'}}"`, all quotes are escaped
- In `display.Name` we have `'{"text":"Hello!"}'` where all quotes are still escaped
- And then in the final two strings there are no extra quotes