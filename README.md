# aqoc.github.io
A Question On Commands

This is a collection of frequently asked command-related / mapmaking questions, designed to be *super linkable*™. It also has search so you can search up your question.

## Contributing

To add a new faq, make a PR with it in `/faq/`. You can look at the other faqs for reference, but you need to have a header of the following kind:
```
---
layout: faq
title: Short Title
question: A question somebody may ask for this answer?
tags:
    - add
    - tags
    - here
summary:
    - various collections of words
    - each list item's words are related
    - only use keywords
---
```

`layout` should always be `faq` (unless you're making a redirect page, see [random](faq/random.md).  
`title` and `question` are fairly obvious.  
`tags` determines the tags that can be used to filter in the search bar. Look at pre-existing tags and ideally use those, though if you feel the need for a new tag, feel free to do so.
`summary` contains lists of collections of words for the search algorithm. See [Player NBT](faq/playernbt.md) for a good example.