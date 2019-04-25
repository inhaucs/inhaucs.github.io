---
title: 4th UCSLab Morning Seminar
date: 2019-04-25 00:00:00 Z
description: Notificaion of 4th UCSLab Morning Seminar (on 2019-04-29) 
card_title: 4th Morning Seminar
card_teaser: with 4 presentations on 2019-04-25.
card_position: 1
icon: fa-bullhorn
categories: [seminars,04-29-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-apr-29-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-04-29

## Presenters
+ Tae-Hyun Kim (김태현)
+ Jong-Hyuk Im (임종혁)
+ Seong-Yun Jeon (전성윤)
+ Hee-Yong Kwon (권희용)

---
## Presentations

---

### Session 2: [Analysis of Privacy Protections in Fitness Tracking Social Networks -or- You can run, but can you hide?](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

+ Jong-Hyuk Im (임종혁)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/hassan)
+ Authors: Wajih Ul Hassan, Saad Hussain, and Adam Bates (University Of Illinois Urbana-Champaign)
+ Conference name: 27th USENIX Security Symposium
+ Published date: 2018-08-16
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-hassan_0.pdf)

#### Abstract
Mobile fitness tracking apps allow users to track their workouts and share them with friends through online social networks. 
Although the sharing of personal data is an inherent risk in all social networks, the dangers presented by sharing personal workouts comprised of geospatial and health data may prove especially grave. 
While fitness apps offer a variety of privacy features, at present it is unclear if these countermeasures are sufficient to thwart a determined attacker, nor is it clear how many of these services’ users are at risk.

In this work, we perform a systematic analysis of privacy behaviors and threats in fitness tracking social networks. 
Collecting a month-long snapshot of public posts of a popular fitness tracking service (21 million posts, 3 million users), 
we observe that 16.5% of users make use of Endpoint Privacy Zones (EPZs), 
which conceal fitness activity near user-designated sensitive locations (e.g., home, office). 
We go on to develop an attack against EPZs that infers users’ protected locations from the remaining available information in public posts, 
discovering that 95.1% of moderately active users are at risk of having their protected locations extracted by an attacker. 
Finally, we consider the efficacy of state-of-the-art privacy mechanisms through adapting geo-indistinguishability techniques as well as developing a novel EPZ fuzzing technique. 
The affected companies have been notified of the discovered vulnerabilities and at the time of publication have incorporated our proposed countermeasures into their production systems.
 
---
 
{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}