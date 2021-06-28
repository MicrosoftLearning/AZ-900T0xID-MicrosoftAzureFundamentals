---
title: Petunjuk Host Online
permalink: index.html
layout: home
---

# Direktori Konten

Hyperlink untuk setiap penelusuran. Instruktur dapat memilih untuk menggunakan penelusuran sebagai demonstrasi atau lab siswa. 

## Panduan

{% assign wts = site.pages | where_exp:"page", "page.url contains '/Instructions/Walkthroughs'" %}
| Modul | Panduan |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

