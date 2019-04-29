---
title: 4th UCSLab Morning Seminar
date: 2019-04-25 00:00:00 Z
description: Notificaion of 4th UCSLab Morning Seminar (on 2019-04-29) 
card_title: 4th Morning Seminar
card_teaser: with 4 presentations on 2019-04-29.
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

### Session 1: [How Do Tor Users InteractWith Onion Services?](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-th-apr-30-2019.html)

+ Tae-Hyun Kim (김태현)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/winter)
+ Authors: Philipp Winter; Anne Edmundson; Laura M. Roberts; Agnieszka Dutkowska-Zuk; Marshini Chetty; and Nick Feamster (Princeton University)
+ Conference name: 27th USENIX Security Symposium
+ Published date: 2018-08-15
+ [Paper Link](https://www.usenix.org/conference/usenixsecurity18/presentation/winter)

#### Abstract
Onion services are anonymous network services that are exposed over the Tor network. In contrast to conventional Internet services, onion services are private, generally not indexed by search engines, and use self-certifying domain names that are long and difficult for humans to read. In this paper, we study how people perceive, understand, and use onion services based on data from 17 semi-structured interviews and an online survey of 517 users. We find that users have an incomplete mental model of onion services, use these services for anonymity and have varying trust in onion services in general. Users also have difficulty discovering and tracking onion sites and authenticating them. Finally, users want technical improvements to onion services and better information on how to use them. Our findings suggest various improvements for the security and usability of Tor onion services, including ways to automatically detect phishing of onion services, more clear security indicators, and ways to manage onion domain names that are difficult to remember.
 
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

### Session 3: [NormFace: L<sub>2</sub> Hypersphere Embedding for Face Verification](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-sy-apr-29-2019.html)

+ Seong-Yun Jeon (전성윤)

#### Information of the paper [(Link)](https://dl.acm.org/citation.cfm?id=3123266.3123359)
+ Authors: Feng Wang, Xiang Xiang, Jian Cheng, and Alan Loddon Yuille (University of Electronic Science and Technology of China and Johns Hopkins University)
+ Conference name: 25th ACM international conference on Multimedia
+ Published date: 2017-08-23
+ [Paper Link](https://dl.acm.org/citation.cfm?id=3123266.3123359)
+ [Paper Link(arXiv)](https://arxiv.org/pdf/1704.06369.pdf)

#### Abstract
Thanks to the recent developments of Convolutional Neural Networks, the performance of face verification methods has increased rapidly. In a typical face verification method, feature normalization is a critical step for boosting performance. This motivates us to introduce and study the effect of normalization during training. But we find this is non-trivial, despite normalization being differentiable. We identify and study four issues related to normalization through mathematical analysis, which yields understanding and helps with parameter settings. Based on this analysis we propose two strategies for training using normalized features. The first is a modification of softmax loss, which optimizes cosine similarity instead of inner-product. The second is a reformulation of metric learning by introducing an agent vector for each class. We show that both strategies, and small variants, consistently improve performance by between 0.2% to 0.4% on the LFW dataset based on two models. This is significant because the performance of the two models on LFW dataset is close to saturation at over 98%.

---
 
{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
