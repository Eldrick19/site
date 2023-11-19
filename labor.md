---
layout: page
title: "Some Things I've Done"
---

{% assign grouped_projects = site.data.projects | group_by:"category" %}

{% for group in grouped_projects %}
<hr/>
<h3>{{ group.name }}</h3>
<div class="project-row">
{% for project in group.items %}
{% assign is_second_in_row = forloop.index0 | modulo: 2 %}
<div class="project-column">
    <h5>{{ project.name }}</h5>
    <br/>
    <a href="{{ project.link }}"><img class="project-image" src="{{ project.image }}" alt="{{ project.name }}"></a>    
    <p class="project-description">{{ project.description }}</p>
</div>
{% if forloop.index0 != 0 and is_second_in_row == 0 %}
</div>
<div class="project-row">
{% elsif forloop.index0 == 0 %}
</div>
<div class="project-row">
{% endif %}
{% endfor %}
</div>
{% endfor %}