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
  + Specular reflection, Blurriness, Chromatic moment, Color diversity
+ 분류를 위해 ensemble classifier 사용
+ 타겟 기기
  + Google Nexus 5 and MacBook Air
+ Face spoofing types
  + Printed photo, replayed video with iPhone 5S, replayed video with iPad Air
+ Face spoofing database
  + MSU mobile face spoofing database (MSU MFSED) : 본인들이 수집한 DB, Idiap REPLAY-ATTACK, CASIA FASD


## Details
+ Motivation
  + 얼굴 인식은 지문과 다르게 따로 센서가 필요하지 않기 때문에 생체 인식의 이점이 있어 많이 사용된다(Abstract 참고 가능)
  + 하지만 얼굴 데이터는 다른 생체 데이터와는 다르게 수집하기 용이함(SNS or Video 등)
  + 논문 출판 당시 최신의 기술인 Commercial Off-The-Shelf (COTS)는 Fig. 2에서 보이듯 Face Spoofing에 취약함
  + 그래서 본 논문은 3D mask(비용 문제)를 제외한 printed photo와 replayed video attacks에 대해서 Face spoofing에 안전한 방법 제안
  + 기존 연구들([[CAM12]], [[AM11]], [[TLL+10]], [[ZYL+12]], [[SPW+07]], [[BLL+09]], [[BDV+13]])은 사용한 DB들의 한계가 있음
+ Contribution
  + IDA 기반의 face spoof detection algorithm 제안
  + 새로운 face spoof detection database 구성 : MSU Mobile Face Spoof Database (MSU MFSD) -> 허락 받고 
  + 세 개의 DB에 대해 제안하는 방법 실험
    + MSU MFSD, Idiap REPLAY-ATTACK, CASIA FASD


+ System Diagram
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-system-diagram.png" legend="System diagram" %}
  + input image를 144 x 120 pixels로 normalize -> PittPatt 5.2.2 SDK 사용
    + Face spoof detection을 위해서는 이 crop 과정이 매우 중요, 얼굴의 다른 부분이나 배경 영향을 받지 않게 하기 위해
  + 이후, 4개의 IDA 특징 추출, 121-d feature vector 생성
  + Ensemble classifier로 투입
  + 분류기는 binary decision 결과 출력

