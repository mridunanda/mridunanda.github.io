---
title: Projects
permalink: /projects
layout: default
---

# Projects

Here's a (very incomplete) list of coding projects that I've worked on over time.
Starred are the projects that are most important to me.

{% for project in site.data.projects %}
  <a name="{{ project.name }}"/>
  <div class="card mb-3">
    <div class="card-body">
      <h5 class="card-title">{% if project.favorite %}<i class="fas fa-star" data-fa-transform="shrink-3"></i>{% endif %} {{ project.title }}</h5>
      <h6 class="card-subtitle mb-2 text-muted"><strong>{{ project.author }}</strong></h6>

      <p class="card-text">{{ project.description | markdownify }}</p>

      <p>Software: <em>{{ project.software }}</em></p>

      {% if project.source %}
        <a href="{{ project.source }}" target="_blank" class="btn btn-primary"><i class="fas fa-code"></i> Code</a>
      {% endif %}

      {% if project.site %}
        <a href="{{ project.site }}" target="_blank" class="btn btn-primary"><i class="fas fa-globe"></i> Site</a>
      {% endif %}
    </div>
  </div>
{% endfor %}
