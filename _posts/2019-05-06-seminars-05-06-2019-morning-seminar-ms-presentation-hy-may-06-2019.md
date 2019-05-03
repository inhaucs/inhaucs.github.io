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
  + Contribution
    + Malware를 탐지하기 위한 권한의 서브셋을 찾는 SigPID 개발 -> 필요한 권한을 84% 줄임(16% 사용)
    + 제안하는 방법 평가 -> 90% in precision, recall, accuracy, and F-measure
    + 포괄성 증명 -> 주로 사용되는 67개의 지도 학습 알고리즘에 적용 (5494 malware & 310926 benign)
      + 55개의 알고리즘에서 F-measure 85% 이상, 평균 수행 시간이 baseline approach에 비해 85.6% 감소


## Motivation
+ Android 시장은 매우 큰데, iOS와는 다르게 third-party나 file-sharing을 통한 어플리케이션 설치를 허용하고 있음 -> Malware가 다운로드될 수 있는 경로
+ Mobile malware의 97%가 Android를 타겟으로 함
+ 이러한 Malware의 타입은 50개 이상 있고, 이 때문에 모두 탐지하기가 힘듦
+ 이전 기술들이 있고 한계가 있음
  + RISKRANKER : 정적 분석 기반 -> False positive 많음
  + TAINTDROID : 동적 분석 기반 -> Malware 탐지 회피 기술
  + DREBIN : 정적 분석 + 기계 학습 -> High Cost


## Introducing SigPID
+ Goal : Malware 분석을 위해 필요한 최소한의 권한 찾기
+ a) Multi-Level Data Pruning(MLDP)을 사용하여 Malware 탐지에 영향이 별로 없는 권한 제거, 이는 세 컴포넌트를 포함
  + Permission Ranking with Negative Rate (PPNR)
  + Support-based Permission Ranking (SPR)
  + Permission Mining with Association Rules (PMAR)
+ b) MLDP로 필터링된 권한들을 지도 학습 분류 방법에 입력으로 사용하여 Malware 탐지

  ##### Multi-Level Data Pruning(MLDP)
  + Permission Ranking with Negative Rate (PPNR)
  + Support-based Permission Ranking (SPR)
  + Permission Mining with Association Rules (PMAR)

  ##### Machine-Learning-Based Malware Detection Using Significant Permissions
  + Permission Ranking with Negative Rate (PPNR)
  + Support-based Permission Ranking (SPR)
  + Permission Mining with Association Rules (PMAR)


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
