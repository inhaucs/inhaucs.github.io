---
title: 5th UCSLab Morning Seminar
date: 2019-05-06 00:00:00 Z
description: Notificaion of 4th UCSLab Morning Seminar (on 2019-05-06)
card_title: 5th Morning Seminar
card_teaser: with 5 presentations on 2019-05-06.
card_position: 1
icon: fa-bullhorn
categories: [seminars,05-06-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-may-06-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-05-06

## Presenters
+ Tae-Hyun Kim (김태현)
+ Jong-Hyuk Im (임종혁)
+ Seong-Yun Jeon (전성윤)
+ Hee-Yong Kwon (권희용)
+ Ye-Byoul Son (손예별)

---
## Presentations

---

### Session 1: [Title](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

---

### Session 2: [Simple Password-Hardened Encryption Services](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-jh-may-06-2019.html)

+ Jong-Hyum Im (임종혁)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/lai)
+ Authors: Russell W. F. Lai and Christoph Egger (Friedrich-Alexander University Erlangen-Nuremberg); Manuel Reinert (Saarland University); Sherman S. M. Chow (Chinese University of Hong Kong); Matteo Maffei (Vienna University of Technology); Dominique Schröder( Friedrich-Alexander University Erlangen-Nuremberg)
+ Conference name: USENIX Security 2018
+ Published date: 2018-08-17
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-lai.pdf)


### Abstract
Passwords and access control remain the popular choice for protecting sensitive data stored online, despite their well-known vulnerability to brute-force attacks. 
A natural solution is to use encryption. Although standard practices of using encryption somewhat alleviate the problem, decryption is often needed for utility, and keeping the decryption key within reach is obviously dangerous. 
To address this seemingly unavoidable problem in data security, we propose password-hardened encryption (PHE). 
With the help of an external crypto server, a service provider can recover the user data encrypted by PHE only when an end user supplied a correct password. 
PHE inherits the security features of password-hardening (Usenix Security ’15), adding protection for the user data. 
In particular, the crypto server does not learn any information about any user data. 
More importantly, both the crypto server and the service provider can rotate their secret keys, a proactive security mechanism mandated by the Payment Card Industry Data Security Standard (PCI DSS). 
We build an extremely simple password-hardened encryption scheme. Compared with the state-of-the-art password-hardening scheme (Usenix Security ’17), our scheme only uses minimal number-theoretic operations and is, therefore, 30% - 50% more efficient. 
In fact, our extensive experimental evaluation demonstrates that our scheme can handle more than 525 encryption and (successful) decryption requests per second per core, which shows that it is lightweight and readily deployable in large-scale systems. 
Regarding security, our scheme also achieves a stronger soundness property, which puts less trust on the good behavior of the crypto server.

---

### Session 3: [Title](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

---

### Session 4: [Significant Permission Identification for Machine-Learning-Based Android Malware Detection](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-hy-may-06-2019.html)

+ Hee-Yong Kwon (권희용)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8255798)
+ Authors: Jin Li (Guangzhou University); Lichao Sun (University of
Illinois at Chicago); Qiben Yan; Zhiqiang Li; Witawas Srisa-an (University of Nebraska–Lincoln); Heng Ye (Beijing Jiaotong University)
+ **Journal** name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-01-12
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8255798)


### Abstract
The alarming growth rate of malicious apps has become a serious issue that sets back the prosperous mobile ecosystem. A recent report indicates that a new malicious app for Android is introduced every 10 s. To combat this serious malware campaign, we need a scalable malware detection approach that can effectively and efficiently identify malware apps. Numerous malware detection tools have been developed, including system-level and network-level approaches. However, scaling the detection for a large bundle of apps remains a challenging task. In this paper, we introduce Significant Permission IDentification (SigPID), a malware detection system based on permission usage analysis to cope with the rapid increase in the number of Android malware. Instead of extracting and analyzing all Android permissions, we develop three levels of pruning by mining the permission data to identify the most significant permissions that can be effective in distinguishing between benign and malicious apps. SigPID then utilizes machine-learning-based classification methods to classify different families of malware and benign apps. Our evaluation finds that only 22 permissions are significant. We then compare the performance of our approach, using only 22 permissions, against a baseline approach that analyzes all permissions. The results indicate that when a support vector machine is used as the classifier, we can achieve over 90% of precision, recall, accuracy, and F-measure, which are about the same as those produced by the baseline approach while incurring the analysis times that are 4–32 times less than those of using all permissions. Compared against other state-of-the-art approaches, SigPID is more effective by detecting 93.62% of malware in the dataset and 91.4% unknown/new malware samples.

---

### Session 5: [SABRE: Protecting Bitcoin against Routing Attacks](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-yb-may-06-2019.html)

+ Ye-Byoul Son (손예별)

#### Information of the paper [(Link)](https://www.ndss-symposium.org/ndss-paper/sabre-protecting-bitcoin-against-routing-attacks/)
+ Authors: Maria Apostolak, Gian Marti, Jan Miller, Laurent Vanbever (ETH Zurich)
+ Journal name: NDSS Symposium 2019 Programme
+ Published date: 2019-02-24
+ [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-1_Apostolaki_paper.pdf)
+ [Slide Link](https://www.ndss-symposium.org/wp-content/uploads/ndss2019_02A-1_Apostolaki_slides.pdf)

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
