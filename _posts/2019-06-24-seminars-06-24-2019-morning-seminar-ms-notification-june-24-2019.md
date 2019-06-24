---
title: 7th UCSLab Morning Seminar
date: 2019-06-20 00:00:00 Z
description: Notificaion of 7th UCSLab Morning Seminar (on 2019-06-24)
card_title: 7th Morning Seminar
card_teaser: with 5 presentations on 2019-06-24.
card_position: 1
icon: fa-bullhorn
categories: [seminars,06-24-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-june-24-2019
permalink: /:categories/:slug.html

---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-06-24

## Presenters
+ Seong-Yun Jeon (전성윤)
+ Hee-Yong Kwon (권희용)
+ Tae-Hyun Kim (김태현)
+ Jong-Hyuk Im (임종혁)


---
## Presentations

---

### Session 1: [Password Authentication Using One-Time Key-Based Signature and Homomorphic Encryption](https://inhaucs.github.io/seminars/06-24-2019-morning-seminar/presentation/ms-presentation-sy-june-24-2019.html)

+ Seong-Yun Jeon (전성윤)

### Information of the paper [(Link)](https://link.springer.com/chapter/10.1007/978-3-319-49106-6_45)
+ Authors: Jong-Hyuk Im; Mun-Kyu Lee (Inha University)
+ **Conference** name: International Conference on Broadband and Wireless Computing, Communication and Applications
+ Published date: 2016-10-22
+ [Paper Link](https://link.springer.com/chapter/10.1007/978-3-319-49106-6_45)


### Abstract
User authentication is a process for a system to verify the identity of a claimed user and to give access permission. Although there are many other authentication methods such as biometrics and physical tokens, passwords are still being used in many applications due to easy deployment. To enhance the security against possible attacks such as an off-line dictionary attack, passwords are usually stored in a hashed form using a random nonce called a salt. However, this does not completely solve the security issue. In this paper, we propose a new password-based authentication method using homomorphic encryption where a password is stored in a remote server in an encrypted form and an input password is compared with the stored one on the encrypted domain. For this purpose, we also propose a new cryptographic primitive called one-time private key-based digital signature.

---

### Session 2: [How Do Tor Users InteractWith Onion Services?](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-winter.pdf)

+ Tae-Hyun Kim (김태현)

### Information of the paper [(Link)](https://www.usenix.org/node/217467)
+ Authors: Philipp Winter;Anne Edmundson;Laura M.Roberts;Agnieszka Durkowska-Zuk;Marshini Chetty;Nick Feamster(Princeton University)
+ Conference name: USENIX Security 2018
+ Published date: 2018-08-17
+ [Paper Link](https://www.usenix.org/node/217467)


### Abstract
Onion services are anonymous network services that are exposed over the Tor network. In contrast to conventional Internet services, onion services are private, generally not indexed by search engines, and use self-certifying domain names that are long and difficult for humans to read. In this paper, we study how people perceive, understand, and use onion services based on data from 17 semi-structured interviews and an online survey of 517 users. We find that users have an incomplete mental model of onion services, use these services for anonymity and have varying trust in onion services in general. Users also have difficulty discovering and tracking onion sites and authenticating them. Finally, users want technical improvements to onion services and better information on how to use them. Our findings suggest various improvements for the security and usability of Tor onion services, including ways to automatically detect phishing of onion services, more clear security indicators, and ways to manage onion domain names that are difficult to remember.


---

### Session 3: [Title](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

---

### Session 4: [Detection of Malicious Code Variants Based on Deep Learning](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

+ Hee-Yong Kwon (권희용)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8330042)
+ Authors: Zhihua Cui; Xingjuan Cai; Jinjun Chen (TaiYuan University of Science and Technology); Fei Xue (Beijing Wuzi University); Yang Cao (Beijing Unibersity of Technology); Gai-ge Wang (Ocean University)
+ **Journal** name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-04-03
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8330042)


### Abstract
With the development of the Internet, malicious code attacks have increased exponentially, with malicious code variants ranking as a key threat to Internet security. The ability to detect variants of malicious code is critical for protection against security breaches, data theft, and other dangers. Current methods for recognizing malicious code have demonstrated poor detection accuracy and low detection speeds. This paper proposed a novel method that used deep learning to improve the detection of malware variants. In prior research, deep learning demonstrated excellent performance in image recognition. To implement our proposed detection method, we converted the malicious code into grayscale images. Then, the images were identified and classified using a convolutional neural network (CNN) that could extract the features of the malware images automatically. In addition, we utilized a bat algorithm to address the data imbalance among different malware families. To test our approach, we conducted a series of experiments on malware image data from Vision Research Lab. The experimental results demonstrated that our model achieved good accuracy and speed as compared with other malware detection models.

---

### Session 5: [A4NT: Author Attribute Anonymity by Adversarial Training of Neural Machine Translation](https://inhaucs.github.io/seminars/06-24-2019-morning-seminar/presentation/ms-presentation-jh-june-24-2019.html)

+ Jong-Hyum Im (임종혁)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/shetty)
+ Authors: Rakshith Shetty; Bernt Schiele; and Mario Fritz; Max Planck (Institute for Informatics)
+ Conference name: USENIX Security 2018
+ Published date: 2018-08-17
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-shetty.pdf)


### Abstract
Text-based analysis methods enable an adversary to reveal privacy relevant author attributes such as gender, age and can identify the text's author. Such methods can compromise the privacy of an anonymous author even when the author tries to remove privacy sensitive content. In this paper, we propose an automatic method, called the Adversarial Author Attribute Anonymity Neural Translation ($\text{A}^{4}\text{NT}$), to combat such text-based adversaries. Unlike prior works on obfuscation, we propose a system that is fully automatic and learns to perform obfuscation entirely from the data. This allows us to easily apply the $\text{A}^{4}\text{NT}$ system to obfuscate different author attributes. We propose a sequence-to-sequence language model, inspired by machine translation, and an adversarial training framework to design a system which learns to transform the input text to obfuscate the author attributes without paired data. We also propose and evaluate techniques to impose constraints on our $\text{A}^{4}\text{NT}$ model to preserve the semantics of the input text. $\text{A}^{4}\text{NT}$ learns to make minimal changes to the input to successfully fool author attribute classifiers, while preserving the meaning of the input text. Our experiments on two datasets and three settings show that the proposed method is effective in fooling the attribute classifiers and thus improves the anonymity of authors.

---





{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
