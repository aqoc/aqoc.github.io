# AQOC

## What is this?

This is a collection of common questions related to commands, datapacks, and mapmaking in general.
I'll link you here if you ask me a common question.

## Search

{% include search.html %}

## Contents

{% for page in site.pages %}
    {% if page.dir == '/faq/' %}
- [{{page.title}}]({{page.url}})
    {% endif %}
{% endfor %}