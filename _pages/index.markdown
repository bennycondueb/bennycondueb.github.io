---
#TODO: improve the buttons  

title: "bennycondueb;"
layout: splash
permalink: /
author_profile: true
classes: 
    - landing

header: 
    overlay_color: "#000"
    overlay_filter: "0.625"
    overlay_image: assets/images/thedigitalartist-banner-1557881.jpg
excerpt: 'welcome to my personal website!' 

intro: 
  - excerpt: '# BSc in Comp Eng @ PoliTo, Robotics Software Developer, & More'

portfolio_whoami_contact_row:
  - image_path: assets/images/tkaucic-portfolio-2903909.svg
    alt: "portfolio open source image for the portfolio page link"
    title: "portfolio"
    excerpt: "Most of the stuff that you find on the CV will be more detailed here."
    url: _pages/portfolio/

  - image_path: assets/images/htchnm-question-mark-5730277_1920.png
    alt: "who am i open source image for the who am i page link"
    title: "who am i"
    excerpt: "Brief description (and definetely not complete) of my persona, in & out of different contexts."
    url: _pages/whoami/

  - image_path: assets/images/inspire-studio-send-icon-6851743_1920.png
    alt: "contact open source image for the contact page link"
    title: "contact"
    excerpt: "If you need to contact me, visit this page" 
    url: _pages/contact/

text_portfolio_row: 
    - excerpt: "# Portfolio Picks"

portfolio_row:
  - image_path: assets/images/io-images-eye-1103593_1920.png
    alt: "eye open source image for the visual odometry page link"
    title: "Visual Odometry"
    excerpt: "Visual Odometry implementation in Python using ROS2 Humble"
    url: _pages/portfolio/visual-odometry/

text_blog_row: 
    - excerpt: "# Blog posts Picks"

# blog_row:
#   - image_path: assets/images/vo_pipeline.png
#     alt: "placeholder image 1"
#     title: "Placeholder 1"
#     excerpt: "This is some sample content that goes here with **Markdown** formatting."


---


{% include feature_row id="intro" type="center" %}

<div class="uniform-icons">
  {% include feature_row.html id="portfolio_whoami_contact_row" %}
</div>

{% include feature_row id="text_portfolio_row" type="center"%}

<div class="uniform-icons">
  {% include feature_row.html id="portfolio_row" %}
</div>

{% include feature_row id="text_blog_row" type="center" %}
