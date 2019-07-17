---
title: 11th UCSLab Morning Seminar
date: 2019-07-18 00:00:00 Z
description: Notificaion of 11th UCSLab Morning Seminar (on 2019-07-18)
card_title: 11th Morning Seminar
card_teaser: with 4 presentations on 2019-07-18.
card_position: 1
icon: fa-bullhorn
categories: [seminars,07-18-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-july-18-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-07-18

## Presenters
+ Hee-Yong Kwon (권희용)
+ Jong-Hyuk Im (임종혁)

---
## Presentations

---

### Session 1: [Body Weight Analysis From Human Body Images](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-hy-july-18-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8666768)
+ Authors: Min Jiang; Guodong Guo (West Virginia University)
+ **Journal** name: IEEE Transactions on Information Forensics and Security (Volume 14, Issue 10)
+ Published date: 2019-03-13
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8666768)


### Abstract
Human body images encode plenty of useful biometric information, such as pupil color, gender, and weight. Among these, body weight is a good indicator of health conditions. Motivated by recent health science studies, this paper investigates the feasibility of analyzing body weight from two-dimensional (2D) frontal view human body images. The widely used body mass index (BMI) is employed as a measure of body weight. To investigate the problems at different levels of difficulties, three feasibility problems, from easy to hard, are studied. More specifically, a framework is developed for analyzing body weight from human body images. Computation of five anthropometric features is proposed for body weight characterization. Correlation is analyzed between the extracted anthropometric features and the BMI values, which validates the usability of the selected features. A visual-body-to-BMI dataset is collected and cleaned to facilitate the study, which contains 5900 images of 2950 subjects along with the labels corresponding gender, height, and weight. Some interesting results are obtained, demonstrating the feasibility of analyzing body weight from 2D body images. In addition, the proposed method outperforms two state-of-art facial image-based weight analysis approaches in most cases.

---

### Session 2: [Turning Your Weakness Into a Strength: Watermarking Deep Neural Networks by Backdooring](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-jh-july-18-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/adi)

- Authors: Yossi Adi and Carsten Baum (Bar Ilan University); Moustapha Cisse (Google Inc); Benny Pinkas and Joseph Keshet (Bar Ilan University)
- **Conference** name: 27th Usenix Security Symposium
- Published date: 2018-08-17
- [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-adi.pdf)

### Abstract

Deep Neural Networks have recently gained lots of success after enabling several breakthroughs in notoriously challenging problems. Training these networks is computationally expensive and requires vast amounts of training data. Selling such pre-trained models can, therefore, be a lucrative business model. Unfortunately, once the models are sold they can be easily copied and redistributed. To avoid this, a tracking mechanism to identify models as the intellectual property of a particular vendor is necessary. In this work, we present an approach for watermarking Deep Neural Networks in a black-box way. Our scheme works for general classification tasks and can easily be combined with current learning algorithms. We show experimentally that such a watermark has no noticeable impact on the primary task that the model is designed for and evaluate the robustness of our proposal against a multitude of practical attacks. Moreover, we provide a theoretical analysis, relating our approach to previous work on backdooring.

------






{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
