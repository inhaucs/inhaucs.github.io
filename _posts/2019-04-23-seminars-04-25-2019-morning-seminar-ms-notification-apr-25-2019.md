---
title: 3rd UCSLab Morning Seminar
date: 2019-04-23 00:00:00 Z
description: Notificaion of 2nd UCSLab Morning Seminar (on 2019-04-25) 
card_title: 3rd Morning Seminar
card_teaser: with 5 presentations on 2019-04-25.
card_position: 1
icon: fa-bullhorn
categories: [seminars,04-25-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-apr-25-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-04-25

## Presenters
+ Seng-Yun Jeon (전성윤)
+ Jong-Hyuk Im (임종혁)
+ Ye-Byoul Son (손예별)
+ Hee-Yong Kwon (권희용)
+ Tae-Hyun Kim (김태현)

---
## Presentations

---
### Session 2: [Privacy-Preserving Deep Learning via Additively Homomorphic Encryption](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-jh-apr-25-2019.html)

+ Jong-Hyuk Im (임종혁)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8302552)
+ Authors: Le Trieu Phong; Yoshinori Aono; Takuya Hayashi; Lihua Wang; Shiho Moriai (in National Institute of Information and Communications Technology in Tokyo)
+ Journal name: IEEE Transactions on Information Forensics and Security
+ Published date: 2017-12-29
+ [Paper Link](https://ieeexplore.ieee.org/document/8241854)

#### Abstract
We present a privacy-preserving deep learning system in which many learning participants perform neural network-based deep learning over a combined dataset of all, without revealing the participants' local data to a central server. 
To that end, we revisit the previous work by Shokri and Shmatikov (ACM CCS 2015) and show that, with their method, local data information may be leaked to an honest-but-curious server. 
We then fix that problem by building an enhanced system with the following properties: 1) no information is leaked to the server and 2) accuracy is kept intact, compared with that of the ordinary deep learning system also over the combined dataset. 
Our system bridges deep learning and cryptography: we utilize asynchronous stochastic gradient descent as applied to neural networks, in combination with additively homomorphic encryption. 
We show that our usage of encryption adds tolerable overhead to the ordinary deep learning system.

---


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
