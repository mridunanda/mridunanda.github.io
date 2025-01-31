---
title: "Projects"
permalink: /projects/
layout: single
author_profile: true
---

The following is a list of unpublished but substantial projects I worked on during my undergraduate studies. I hope to further develop some of these ideas in the future.

{% for project in site.projects %}
### {{ project.title }}
{{ project.description }}

{{project.completion}}{% if project.paper_link %} | See [[Paper]]({{ project.paper_link }}){% endif %}{% if project.repo_link %} [[Code]]({{ project.repo_link }}){% endif %}

---
{% endfor %}