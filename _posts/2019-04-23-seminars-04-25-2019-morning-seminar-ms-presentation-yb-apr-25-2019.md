---
title: Session 3. SABRE: Protecting Bitcoin against Routing Attacks
date: 2019-04-23 00:00:00 Z
description: SABRE: Protecting Bitcoin against Routing Attacks
card_title: Session 3
card_teaser: SABRE: Protecting Bitcoin against Routing Attacks
card_position: 3
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [NDSS, 2019, NDSS2019, Blockchain, Bitcoin]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-04-25

## [SABRE: Protecting Bitcoin against Routing Attacks](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-yb-apr-25-2019.html)

### Information of the paper [(Link)](https://www.ndss-symposium.org/ndss-paper/sabre-protecting-bitcoin-against-routing-attacks/)
+ Authors: Maria Apostolak, Gian Marti, Jan Miller, Laurent Vanbever (ETH Zurich)
+ Journal name: IEEE Transactions on Information Forensics and Security
+ Published date: 2019-02-24
+ [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-1_Apostolaki_paper.pdf)


### Abstract
Nowadays Internet routing attacks remain practically effective as existing countermeasures either fail to provide protection guarantees or are not easily deployable. Blockchain systems are particularly vulnerable to such attacks as they rely on Internet-wide communications to reach consensus. In particular, Bitcoin—the most widely-used cryptocurrency—can be split in half by any AS-level adversary using BGP hijacking.
 In this paper, we present SABRE, a secure and scalable Bitcoin relay network which relays blocks worldwide through a set of connections that are resilient to routing attacks. SABRE runs alongside the existing peer-to-peer network and is easily deployable. As a critical system, SABRE design is highly resilient and can efficiently handle high bandwidth loads, including Denial
of Service attacks. 
 We built SABRE around two key technical insights. First, we leverage fundamental properties of inter-domain routing (BGP) policies to host relay nodes: (i) in networks that are inherently protected against routing attacks; and (ii) on paths that are economically-preferred by the majority of Bitcoin clients. These properties are generic and can be used to protect other Blockchain-based systems. Second, we leverage the fact that relaying blocks is communication-heavy, not computation-heavy. This enables us to offload most of the relay operations to programmable network hardware (using the P4 programming language). Thanks to this hardware/software co-design, SABRE nodes operate seamlessly under high load while mitigating the effects of malicious clients. 
 We present a complete implementation of SABRE together with an extensive evaluation. Our results demonstrate that SABRE is effective at securing Bitcoin against routing attacks, even with deployments of as few as 6 nodes.
## Summary (Korean)


## Details


### Contents of the paper


#### Conclusion


### Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
