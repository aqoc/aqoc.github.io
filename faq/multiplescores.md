---
layout: faq
title: Multiple Scores
question: How can I display multiple scores in the sidebar?
tags:
    - score
    - player
summary:
    - score display multiple many lots sidebar
---

Unfortunately, you can't. There's a few alternatives:

## Different locations
There are 3 different locations you can put objectives in: `belowName`, `list`, and `sidebar`. So you can display up to 3 objectives in those.

## Custom actionbar
You can create a custom actionbar (or other text form) that displays them, making use of the score json text component:

```json
{
    "score": {
        "name": "@s",
        "objective": "<objective>"
    }
}
```