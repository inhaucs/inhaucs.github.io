---
title: 2nd UCSLab Morning Seminar
date: 2019-04-18 00:00:00 Z
description: Notificaion of 2nd UCSLab Morning Seminar (on 2019-04-22) 
card_title: 2nd Morning Seminar
card_teaser: with 5 presentations on 2019-04-22.
card_position: 1
icon: fa-bullhorn
categories: [seminars,04-22-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-04-22

## Presenters
+ Ye-Byoul Son (손예별) : Cont.
+ Tae-Hyun Kim (김태현) : Cont.
+ Jong-Hyuk Im (임종혁)
+ Hee-Yong Kwon (권희용)
+ Sung-Yun Jeon (전성윤)


## Presentations

### Session 3: [Rethinking Access Control and Authentication for the Home Internet of Things (IoT)](https://inhaucs.github.io/seminars/04-22-2019-morning-seminar/presentation/ms-presentation-jh-apr-22-2019.html)

+ Jong-Hyuk Im (임종혁)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/he)
+ Authors: Weijia He (University of Chicago); Maximilian Golla (Ruhr-University Bochum); Roshni Padhi and Jordan Ofek (University of Chicago); Markus Dürmuth (Ruhr-University Bochum); Earlence Fernandes (University of Washington); Blase Ur (University of Chicago)
+ Conference name: 27th USENIX Security Symposium (USENIX Security 18)
+ Published date: 2018-08-15
+ [Paper file](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-he.pdf)

#### Abstract
Computing is transitioning from single-user devices to the Internet of Things (IoT), in which multiple users with complex social relationships interact with a single device. 
Currently deployed techniques fail to provide usable access-control specification or authentication in such settings. 
In this paper, we begin reenvisioning access control and authentication for the home IoT. 
We propose that access control focus on IoT capabilities (i.e., certain actions that devices can perform), rather than on a per-device granularity. 
In a 425-participant online user study, we find stark differences in participants' desired access-control policies for different capabilities within a single device, as well as based on who is trying to use that capability. 
From these desired policies, we identify likely candidates for default policies. We also pinpoint necessary primitives for specifying more complex, yet desired, access-control policies. 
These primitives range from the time of day to the current location of users. 
Finally, we discuss the degree to which different authentication methods potentially support desired policies.


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
