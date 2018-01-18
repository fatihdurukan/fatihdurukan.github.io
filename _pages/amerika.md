---
title: "Amerika (ABD)"
layout: splash
permalink: /amerika/

header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: /assets/images/newyork.jpg



intro:
  - excerpt: 'Bir rüya gibi : Amerika...'

feature_row2:
  - image_path: /assets/images/algoritma.jpg
    alt: "placeholder image 2"
    title: "Ders 1"
    excerpt: 'Ders içeriği...'
    url: "/home/"
    btn_label: "Read More"
    btn_class: "btn--primary"

feature_row3:
  - image_path: /assets/images/algoritma.jpg
    alt: "Ders 2"
    title: "Ders 2"
    excerpt: 'Ders içeriği...'
    url: "/layout/uncategorized/layout-comments/"
    btn_label: "Read More"
    btn_class: "btn--primary"

---

{% include feature_row id="intro" type="center" %}

{% include feature_row %}

{% include feature_row id="feature_row2" type="left" %}

{% include feature_row id="feature_row3" type="left" %}

{% include feature_row id="feature_row4" type="center" %}