+ Four different features to detect face spoof
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-specular-reflection.png" legend="Specular reflection" %}
  + Specular Reflection Features : 반사광 추출 Fig. 4에서 보면 실제 이미지에서와 replayed video에서 추출되는 반사광의 위치와 분포가 다름을 알 수 있음
  + Blurriness Features : Spoofing에 사용되는 이미지는 크기가 제한되는 경우가 많기 때문에 카메라에 가까이 붙여 인식시키려고 시도한다. 그러므로 카메라의 초점이 맞지 않아 Blur가 생기는데, 이를 특징으로 사용
  {% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-chromatic-difference.png" legend="Chromatic Difference" %}
  + Chromatic Moment Features : Spoofing에 사용되는 이미지는 실제 이미지의 색을 완벽하게 재구성하지 못 함 -> In my opinion, it is nutshell (Analog -> Digital -> Print), 이에 따라 두 이미지의 Hue(색조), Saturation(포화도), Value(값)의 분포를 사용
    + Fig. 5에서 보면 Saturation과 Value에서의 분포가 다름을 알 수 있음
  + Color Diversity Features : 실제 이미지와 Spoofing 이미지에서의 색의 다양성에 대한 특징 (Chromatic Moment Features와 같은 이유로, 색의 다양성이 다름)
  
+ Classification Method
  + SVM with RBF kernel
  + Ensemble Classifier를 구성할 때, 여러 알고리즘으로 Ensemble 하는 것이 아닌 SVM에 각각 다른 training sample group으로 학습된 Classifier 사용
    + Attack type에 따라 spoof sample을 K group으로 나눔
    + 그리고 모든 실제 이미지 + a group of spoof spoof sample을 training set으로 설정 -> K 개의 training set, classifier가 되는 이유
  + Test 시 feature input은 모든 classifier로 들어가서 fusion -> fusion scheme으로는 sum and min rule 사용
    + min rule이 더 나은 성능을 보임
+ Database summary
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-db-summary.png" legend="Summary of databases" %}

## Experimental Results
+ 실험에 사용된 비교 Features
  + LBP features [[MHP11]], DoG-LBP features [[KD12]], IDA features
+ 사용된 데이터 수
  + Idiap : Training(22,497 Genuine / 69,686 Spoof), Test(29,791 Genuine / 93,686 Spoof)
  + CASIA (H) : Training(4,579 Genuine / 11,858 Spoof), Test(5,603 Genuine / 16,958 Spoof)
  + MSU : Training(11,567 Genuine / 33,050 Spoof), Test(11,178 Genuine / 33,102 Spoof)
+ Results
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-intra_db_performance.png" legend="Intra-Database Performance" %}
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-cross_db_performance.png" legend="Cross-Database Performance" %}
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-04-30-fig-both_db_performance.png" legend="Intra and Cross Databases Performance" %}


### Points to note
+ Face spoof attack detection을 위해 네 가지 특징을 사용함
+ Ensemble을 사용했지만 다양한 input에 대해 ensemble하였고, 이에 다른 Learning model을 Ensemble 했을 때는 어떤 결과가 나올지
+ Face spoof detection의 새로운 DB 공개



## Discussion

[CAM12]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6313548> "I. Chingovska, A. Anjos, and S. Marcel, “On the effectiveness of local binary patterns in face anti-spoofing,” in Proc. IEEE BIOSIG, Sep. 2012, pp. 1–7."
[AM11]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6117503> "A. Anjos and S. Marcel, “Counter-measures to photo attacks in face recognition: A public database and a baseline,” in Proc. IJCB, Oct. 2011, pp. 1–7."
[TLL+10]: <http://parnec.nuaa.edu.cn/xtan/paper/eccv10r1.pdf> "X. Tan, Y. Li, J. Liu, and L. Jiang, “Face liveness detection from a single image with sparse low rank bilinear discriminative model,” in Proc. ECCV, Sep. 2010, pp. 504–517."
[ZYL+12]: <http://www.cbsr.ia.ac.cn/users/jjyan/ZHANG-ICB2012.pdf> "Z. Zhang, J. Yan, S. Liu, Z. Lei, D. Yi, and S. Z. Li, “A face antispoofing database with diverse attacks,” in Proc. ICB, Mar./Apr. 2012, pp. 26–31."
[SPW+07]: <https://arxiv.org/pdf/1801.01949.pdf> "L. Sun, G. Pan, Z. Wu, and S. Lao, “Blinking-based live face detection using conditional random fields,” in Proc. AIB, 2007, pp. 252–260."
[BLL+09]: <https://arxiv.org/pdf/1804.06702.pdf> "W. Bao, H. Li, N. Li, and W. Jiang, “A liveness detection method for face recognition based on optical flow field,” in Proc. IASP, Apr. 2009, pp. 233–236."
[BDV+13]: <http://iab-rubric.org/papers/PID2777141.pdf> "S. Bharadwaj, T. I. Dhamecha, M. Vatsa, and R. Singh, “Computationally efficient face spoofing detection with motion magnification,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit. Workshops (CVPRW), Jun. 2013, pp. 105–110."
[MHP11]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6117510> "J. Määtta, A. Hadid, and M. Pietikäinen, “Face spoofing detection from single images using micro-texture analysis,” in Proc. IJCB, Oct. 2011, pp. 1–7."
[KD12]: <http://www.eurecom.fr/en/publication/3646/download/mm-publi-3646.pdf> "N. Kose and J. Dugelay, “Classification of captured and recaptured images to detect photograph spoofing,” in Proc. ICIEV, May 2012, pp. 1027–1032."


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
