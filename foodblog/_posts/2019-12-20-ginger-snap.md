---
layout: post
title:  "Ginger Snap Cookies"
date:   2019-12-20 
tags: food
feature-img: "/assets/gingersnap.png"
---
{% for recipe in site.data.recipes %}
  {% if recipe.name == page.title %}
	{% if recipe.intro %}
<p> {{ recipe.intro }}
	{% endif %}
	{% if recipe.site %}
You can find the <a href="{{ recipe.site }}">Original Recipe</a> here. </p>
	{% endif %}
    {% if recipe.name or recipe.instructions %}
**Mridu's Modifications:**
    {% endif %}
    {% if recipe.ingredients %}
<div class="card">
  <div class="container">
	<p><span style="font-weight: bold; color: #808080">Ingredients:</span></p>
	<ul>
	  {% if recipe.replace %}
	  <li> Replace </li>
	  {% endif %}
		<ul>
	  {% for ing_rep in recipe.replace %}
		  <li> <i> {{ing_rep[0]}} </i> with <b><i> {{ing_rep[1]}} </i></b></li>
	  {% endfor %}
		</ul>
	  {% if recipe.without %}
	  <li> Can do without </li>
	  {% endif %}
		<ul>
	  {% for ing in recipe.without %}
		  <li> <i> {{ing}} </i></li>	
	  {% endfor %}
		</ul>
	</ul>
  </div>
</div>
<br>
	{% endif %}
    {% if recipe.instructions %}
<div class="card">
  <div class="container">
	<p><span style="font-weight: bold; color: #808080">Instructions:</span></p>
	<ul>
	{% for instr in recipe.instructions %}
	  <li> {{instr}} </li>	
	{% endfor %}
	</ul>
  </div>
</div>
<br>
	{% endif %}
  {% endif %}
{% endfor %}
