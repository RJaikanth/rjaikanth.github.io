---
# Meta
title: "Raghhuveer Jaikanth's Blog"
layout: splash

# Header
header:
  overlay_color: "#000"
  overlay_filter: "0.5"
  overlay_image: assets/images/about_bg.jpg
  caption: "[Source](https://www.stockvault.net/photo/264047/abstract-background-big-data-concept)"
excerpt: 
  "All Things AI and ML. Follow the links for more!"

# Intro
intro: 
  - excerpt: Hi welcome to my blog. I post summaries of research papers in the deep learing field as well as their implementations. Follow the links for more!


# Feature rows
cv_row:
  - image_path: /assets/images/cv.png
    alt: "Computer Vision Papers"
    title: "Computer Vision Research Papers"
    excerpt: "Follow this link to find summaries of deep learning research papers in the field of Computer Vision."
    url: "/cv-papers"
    btn_label: "Computer Vision Papers"
    btn_class: "btn--info btn--primary"
nlp_row:
  - image_path: /assets/images/nlp.png
    alt: "NLP Papers"
    title: "NLP Research Papers"
    excerpt: "Follow this link to find summaries of deep learning research papers in the field of NLP."
    url: "/nlp-papers"
    btn_label: "NLP Papers"
    btn_class: "btn--info btn--primary"
---

{% include feature_row id="intro" type="center" %}

{% include feature_row id="cv_row" type="left" %}

<!-- {% include feature_row id="nlp_row" type="right" %} -->