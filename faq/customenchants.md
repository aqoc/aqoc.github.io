---
layout: faq
title: Custom Enchantments
question: How do I make custom enchantments?
tags:
    - enchantments
summary:
    - custom own enchant enchantments enchants
    - can possible hardcode enchant
---

In short, **you can't**. The vanilla ones are hardcoded, so you'll have a lot of trouble trying to do it with datapacks.

That said, you can try to replicate the enchantment system. This has drawbacks:
- Doesn't work on anvils
- Doesn't work in enchantment tables
- Doesn't work in grindstones

But, if you're making, say, a map, it could help. Basically, you apply a custom lore to the item that mimics enchantment lore. You also tag the item, and run ticking functions that perform whatever you want the enchantment to be.