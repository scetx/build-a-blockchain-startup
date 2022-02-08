---
layout: page
title: Schedule
permalink: /schedule/
---

# Schedule

<table style="table-layout: fixed; font-size: 80%;">
  <thead>
      <th style="width: 10%;"> Date </th>
      <th style="width: 30%;"> Class Materials </th>
      <th style="width: 50%;"> Assigned Materials </th>
      <!-- <th style="text-align:left; width: 10%;"> Quiz </th> -->
  </thead>
  <tbody>
    {% for row in site.data.schedule %}
    <tr>
      <td> {{ row.date }} </td>
      <td> {{ row.topic }}
        <br>
        {% if row.page %} <!-- Expects an INTERNAL URL -->
          [<a href="{{site.url}}{{site.baseurl}}{{row.page}}" style="font-size: 80%;">Class Notes</a>]
        {% endif %}
        {% if row.slides %} <!-- Expects an EXTERNAL URL -->
          [<a target="_blank" href="{{row.slides}}" style="font-size: 80%;">Slides</a>]
        {% endif %}
        {% if row.recording %} <!-- Expects an EXTERNAL URL -->
          [<a target="_blank" href="{{row.recording}}" style="font-size: 80%;text-decoration: underline;">Recording</a>]
        {% endif %}
      </td>
      <td>
        {% if row.material %} <!-- Handle an EXTERNAL or INTERNAL URL -->
        <ul>
          {% for r in row.material %}
            {% if r.file %} <!-- Expects an INTERNAL URL -->
              {% assign material_link = site.url | append: site.baseurl | append: r.file %}
            {% endif %}
            {% if r.link %} <!-- Expects an EXTERNAL URL -->
              {% assign material_link = r.link %}
            {% endif %}
          <li> <a target="_blank" href="{{material_link}}"> {{ r.name }} </a> </li>
          {% endfor %}
        </ul>
        {% else %}
		<ul>
		  <li><em>TBA</em></li>
        </ul>
        {% endif %}
      </td>
      <!-- <td>
        {% if row.quiz %}
          <a href="{{row.quiz.link}}" style="text-decoration: underline;">{{row.quiz.name}}</a>
        {% else %}
          None
        {% endif %}
      </td> -->
    </tr>
    {% endfor %}
  </tbody>
</table>
