---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
title: Does a 30 Hit - D&D Campaign
---

Welcome to the world of **Bavleri**, the setting for our D&D campaign "Does a 30 Hit". 

## [Bavleri](./Bavleri/Bavleri)

## World Events
<div class="row">
{% assign events = site.events | sort: 'gameDate' | reverse %}
{% for event in events %}
<div class="column bordered-cell">
<span class="post-meta">{{event.gameDate | date: "%b %d, %Y"}}</span>
{{event}}

</div>
{% endfor %}
</div>

## Archived Stories
<div class="column">
{% assign stories = site.archivedStories | sort: 'gameDate' | reverse %}
{% for story in stories %}
<div class="bordered-cell">
<a href="{{story.url | relative_url}}" target="_blank">{{story.title}}</a>

Start: `{{story.gameDate}}`

Completed: `{{story.completedDate}}`

</div>
{% endfor %}
</div>