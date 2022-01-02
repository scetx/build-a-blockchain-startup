---
layout: title-page
title: Schedule
permalink: /schedule/
---


<table style="table-layout: fixed; font-size: 80%;">
  <thead>
      <th style="text-align:left; width: 10%;"> Date </th>
      <!-- <th style="text-align:left; width: 10%;"> Quiz </th> -->
      <th style="text-align:left; width: 50%;"> Topic </th>
      <th style="text-align:left; width: 30%;"> Readings </th>
  </thead>
  <tbody>
    {% for row in site.data.schedule %}
    <tr>
      <td> {{ row.date }} </td>
      <!-- <td> 
        {% if row.quiz %} 
          <a target="_parent" href="{{row.quiz.link}}" style="text-decoration: underline;">{{row.quiz.name}}</a>
        {% else %}
          None
        {% endif %}
      </td> -->
      <td> {{ row.topic }} 
        <br>
        {% if row.slides %}
          [<a target="_parent" href="{{site.url}}{{row.class}}" style="font-size: 80%;">Class Notes</a>]
        {% endif %}
        {% if row.slides %}
          [<a target="_parent" href="{{site.url}}{{row.slides}}" style="font-size: 80%;">Slides</a>]
        {% endif %}
        {% if row.recording %}
          [<a target="_parent" href="{{row.recording}}" style="font-size: 80%;text-decoration: underline;">Recording</a>]
        {% endif %}
      </td>
      <td> 
        {% if row.reading %}
        <ul style="margin-bottom: 0;">
          {% for r in row.reading %}
            {% if r.file %}
              {% assign reading_link = site.url | append: r.file %}
            {% endif %}
            {% if r.link %}
              {% assign reading_link = r.link %}
            {% endif %}
          <li> <a target="_parent" href="{{reading_link}}"> {{ r.name }} </a> </li>
          {% endfor %}
        </ul>
        {% endif %}
      </td>
    </tr>
    {% endfor %}
  </tbody>
</table>

