## What is this?

This is a collection of common questions related to commands, datapacks, and mapmaking in general.
I'll link you here if you ask me a common question.

## Contents

- [Counting](faq/counting.html)
- [Scheduling](faq/schedule.md)
- [Data packs](faq/datapack.md)
- [Function Tags](faq/functag.md)
- [Shootfacing](faq/shootfacing.md)
- [Player NBT Modification](faq/playernbt.md)
- [Optimization](faq/optimization.md)
- [Random Number Generation](faq/random.md)
- [Damage](faq/damage.md)

{% for page in site.pages %}
    {% if page.dir == '/faq/' %}
        - {{page.title}} [Tags: {% for tag in page.tags %} tag {% endfor %}]
    {% endif %}
{% endfor %}