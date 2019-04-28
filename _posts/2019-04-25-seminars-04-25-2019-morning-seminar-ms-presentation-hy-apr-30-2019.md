---
title: Session 5. Face Spoof Detection With Image Distortion Analysis
date: 2019-04-28 00:00:00 Z
description: Face Spoof Detection With Image Distortion Analysis
card_title: Session 5
card_teaser: Face Spoof Detection With Image Distortion Analysis
card_position: 5
icon: fa-server
categories: [seminars,04-29-2019-morning-seminar,presentation]
tags: [TIFS, 2015, TIFS2015, face recognition, spoof detection, image distortion analysis, ensemble classifier, cross-database, cross-device]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-30-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-30

## [Face Spoof Detection With Image Distortion Analysis](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-hy-apr-30-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/7031384)
+ Authors: Di Wen; Hu Han; and Anil K. Jain (Michigan State University)
+ Conference name: IEEE Transactions on Information Forensics and Security
+ Published date: 2015-02-04
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7031384)


### Abstract
Automatic face recognition is now widely used in applications ranging from deduplication of identity to authentication of mobile payment. This popularity of face recognition has raised concerns about face spoof attacks (also known as biometric sensor presentation attacks), where a photo or video of an authorized person’s face could be used to gain access to facilities or services. While a number of face spoof detection techniques have been proposed, their generalization ability has not been adequately addressed. We propose an efficient and rather robust face spoof detection algorithm based on image distortion analysis (IDA). Four different features (specular reflection, blurriness, chromatic moment, and color diversity) are extracted to form the IDA feature vector. An ensemble classifier, consisting of multiple SVM classifiers trained for different face spoof attacks (e.g., printed photo and replayed video), is used to distinguish between genuine (live) and spoof faces. The proposed approach is extended to multiframe face spoof detection in videos using a voting-based scheme. We also collect a face spoof database, MSU mobile face spoofing database (MSU MFSD), using two mobile devices (Google Nexus 5 and MacBook Air) with three types of spoof attacks (printed photo, replayed video with iPhone 5S, and replayed video with iPad Air). Experimental results on two public-domain face spoof databases (Idiap REPLAY-ATTACK and CASIA FASD), and the MSU MFSD database show that the proposed approach outperforms the state-of-the-art methods in spoof detection. Our results also highlight the difficulty in separating genuine and spoof faces, especially in cross-database and cross-device scenarios.


## Summary (Korean)
+ Image Distortion Analysis (IDA) 기반의 Face Spoof Attack Detection 방법 제안
+ IDA에는 4개의 특징들이 사용됨
  + Specular reflection
  + Blurriness
  + Chromatic moment
  + Color diversity
+ 분류를 위해 ensemble classifier 사용
+ 타겟 기기
  + Google Nexus 5 and MacBook Air
+ Face spoofing types
  + Printed photo, replayed video with iPhone 5S, replayed video with iPad Air
+ Face spoofing database
  + MSU mobile face spoofing database (MSU MFSED) : 본인들이 수집한 DB
  + Idiap REPLAY-ATTACK
  + CASIA FASD


## Details
+ Motivation
  + 얼굴 인식은 지문과 다르게 따로 센서가 필요하지 않기 때문에 생체 인식의 이점이 있어 많이 사용된다(Abstract 참고 가능)
  + 하지만 얼굴 데이터는 다른 생체 데이터와는 다르게 수집하기 용이함(SNS or Video 등)
  + 논문 출판 당시 최신의 기술인 Commercial Off-The-Shelf (COTS)는 Fig. 2에서 보이듯 Face Spoofing에 취약함
  + 그래서 본 논문은 3D mask(비용 문제)를 제외한 printed photo와 replayed video attacks에 대해서 Face spoofing에 안전한 방법 제안
  + 기존 연구들([[CAM12]][[AM11]][[TLL+10]][[ZYL+12]][[SPW+07]][[BLL+09]][[BDV+13]])은 사용한 DB들의 한계가 있음
+ Contribution
  + IDA 기반의 face spoof detection algorithm 제안
  + 새로운 face spoof detection database 구성 : MSU Mobile Face Spoof Database (MSU MFSD) -> 허락 받고 
  + 세 개의 DB에 대해 제안하는 방법 실험
    + MSU MFSD, Idiap REPLAY-ATTACK, CASIA FASD


### Contents of the paper


### Points to note



## Discussion

[CAM12]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6313548> "I. Chingovska, A. Anjos, and S. Marcel, “On the effectiveness of local binary patterns in face anti-spoofing,” in Proc. IEEE BIOSIG, Sep. 2012, pp. 1–7."
[AM11]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6117503> "A. Anjos and S. Marcel, “Counter-measures to photo attacks in face recognition: A public database and a baseline,” in Proc. IJCB, Oct. 2011, pp. 1–7."
[TLL+10]: <http://parnec.nuaa.edu.cn/xtan/paper/eccv10r1.pdf> "X. Tan, Y. Li, J. Liu, and L. Jiang, “Face liveness detection from a single image with sparse low rank bilinear discriminative model,” in Proc. ECCV, Sep. 2010, pp. 504–517."
[ZYL+12]: <http://www.cbsr.ia.ac.cn/users/jjyan/ZHANG-ICB2012.pdf> "Z. Zhang, J. Yan, S. Liu, Z. Lei, D. Yi, and S. Z. Li, “A face antispoofing database with diverse attacks,” in Proc. ICB, Mar./Apr. 2012, pp. 26–31."
[SPW+07]: <https://arxiv.org/pdf/1801.01949.pdf> "L. Sun, G. Pan, Z. Wu, and S. Lao, “Blinking-based live face detection using conditional random fields,” in Proc. AIB, 2007, pp. 252–260."
[BLL+09]: <https://arxiv.org/pdf/1804.06702.pdf> "W. Bao, H. Li, N. Li, and W. Jiang, “A liveness detection method for face recognition based on optical flow field,” in Proc. IASP, Apr. 2009, pp. 233–236."
[BDV+13]: <http://iab-rubric.org/papers/PID2777141.pdf> "S. Bharadwaj, T. I. Dhamecha, M. Vatsa, and R. Singh, “Computationally efficient face spoofing detection with motion magnification,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. Workshops (CVPRW), Jun. 2013, pp. 105–110."



{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
