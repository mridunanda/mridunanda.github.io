---
layout: default 
title: Projects 
permalink: /projects 
---

<h2 class="post-list-heading">{{ page.title | default: "Projects" }} </h2>

{% for project in site.data.projects %}
<div class="card">
  <div class="container">
	<h2> {{ project.title }} </h2>
	<h3> {{ project.author }} </h3>
  	<p>Software: <em>{{ project.software }}</em></p>
  	<p class="card-text">{{ project.description | markdownify }}</p>
	{% if project.source %}
  	  <a href="{{ project.source }}" class="button">Code</a>
	{% endif %}
	{% if project.site %}
  	  <a href="{{ project.site }}" class="button">Site</a>
	{% endif %}
  </div>
</div>
<br>
{% endfor %}
