---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

#TODO: wrap the css in the page into a proper css file 
#TODO insert a proper header image!! 
#TODO: find a way to put links into the images not only in the buttons, would look cool 
#TODO: improve the buttons  
#TODO: add the rows for the blog and for the portfolio

title: "bennycondueb;"
layout: splash
permalink: /
author_profile: true
classes: 
    - landing

header: 
    overlay_color: "#000"
    overlay_filter: "0.5"
    # overlay_image: /assets/images/vo_pipeline.png 

# excerpt: 'BSc in Comp Eng @ PoliTo, Robotics Software Developer, & More' 

intro: 
  - excerpt: 'BSc in Comp Eng @ PoliTo, Robotics Software Developer, & More'

portfolio_whoami_contact_row:
  - image_path: assets/images/tkaucic-portfolio-2903909.svg
    alt: "portfolio open source image for the portfolio page link"
    title: "portfolio"
    excerpt: "Most of the stuff that you find on the CV will be more detailed here."
    url: _pages/portfolio.md

  - image_path: assets/images/htchnm-question-mark-5730277_1920.png
    alt: "who am i open source image for the who am i page link"
    title: "who am i"
    excerpt: "Brief description (and definetely not complete) of my persona, in & out of different contexts."
    url: _pages/whoami.md

  - image_path: assets/images/inspire-studio-send-icon-6851743_1920.png
    alt: "contact open source image for the contact page link"
    title: "contact"
    excerpt: "If you need to contact me, visit this page" 
    url: _pages/contact.md

portfolio_row:
  - image_path: assets/images/vo_pipeline.png
    alt: "placeholder image 1"
    title: "Placeholder 1"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."

blog_row:
  - image_path: assets/images/vo_pipeline.png
    alt: "placeholder image 1"
    title: "Placeholder 1"
    excerpt: "This is some sample content that goes here with **Markdown** formatting."

#
#{% include feature_row id="portfolio_row" %}
#{% include feature_row id="blog_row" %}

---


{% include feature_row id="intro" type="center" %}

<div class="uniform-icons">
  {% include feature_row id="portfolio_whoami_contact_row" %}
</div>


<style>
  .uniform-icons .archive__item-teaser img {
    height: 180px; /* Modifica questo valore per ingrandire o rimpicciolire le immagini */
    width: 100%;
    object-fit: contain; 
  }
</style>