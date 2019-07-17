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
+ Seong-Yun Jeon (전성윤)
+ Ye-Byoul Son (손예별)

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


### Session 3: [BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-sy-july-18-2019.html)

### Information of the paper [(Link)](https://www.sciencedirect.com/science/article/pii/S1084804518301619)

- Authors: Chao Lin, Debiao He(Key Laboratory of Aerospace Information Security and Trusted Computing, Ministry of Education, School of Cyber Science and Engineering, Wuhan University), Xinyi Huang(School of Mathematics and Computer Science, Fujian Normal University), Kim-Kwang Raymond Choo(The University of Texas at San Antonio), Athanasios V. Vasilakos(Department of Computer Science, Electrical and Space Engineering, Lulea University of Technology)
- **Journal** name: Journal of Network and Computer Applications
- Published date: 2018-08-15
- [Paper Link](https://www.sciencedirect.com/science/article/pii/S1084804518301619)

### Abstract

To be prepared for the ‘Industry 4.0’-era, we propose a hierarchical framework comprising four tangible layers, which is designed to vertically integrate inter-organizational value networks, engineering value chain, manufacturing factories, etc. The conceptual framework allows us to efficiently implement a flexible and reconfigurable smart factory. However, we need to consider security inherent in existing (stand-alone) devices and networks as well as those that may arise in such integrations. Especially the existing solutions are insufficient to address these fundamental security concerns. Thus, we present a blockchain-based system for secure mutual authentication, BSeIn, to enforce fine-grained access control polices. The proposed system (with integrated attribute signature, multi-receivers encryption and message authentication code) is designed to provide privacy and security guarantees such as anonymous authentication, auditability, and confidentiality. BSeIn also scales well due to the utilization of smart contract. We then evaluate the security and performance of BSeIn. For example, findings from the performance evaluation demonstrate that Initialization/Request Issuance/Chain Transaction/State Delivery/Permission Update phase only cost 12.123/4.810/6.978/0.013/2.559s, respectively.


------
### Session 4: [Chameleon Hashing and Signatures]()

### Information of the paper [(Link)](https://pdfs.semanticscholar.org/1c29/4428c76ba7d1d0bb5e1d1bc931138c092453.pdf)

- Authors: Hugo Krawczyk, Tal Rabin (IBM Research)
- Publish date : 1997
- [Paper Link](https://pdfs.semanticscholar.org/1c29/4428c76ba7d1d0bb5e1d1bc931138c092453.pdf)

- Ref
  - **Conference** name: Network and Distributed System Security Symposium 2000
  - Published date: 2000-02-03
  - Information of the paper[(Link)](https://www.ndss-symposium.org/ndss2000/chameleon-signatures/)
  - [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2017/09/Chameleon-Signatures-paper-Hugo-Krawczyk.pdf)

### Abstract
We introduce chameleon signatures that provide with an undeniable commitment of the signer to the contents of the signed document (as regular digital signatures do) but, at the same time, do not allow the recipient of the signature to disclose the contents of the signed information to any third party without the signer's consent. These signatures are closely related to \undeniable signatures", but chameleon signatures allow for simpler and more efficient realizations than the latter. In particular, they are essentially non-interactive and do not involve the design and complexity of zero-knowledge proofs on which traditional undeniable signatures are based. Instead, chameleon signatures are generated under the standard method of hash-then-sign. Yet, the hash functions which are used are chameleon hash functions. These hash functions are characterized by the nonstandard property of being collision-resistant for the signer but collision tractable for the recipient. 

------


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
