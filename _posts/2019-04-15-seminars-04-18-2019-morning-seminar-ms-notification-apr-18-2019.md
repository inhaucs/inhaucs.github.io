---
title: 1st UCSLab Morning Seminar
date: 2019-04-15 00:00:00 Z
description: Notificaion of 1st UCSLab Morning Seminar (on 2019-04-18) 
card_title: 1st Morning Seminar
card_teaser: with 5 presentations on 2019-04-18.
card_position: 1
icon: fa-bullhorn
categories: [seminars,04-18-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-04-18

## Presenters
+ Jong-Hyuk Im (임종혁)
+ Hee-Yong Kwon (권희용)
+ Tae-Hyun Kim (김태현)
+ Sung-Yun Jeon (전성윤)
+ Ye-Byoul Son (손예별)
---
## Presentations

### Session 1: [The Rewards and Costs of Stronger Passwords in a University: Linking Password Lifetime to Strength](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-jh-apr-18-2019.html)

+ Jong-Hyuk Im (임종혁)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/becker)
+ Authors: Ingolf Becker, Simon Parkin, and M. Angela Sasse, University College London
+ Conference name: 27th USENIX Security Symposium (USENIX Security 18)
+ Published date: 2018-08-15
+ [Paper file](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-becker.pdf)

#### Abstract
We present an opportunistic study of the impact of a new password policy in a university with 100,000 staff and students. The goal of the IT staff who conceived the policy was to encourage stronger passwords by varying password lifetime according to password strength. Strength was measured through Shannon entropy (acknowledged to be a poor measure of password strength by the academic community, but still widely used in practice). When users change their password, a password meter informs them of the lifetime of their new password, which may vary from 100 days (50 bits of entropy) to 350 days (120 bits of entropy).
We analysed data of nearly 200,000 password changes and 115,000 resets of passwords that were forgotten/expired over a period of 14 months. The new policy took over 100 days to gain traction, but after that, average entropy rose steadily. After another 12 months, the average password lifetime increased from 146 days (63 bits) to 170 days (70 bits).
We also found that passwords with more than 300 days of lifetime are 4 times as likely to be reset as passwords of 100 days of lifetime. Users who reset their password more than once per year (27% of users) choose passwords with over 10 days fewer lifetime, and while they also respond to the policy, maintain this deficit.
We conclude that linking password lifetime to strength at the point of password creation is a viable strategy for encouraging users to choose stronger passwords (at least when measured by Shannon entropy).

---
### Session 2: [Privacy-Preserving Machine Learning: Threats and Solutions](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-hy-apr-18-2019.html)

+ Hee-Yong Kwon (권희용)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8677282/)
+ Authors: Mohammad Al-Rubaie, Iowa State University and J. Morris Chang, University of South Florida
+ Conference name: IEEE Security and Privacy Magazine
+ Published date: 2019-03-29 (Magazine version: 2019-04-11)
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8677282)

#### Abstract
For privacy concerns to be addressed adequately in today’s machine-learning (ML) systems, the knowledge gap between the ML and privacy communities must be bridged. This article aims to provide an introduction to the intersection of both fields with special emphasis on the techniques used to protect the data.
---
### Session 3: [Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-sy-apr-18-2019.html)

+ Seong-Yun Jeon (전성윤)

#### Information of the paper [(Link)](https://www.rsaconference.com/events/us19/speakers/cryptographers-track)
+ Authors: Manuel Barbosa(INESC TEC and FCUP, Portugal), Dario Catalano(Universit`a di Catania, Italy), Azam Soleimanian(Kharazmi University of Tehran, Iran and École Normale Supérieure, Paris, France), and Bogdan Warinschi(University of Bristol, Bristol, UK)
+ Conference name: The Cryptographers' Track at the RSA Conference 2019
+ Published date: 2019-03-04
+ [Paper Link](https://doi.org/10.1007/978-3-030-12612-4_7)

#### Abstract
We present an opportunistic study of the impact of a new password policy in a university with 100,000 staff and students. The goal of the IT staff who conceived the policy was to encourage stronger passwords by varying password lifetime according to password strength. Strength was measured through Shannon entropy (acknowledged to be a poor measure of password strength by the academic community, but still widely used in practice). When users change their password, a password meter informs them of the lifetime of their new password, which may vary from 100 days (50 bits of entropy) to 350 days (120 bits of entropy).
We analysed data of nearly 200,000 password changes and 115,000 resets of passwords that were forgotten/expired over a period of 14 months. The new policy took over 100 days to gain traction, but after that, average entropy rose steadily. After another 12 months, the average password lifetime increased from 146 days (63 bits) to 170 days (70 bits).
We also found that passwords with more than 300 days of lifetime are 4 times as likely to be reset as passwords of 100 days of lifetime. Users who reset their password more than once per year (27% of users) choose passwords with over 10 days fewer lifetime, and while they also respond to the policy, maintain this deficit.
We conclude that linking password lifetime to strength at the point of password creation is a viable strategy for encouraging users to choose stronger passwords (at least when measured by Shannon entropy).
---
### Session 4: [An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-yb-apr-18-2019.html)

+ Ye-Byoul Son (손예별)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8302552)
+ Authors: QUN LIN et al. Institute of Mathematics and Statistics, Hanshan Normal University, China
+ Journal name: IEEE ACCESS
+ Published date: 2018-02-27 (Present version : 2018-05-02)
+ [Paper Link](https://ieeexplore.ieee.org/document/8302552)

#### Abstract
Identity-based cryptosystems mean that public keys can be directly derived from user identifiers, such as telephone numbers, email addresses, and social insurance number, and so on. So they can simplify key management procedures of certificate-based public key infrastructures and can be used to realize authentication in blockchain. Linearly homomorphic signature schemes allow to perform linear computations on authenticated data. And the correctness of the computation can be publicly verified. Although a series of homomorphic signature schemes have been designed recently, there are few homomorphic signature schemes designed in identity-based cryptography. In this paper, we construct a new ID-based linear homomorphic signature scheme, which avoids the shortcomings of the use of public-key certificates. The scheme is proved secure against existential forgery on adaptively chosen message and ID attack under the random oracle model. The ID-based linearly homomorphic signature schemes can be applied in e-business and cloud computing. Finally, we show how to apply it to realize authentication in blockchain.
---

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}


