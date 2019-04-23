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

### Session 3: [SABRE: Protecting Bitcoin against Routing Attacks](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-yb-apr-25-2019.html)

+ Ye-Byoul Son (손예별)

#### Information of the paper [Link](https://www.ndss-symposium.org/ndss-paper/sabre-protecting-bitcoin-against-routing-attacks/)
Authors : Maria Apostolak, Gian Marti, Jan Miller, Laurent Vanbever (ETH Zurich)
Journal : NDSS19 
Published date: 2019-02-24
[Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-1_Apostolaki_paper.pdf)

#### Abstract
Nowadays Internet routing attacks remain practically effective as existing countermeasures either fail to provide protection guarantees or are not easily deployable. Blockchain systems are particularly vulnerable to such attacks as they rely on Internet-wide communications to reach consensus. In particular, Bitcoin—the most widely-used cryptocurrency—can be split in half by any AS-level adversary using BGP hijacking. 
 In this paper, we present SABRE, a secure and scalable Bitcoin relay network which relays blocks worldwide through a set of connections that are resilient to routing attacks. SABRE runs alongside the existing peer-to-peer network and is easily deployable. As a critical system, SABRE design is highly resilient and can efficiently handle high bandwidth loads, including Denial
of Service attacks. 
 We built SABRE around two key technical insights. First, we leverage fundamental properties of inter-domain routing (BGP) policies to host relay nodes: (i) in networks that are inherently protected against routing attacks; and (ii) on paths that are economically-preferred by the majority of Bitcoin clients. These properties are generic and can be used to protect other Blockchain-based systems. Second, we leverage the fact that relaying blocks is communication-heavy, not computation-heavy. This enables us to offload most of the relay operations to programmable network hardware (using the P4 programming language). Thanks to this hardware/software co-design, SABRE nodes operate seamlessly under high load while mitigating the effects of malicious clients. 
 We present a complete implementation of SABRE together with an extensive evaluation. Our results demonstrate that SABRE is effective at securing Bitcoin against routing attacks, even with deployments of as few as 6 nodes.
 
 ---

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
