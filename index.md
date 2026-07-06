---
layout: default
title: Home
---
<h1>{{ site.title }}</h1>
<p>{{ site.tagline }}</p>

<p>Quattro categorie per ora — se ne aggiungono altre semplicemente creando
una nuova cartella con lo stesso schema di questa. Ogni pagina appartiene
a una categoria e può linkare liberamente alle altre.</p>

<ul class="elenco-pagine">
  {% for c in site.categorie %}
  <li>
    <a href="{{ '/' | append: c.slug | append: '/' | relative_url }}">{{ c.nome }}</a>
    <p>{{ c.descrizione }}</p>
  </li>
  {% endfor %}
</ul>
