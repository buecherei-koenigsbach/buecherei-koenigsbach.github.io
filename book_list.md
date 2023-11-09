---
title: Bücherliste
layout: default
---

<h1>{{ page.title }}</h1>

<ul>
  {% for book in site.data.books %}
    <li>
      <strong>Titel:</strong> {{ book.Title }} <br>
      <strong>Autor:</strong> {{ book.Author }} <br>
      <strong>Verlag:</strong> {{ book.Publisher }} <br>
      <strong>Veröffentlichungsdatum:</strong> {{ book['Published Date'] }} <br>
      <strong>ISBN:</strong> {{ book.ISBN }} <br>
      <img src="{{ book['Image URL'] }}" alt="Buchcover" height="150"><br>
    </li>
  {% endfor %}
</ul>
