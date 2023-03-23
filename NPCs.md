---
layout: page
title: NPCs
type: title
inHeader: true
---
{% assign cities = site.pages | where: 'type', 'city' %}
<div class="row">
{% for city in cities %}
{% assign npcs = site.pages | where_exp: 'item', 'item.dir contains city.dir' | where: 'type', 'npc' %}
{% if npcs %}
<div class="column cell">
### [{{ city.title }}]({{ locationPage.url | relative_url}})
{% assign npcs_by_location = npcs | group_by: 'location' %}
{% for npc_locations in npcs_by_location %}
{% if npc_locations.name != "" %}
{% assign locationPage = site.pages | where_exp: 'item', 'item.name contains npc_locations.name' | first %}
#### [{{ locationPage.title }}]({{ locationPage.url | relative_url}})
{% else %}
#### Not Specified
{% endif %}
{% for subpage in npc_locations.items %}
* [{{ subpage.title }}]({{ subpage.url | relative_url}})
{% endfor %}
{% endfor %}
{% endif %}
</div>
{% endfor %}
</div>


<!-- ### City NPCs
{% assign current_dir = page.dir %}
{% assign npcs = site.pages | where_exp: 'item', 'item.dir contains current_dir' | where: 'type', 'npc' %}
{% assign npcs_by_location = npcs | group_by: 'location' %}
{% for npc_locations in npcs_by_location %}
{% if npc_locations.name != "" %}
{% assign locationPage = site.pages | where_exp: 'item', 'item.name contains npc_locations.name' | first %}
{% assign cityPage = site.pages | where_exp: 'item', 'item.name contains locationPage.city' | first %}
#### [{{ locationPage.title }}]({{ locationPage.url | relative_url}}) {% if cityPage %} ([{{ cityPage.title }}]({{ cityPage.url | relative_url}})) {% endif %}
{% else %}
#### Undefined
{% endif %}
{% for subpage in npc_locations.items %}
* [{{ subpage.title }}]({{ subpage.url | relative_url}})
{% endfor %}
{% endfor %} -->