---
title: UCSLab Paper Review Test posting
date: 2019-04-12 00:00:00 Z
description: test about how to post into this site. 
card_title: Paper Review(title)
card_teaser: Paper Review 에 대한 내용(teaser)
card_position: 1
icon: fa-server
categories: [seminars,morning-seminar,04-18-2019]
sidebar: morning-seminar
layout: default
slug: ucslab-paper-review-test
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

# English Test

below, image!

{% include articles/figure.html
    url="/assets/img/help/2019/03/digital-ocean/001_create_droplet.png"
    legend="Create droplet"
%}

List :
- 1 GB
- 1 CPU


## Login in the machine and get the mysql credentials
external url link using
[online tools](https://www.whatsmydns.net/).
code block:
```
ssh root@this_droplet_ip
```


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
