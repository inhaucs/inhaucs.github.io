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

---

### Session 1: [An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain](https://inhaucs.github.io/seminars/04-22-2019-morning-seminar/presentation/ms-presentation-yb-apr-22-2019.html)

+ Ye-Byoul Son (손예별)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8302552)
+ Authors: QUN LIN et al. Institute of Mathematics and Statistics, Hanshan Normal University, China
+ Journal name: IEEE ACCESS
+ Published date: 2018-02-27 (Present version : 2018-05-02)
+ [Paper Link](https://ieeexplore.ieee.org/document/8302552)

#### Abstract
Identity-based cryptosystems mean that public keys can be directly derived from user identifiers, such as telephone numbers, email addresses, and social insurance number, and so on. So they can simplify key management procedures of certificate-based public key infrastructures and can be used to realize authentication in blockchain. Linearly homomorphic signature schemes allow to perform linear computations on authenticated data. And the correctness of the computation can be publicly verified. Although a series of homomorphic signature schemes have been designed recently, there are few homomorphic signature schemes designed in identity-based cryptography. In this paper, we construct a new ID-based linear homomorphic signature scheme, which avoids the shortcomings of the use of public-key certificates. The scheme is proved secure against existential forgery on adaptively chosen message and ID attack under the random oracle model. The ID-based linearly homomorphic signature schemes can be applied in e-business and cloud computing. Finally, we show how to apply it to realize authentication in blockchain.

---

### Session 2:


---

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

---

### Session 4: [Signal Processing and Machine Learning with Differential Privacy](https://inhaucs.github.io/seminars/04-22-2019-morning-seminar/presentation/ms-presentation-hy-apr-22-2019.html)

+ Hee-Yong Kwon (권희용)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6582713)
+ Authors: Anand D. Sarwate (Toyota Technological Institute); Kamalika Chaudhuri (University of California)
+ Conference name: IEEE Signal Processing Magazine
+ Published date: 2013-08-19
+ [Paper file](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6582713)

#### Abstract
Private companies, government entities, and institutions such as hospitals routinely gather vast amounts of digitized personal information about the individuals who are their customers, clients, or patients. Much of this information is private or sensitive, and a key technological challenge for the future is how to design systems and processing techniques for drawing inferences from this large-scale data while maintaining the privacy and security of the data and individual identities. Individuals are often willing to share data, especially for purposes such as public health, but they expect that their identity or the fact of their participation will not be disclosed. In recent years, there have been a number of privacy models and privacy-preserving data analysis algorithms to answer these challenges. In this article, we will describe the progress made on differentially private machine learning and signal processing.

---

### Session 5:

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
