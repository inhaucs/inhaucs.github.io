---
title: 14th UCSLab Morning Seminar
date: 2019-08-01 00:00:00 Z
description: Notificaion of 14th UCSLab Morning Seminar (on 2019-08-01)
card_title: 14th Morning Seminar
card_teaser: with 5 presentations on 2019-08-01.
card_position: 1
icon: fa-bullhorn
categories: [seminars,08-01-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-aug-01-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-07-31 ~ 2019-08-01

## Presenters
+ Jong-Hyuk Im (임종혁)
+ Hee-Yong Kwon (권희용)

## Presentations

---

### Session 1: [Turning Your Weakness Into a Strength: Watermarking Deep Neural Networks by Backdooring](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-jh-july-18-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/adi)

- Authors: Yossi Adi and Carsten Baum (Bar Ilan University); Moustapha Cisse (Google Inc); Benny Pinkas and Joseph Keshet (Bar Ilan University)
- **Conference** name: 27th Usenix Security Symposium
- Published date: 2018-08-17
- [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-adi.pdf)


### Abstract
Deep Neural Networks have recently gained lots of success after enabling several breakthroughs in notoriously challenging problems. Training these networks is computationally expensive and requires vast amounts of training data. Selling such pre-trained models can, therefore, be a lucrative business model. Unfortunately, once the models are sold they can be easily copied and redistributed. To avoid this, a tracking mechanism to identify models as the intellectual property of a particular vendor is necessary. In this work, we present an approach for watermarking Deep Neural Networks in a black-box way. Our scheme works for general classification tasks and can easily be combined with current learning algorithms. We show experimentally that such a watermark has no noticeable impact on the primary task that the model is designed for and evaluate the robustness of our proposal against a multitude of practical attacks. Moreover, we provide a theoretical analysis, relating our approach to previous work on backdooring.

---


### Session 2: [BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0](https://inhaucs.github.io/seminars/07-22-2019-morning-seminar/presentation/ms-presentation-sy-july-22-2019.html)

### Information of the paper [(Link)](https://www.sciencedirect.com/science/article/pii/S1084804518301619)

- Authors: Chao Lin, Debiao He(Key Laboratory of Aerospace Information Security and Trusted Computing, Ministry of Education, School of Cyber Science and Engineering, Wuhan University), Xinyi Huang(School of Mathematics and Computer Science, Fujian Normal University), Kim-Kwang Raymond Choo(The University of Texas at San Antonio), Athanasios V. Vasilakos(Department of Computer Science, Electrical and Space Engineering, Lulea University of Technology)
- **Journal** name: Journal of Network and Computer Applications
- Published date: 2018-08-15
- [Paper Link](https://www.sciencedirect.com/science/article/pii/S1084804518301619)

### Abstract

To be prepared for the ‘Industry 4.0’-era, we propose a hierarchical framework comprising four tangible layers, which is designed to vertically integrate inter-organizational value networks, engineering value chain, manufacturing factories, etc. The conceptual framework allows us to efficiently implement a flexible and reconfigurable smart factory. However, we need to consider security inherent in existing (stand-alone) devices and networks as well as those that may arise in such integrations. Especially the existing solutions are insufficient to address these fundamental security concerns. Thus, we present a blockchain-based system for secure mutual authentication, BSeIn, to enforce fine-grained access control polices. The proposed system (with integrated attribute signature, multi-receivers encryption and message authentication code) is designed to provide privacy and security guarantees such as anonymous authentication, auditability, and confidentiality. BSeIn also scales well due to the utilization of smart contract. We then evaluate the security and performance of BSeIn. For example, findings from the performance evaluation demonstrate that Initialization/Request Issuance/Chain Transaction/State Delivery/Permission Update phase only cost 12.123/4.810/6.978/0.013/2.559s, respectively.

---


{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}