---
layout: archive
title: "Site Haritası"
permalink: /sitemap/
author_profile: false
---

Bütün içeriklere buradan ulaşabilirsiniz.

<font color="red"><h2>Sayfalar</h2></font>
{% for post in site.pages %}
  {% include archive-single.html %}
{% endfor %}

<font color="red"><h2>Gönderiler</h2></font>
{% for post in site.posts %}
  {% include archive-single.html %}
{% endfor %}

{% capture written_label %}'None'{% endcapture %}

{% for collection in site.collections %}
{% unless collection.output == false or collection.label == "posts" %}
  {% capture label %}{{ collection.label }}{% endcapture %}
  {% if label != written_label %}
  <h2>{{ label }}</h2>
  {% capture written_label %}{{ label }}{% endcapture %}
  {% endif %}
{% endunless %}
{% for post in collection.docs %}
  {% unless collection.output == false or collection.label == "posts" %}
  {% include archive-single.html %}
  {% endunless %}
{% endfor %}
{% endfor %}
