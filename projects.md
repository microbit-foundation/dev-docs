---
layout: page
order:
title: micro:bit labs
heading: micro:bit labs
description: Current, historic and work in progress research and development projects relating to technical aspects of the micro:bit.
permalink: /labs/
ref: projects
lang: en
---

This page collates technical projects, research and development that have been done on/with the BBC micro:bit in universities, labs, clubs and schools around the world. It has been created by the micro:bit community, and you are welcome to submit any of your own work to it by [submitting a project template](https://github.com/microbit-foundation/dev-docs/issues/new?template=labs.md)

If you’d like to see [research about the impact of micro:bit, head over to our main site](https://microbit.org/research/). 

---  

[Add your research/project to the lab](https://github.com/microbit-foundation/dev-docs/issues/new?template=labs.md){: .btn.btn-info}

{% for projects in site.projects %}
  {% if projects.post_filter contains 'projects' %}
  <div class="project-post">
  <h2>
    <a href="{{ projects.permalink }}">
    {{ projects.title }}
    </a>
  </h2>
  <p>{{ projects.description | markdownify }}</p>
  <div class="categories">
    {% assign sortedCategories = projects.categories | sort %}
    {% for category in sortedCategories %}
        <span class="category">
            <a href="/projects/category/{{ category }}" class="btn btn-info">{{ category }}</a>
        </span>
    {% endfor %}
  </div>
  </div>

  {% endif %}
{% endfor %}
