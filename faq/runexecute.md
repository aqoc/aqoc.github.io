---
title: Run Execute
question: Why is <code>run execute</code> unnecessary?
layout: faq
tags:
    - execute
    - unnecessary
summary:
    - run execute unnecessary unneeded invalid
---

**Because execute automatically chains its subcommands like this.**

For example, the following command:
```
execute as @a at @s if score @s global matches 1.. run say hi
```
is (more or less) internally converted to:
```
execute as @a run execute at @s run if score @s global matches 1.. run say hi
```

Using `execute ... run execute ...` clogs up your code and is 100% never needed. Remove it.