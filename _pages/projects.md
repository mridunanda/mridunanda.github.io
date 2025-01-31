---
title: "Projects"
permalink: /projects/
layout: single
author_profile: true
---

The following is a list of unpublished but substantial projects I worked on during my undergraduate studies. I hope to have the opportunity to further develop some of these ideas in the future. In the meantime, feel free to explore the projects listed below.


{% for project in site.projects %}
### {{ project.title }}
{{ project.description }}

- [Paper Link]({{ project.paper_link }})
- [Code Repository]({{ project.repo_link }})

---
{% endfor %}