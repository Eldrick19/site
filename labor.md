---
layout: page
title: "My Work"
---

<div class="project-row">
{% for project in site.data.projects %}
    <div class="project-column">
        <h4>{{ project.name }}</h4>
        <img src="{{ project.image }}" alt="{{ project.name }}">
        <p class="project-description">{{ project.description }}</p>
        <a href="{{ project.link }}">Learn More</a>
    </div>
    {% if forloop.index0 != 0 and forloop.index0 | modulo: 2 == 1 %}
        </div><div class="project-row">
    {% endif %}
{% endfor %}
</div>