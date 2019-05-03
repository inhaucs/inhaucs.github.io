---
title: Session 4. Significant Permission Identification for Machine-Learning-Based Android Malware Detection
date: 2019-05-06 00:00:00 Z
description: Significant Permission Identification for Machine-Learning-Based Android Malware Detection
card_title: Session 4
card_teaser: Significant Permission Identification for Machine-Learning-Based Android Malware Detection
card_position: 4
icon: fa-server
categories: [seminars,05-06-2019-morning-seminar,presentation]
tags: [TII, 2018, TII2018, Access control, computer security, machine learning, mobile applications, mobile computing]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-may-06-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-05-06

## [Significant Permission Identification for Machine-Learning-Based Android Malware Detection](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-hy-may-06-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8255798)
+ Authors: Jin Li (Guangzhou University); Lichao Sun (University of
Illinois at Chicago); Qiben Yan; Zhiqiang Li; Witawas Srisa-an (University of Nebraska–Lincoln); Heng Ye (Beijing Jiaotong University)
+ Conference name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-01-12
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8255798)


### Abstract
The alarming growth rate of malicious apps has become a serious issue that sets back the prosperous mobile ecosystem. A recent report indicates that a new malicious app for Android is introduced every 10 s. To combat this serious malware campaign, we need a scalable malware detection approach that can effectively and efficiently identify malware apps. Numerous malware detection tools have been developed, including system-level and network-level approaches. However, scaling the detection for a large bundle of apps remains a challenging task. In this paper, we introduce Significant Permission IDentification (SigPID), a malware detection system based on permission usage analysis to cope with the rapid increase in the number of Android malware. Instead of extracting and analyzing all Android permissions, we develop three levels of pruning by mining the permission data to identify the most significant permissions that can be effective in distinguishing between benign and malicious apps. SigPID then utilizes machine-learning-based classification methods to classify different families of malware and benign apps. Our evaluation finds that only 22 permissions are significant. We then compare the performance of our approach, using only 22 permissions, against a baseline approach that analyzes all permissions. The results indicate that when a support vector machine is used as the classifier, we can achieve over 90% of precision, recall, accuracy, and F-measure, which are about the same as those produced by the baseline approach while incurring the analysis times that are 4–32 times less than those of using all permissions. Compared against other state-of-the-art approaches, SigPID is more effective by detecting 93.62% of malware in the dataset and 91.4% unknown/new malware samples.


## Summary (Korean)
+ Android에서 새로운 Malware들이 10초에 하나 꼴로 추가되고 있음
+ 기존의 system-level, network-level 의 malware detection tool들이 있으나 여전히 문제
+ 이에, Significant Permission IDentification (SigPID) 제안
  + 권한 분석에 기반한 Malware detection system
  + Android의 모든 권한을 분석하는 것이 아닌 일반 앱과 Malware를 구분하는 가장 심대한 권한을 가지치기하는 세 가지 레벨을 개발
  + 기계 학습 기반 분류 방법 사용
  + 결과적으로 22 개의 권한이 중요 권한임을 찾음
  + 실험 : baseline approach(모든 권한에 대해 분석) vs. 상기 22개의 권한에 대한 분석
    + 결과적으로 SVM을 분류기로 사용했을 때, baseline approach 와 비교하여 비슷한 결과를 얻었으며, 90%가 넘는 precision, recall, accuracy, F-measure를 보였고, 4-32배 빠름
    + State-of-art approach와 비교해도 SigPID는 93.62%의 malware를 탐지함으로써 더 나은 성능을 보였고, 알려지지 않거나/새로운 Malware에 대해서도 91.4% 탐지


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
