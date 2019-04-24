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
+ Seong-Yun Jeon (전성윤)
+ Jong-Hyuk Im (임종혁)
+ Ye-Byoul Son (손예별)
+ Hee-Yong Kwon (권희용)
+ Tae-Hyun Kim (김태현)

---
## Presentations

---
### Session 1: [Overview of the combination of biometric matchers](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-sy-apr-25-2019.html)

+ Seong-Yun Jeon (전성윤)

#### Information of the paper [(Link)](https://www.sciencedirect.com/science/article/pii/S1566253516300446?via%3Dihub)
+ Authors: Alessandra Lumini; Loris Nanni; (in the University of Bologna in Italy and the University of Padua in Italy)
+ Journal name: Information Fusion
+ Published date: 2016-05-18
+ [Paper Link](https://www.sciencedirect.com/science/article/pii/S1566253516300446?via%3Dihub)

#### Abstract
Biometric identity verification refers to technologies used to measure human physical or behavioral characteristics, which offer a radical alternative to passports, ID cards, driving licenses or PIN numbers in authentication. Since biometric systems present several limitations in terms of accuracy, universality, distinctiveness, acceptability, methods for combining biometric matchers have attracted increasing attention of researchers with the aim of improving the ability of systems to handle poor quality and incomplete data, achieving scalability to manage huge databases of users, ensuring interoperability, and protecting user privacy against attacks. The combination of biometric systems, also known as “biometric fusion”, can be classified into unimodal biometric if it is based on a single biometric trait and multimodal biometric if it uses several biometric traits for person authentication.
The main goal of this study is to analyze different techniques of information fusion applied in the biometric field. This paper overviews several systems and architectures related to the combination of biometric systems, both unimodal and multimodal, classifying them according to a given taxonomy. Moreover, we deal with the problem of biometric system evaluation, discussing both performance indicators and existing benchmarks.
As a case study about the combination of biometric matchers, we present an experimental comparison of many different approaches of fusion of matchers at score level, carried out on three very different benchmark databases of scores. Our experiments show that the most valuable performance is obtained by mixed approaches, based on the fusion of scores. The source code of all the method implemented for this research is freely available for future comparisons1.
After a detailed analysis of pros and cons of several existing approaches for the combination of biometric matchers and after an experimental evaluation of some of them, we draw our conclusion and suggest some future directions of research, hoping that this work could be a useful start point for newer research.

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
+ Authors : Maria Apostolak, Gian Marti, Jan Miller, Laurent Vanbever (ETH Zurich)
+ Journal : NDSS19 
+ Published date: 2019-02-24 
+ [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-1_Apostolaki_paper.pdf)

#### Abstract
Nowadays Internet routing attacks remain practically effective as existing countermeasures either fail to provide protection guarantees or are not easily deployable. Blockchain systems are particularly vulnerable to such attacks as they rely on Internet-wide communications to reach consensus. In particular, Bitcoin—the most widely-used cryptocurrency—can be split in half by any AS-level adversary using BGP hijacking. 
 In this paper, we present SABRE, a secure and scalable Bitcoin relay network which relays blocks worldwide through a set of connections that are resilient to routing attacks. SABRE runs alongside the existing peer-to-peer network and is easily deployable. As a critical system, SABRE design is highly resilient and can efficiently handle high bandwidth loads, including Denial
of Service attacks. 
 We built SABRE around two key technical insights. First, we leverage fundamental properties of inter-domain routing (BGP) policies to host relay nodes: (i) in networks that are inherently protected against routing attacks; and (ii) on paths that are economically-preferred by the majority of Bitcoin clients. These properties are generic and can be used to protect other Blockchain-based systems. Second, we leverage the fact that relaying blocks is communication-heavy, not computation-heavy. This enables us to offload most of the relay operations to programmable network hardware (using the P4 programming language). Thanks to this hardware/software co-design, SABRE nodes operate seamlessly under high load while mitigating the effects of malicious clients. 
 We present a complete implementation of SABRE together with an extensive evaluation. Our results demonstrate that SABRE is effective at securing Bitcoin against routing attacks, even with deployments of as few as 6 nodes.
 
 ---
 
 
 ---
 
 
 ### Session 4: [Surveylance: Automatically Detecting Online Survey Scams](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-th-apr-25-2019.html)

+ Tae-Hyun Kim (김태현)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8418597)
+ Authors: Amin Kharraz, William Robertson, Engin Kirda(Northeastern University, University of Illinois Urbana-Champaign)
+ Conference name: 2018 IEEE Symposium on Security and Privacy
+ Published date: 2018-05-20
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8418597)

#### Abstract
Online surveys are a popular mechanism for performing market research in exchange for monetary compensation. Unfortunately, fraudulent survey websites are similarly rising in popularity among cyber-criminals as a means for executing social engineering attacks. In addition to the sizable population of users that participate in online surveys as a secondary revenue stream, unsuspecting users who search the web for free content or access codes to commercial software can also be exposed to survey scams. This occurs through redirection to websites that ask the user to complete a survey in order to receive the promised content or a reward.
In this paper, we present SURVEYLANCE, the first system that automatically identifies survey scams using machine learning techniques. Our evaluation demonstrates that SURVEYLANCE works well in practice by identifying 8,623 unique websites involved in online survey attacks. We show that SURVEYLANCE is suitable for assisting human analysts in survey scam detection at scale. Our work also provides the first systematic analysis of the survey scam ecosystem by investigating the capabilities of these services, mapping all the parties involved in the ecosystem, and quantifying the consequences to users that are exposed to these services. Our analysis reveals that a large number of survey scams are easily reachable through the Alexa top 30K websites, and expose users to a wide range of security issues including identity fraud, deceptive advertisements, potentially unwanted programs (PUPs), malicious extensions, and malware.

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
