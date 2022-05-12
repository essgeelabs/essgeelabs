---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
categories:
  - News
tags: 
  - news
author: {{ .Site.Params.Author }}
summary: 
cover:
    image: "/images/egllogo.jpg" # image path/url
    alt: "Ess Gee Labs Logo" # alt text
    # caption: "<text>" # display caption under cover
    relative: true # when using page bundles set this to true
    hidden: false # only hide on current single page
editPost:
    URL: "https://github.com/essgeelabs/essgeelabs/tree/master/content"
    Text: "Suggest Changes" # edit text
    appendFilePath: true # to append file path to Edit link
---

