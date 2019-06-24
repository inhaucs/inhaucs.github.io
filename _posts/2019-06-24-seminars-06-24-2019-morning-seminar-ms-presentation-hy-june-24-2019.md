---
title: Session 4. Detection of Malicious Code Variants Based on Deep Learning
date: 2019-06-24 00:00:00 Z
description: Detection of Malicious Code Variants Based on Deep Learning
card_title: Session 4
card_teaser: Detection of Malicious Code Variants Based on Deep Learning
card_position: 4
icon: fa-server
categories: [seminars,06-24-2019-morning-seminar,presentation]
tags: [TII, 2018, TII2018, Malware variants, grayscale image, deep learning, convolution neural network, bat algorithm]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-june-24-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-06-24

## [Detection of Malicious Code Variants Based on Deep Learning](https://inhaucs.github.io/seminars/05-16-2019-morning-seminar/presentation/ms-presentation-hy-may-16-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8330042)
+ Authors: Zhihua Cui; Xingjuan Cai; Jinjun Chen (TaiYuan University of Science and Technology); Fei Xue (Beijing Wuzi University); Yang Cao (Beijing Unibersity of Technology); Gai-ge Wang (Ocean University)
+ **Journal** name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-04-03
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8330042)


### Abstract
With the development of the Internet, malicious code attacks have increased exponentially, with malicious code variants ranking as a key threat to Internet security. The ability to detect variants of malicious code is critical for protection against security breaches, data theft, and other dangers. Current methods for recognizing malicious code have demonstrated poor detection accuracy and low detection speeds. This paper proposed a novel method that used deep learning to improve the detection of malware variants. In prior research, deep learning demonstrated excellent performance in image recognition. To implement our proposed detection method, we converted the malicious code into grayscale images. Then, the images were identified and classified using a convolutional neural network (CNN) that could extract the features of the malware images automatically. In addition, we utilized a bat algorithm to address the data imbalance among different malware families. To test our approach, we conducted a series of experiments on malware image data from Vision Research Lab. The experimental results demonstrated that our model achieved good accuracy and speed as compared with other malware detection models.


## Summary (Korean)
+ Internet 발달과 함께 각종 malware들의 변종들이 등장
  + Symantec 401 million malicious codes 찾음 (2016), 이 중 357 millions는 variants
+ 현재의 탐지 방법들은 탐지율이 매우 낮고 심지어 느림
  + Static or Dynamic approaches
    + 보통 feature-based로 수행되는데, 둘 다 회피 가능
+ 이를 해결하기 위해 malicious code를 grayscale 이미지로 변환하는 방법이 이미 제안([NLJ+11])
  + 상기 회피 방법(e.g., 난독화)을 다룰 수 있지만 이미지로부터 feature extraction이 오래 걸리고(high cost), 큰 데이터셋에 대해 효율적이지 않음
+ Deep learning을 사용해서 malware의 변종들을 탐지하는 방법을 제안
  + Malware 코드를 **grayscale** 이미지로 변환
  + 변환된 image에 대해서 **Convolution Neural Network (CNN)** 적용
  + 다른 malware familie 사이의 불균형을 다루기 위해 **bat algorithm** 사용
+ Vision Research Lab.의 malware 이미지 데이터에 대해 실험했고(Santa Barbara, [[NLJ+11]]), 좋은 정확도와 속도를 보임
+ Contributions
  + Malware binary를 이미지로 변환하는 방법을 소개하고, 이를 통해 malware 탐지 문제를 이미지 분류 문제로 변환
  + CNN 기반의 malware variants detection 방법 소개
  + 다른 malware family 간의 데이터 불균형 문제를 해결하기 위해, bat algorithm에 기반한 data equilibrium approach 설계
  + 많은 실험을 통해, 제안하는 방법이 malware detection에 효과적임을 보임

[NLJ+11]: <https://dl.acm.org/citation.cfm?id=2016908> "Nataraj, Lakshmanan, et al. “Malware images: visualization and automatic classification.” Proceedings of the 8th international symposium on visualization for cyber security. ACM, 2011."


## Related work
+ 다음의 네 가지 분석 또는 탐지 방법에 대한 관련 연구 내용 포함
  + Malware Detection Based on Feature Analysis
  + Malicious Code Visualization
  + Image Processing Techniques for Malware Detection
  + Malware Detection Based on Deep Learning


## Malware Detection based on a CNN (proposed method)
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-24-fig-proposed-method.png" legend="Overview of the proposed method." %}
+ 제안하는 방법은 상기 그림과 같이 malicious 코드를 grayscale image로 변환; 그리고 CNN 적용을 통한 탐지의 두 단계로 구성됨
+ Binary Malware to Gray image
  + [[NKJ+11]]에서 제안하는 변환 방법 사용 (visualization of executable malware binary files)
    + 먼저 Binary를 8-bit 단위로 나누어 0-255로 표현 -> 10진수의 1-D vector로 변환
    + 1-D vector를 특정 width에 따라 2-D matrix로 변환
      + 특정 width는 [[NKJ+11]]에서 실험을 통해 파일 크기에 따라 고정됨
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-24-fig-malware_images.png" legend="Malware Images." %}
  + [[NKJ+11]]에서 보인 Malware Family 내의 유사성과 Family 간의 차이
+ Malware Image Classification Based on CNN
  + CNN은 multidimensional input에 이점
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-24-fig-malware_classification.png" legend="Malware Classification." %}
  + 뭔가 새로운 방법을 적용한 줄 알았으나, 일반적인 CNN 사용

[NKJ+11]: <https://dl.acm.org/citation.cfm?id=2016908> "L. Nataraj, S. Karthikeyan, G. Jacob, andB.Manjunath, “Malware images: visualization and automatic classification,” in Proc. 8th Int. Symp. Vis. Cyber Security, 2011, Paper 4."


## Malware Image Data Equilibrium
+ Malware 샘플이 family에 따라 개수의 차이가 있음(데이터 불균형) -> 학습이 제대로 되지 않음(low accuracy & poor robustness)
  + Image Data Augmentation (IDA) Technology
    + 데이터 불균형을 해결하기 위해, 부족한 데이터 확대 -> 과적합 방지
    + 새로운 데이터 생성 방법의 종류
      + rotation/reflection, flip, zoom, shift, scale, contrast, noise, color 등
    + 상기 생성 방법들 중 몇 가지를 임의 선택하여 새로운 데이터 생성
  + Data Equalization Based on a Bat algorithm (DRBAz )
    + Swarm intelligence(집단 지성)에 기반한 데이터 불균형 해결법 제시: Dynamic Resampling method based on the Bat Algorithm
      + Bat Algorithm은 기존에 연구된 내용([[Y10]])
      + 다른 malware family 간의 sampling weight을 최적화하기 위해 사용됨

[Y10]: <https://link.springer.com/chapter/10.1007/978-3-642-12538-6_6> "X.-S.Yang, “A new metaheuristic bat-inspired algorithm,” Nature Inspired Cooperative Strategies for Optimization (NICSO 2010), New York, NY, USA: Springer, pp. 65–74, 2010."


## Experimental Evaluation
+ Caffe framework 사용 (NN framework)
+ Intel Core i5-4590 CPU (3.3 GHz), Nvidia Geforce GTX 750Ti GPU (2 GB), and 8 GB RAM
+ Dataset: 25 Malware Families, 9,342 grayscale images
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-24-fig-experimental_results.png" legend="Performances of experimental Results" %}
  + Data Equalization을 통해 Validation 시에 더 나은 성과를 보임을 알 수 있음 (Overfitting 방지)
  + CNN을 수행하기 위해 Image size를 fix해야함에 따라 다양한 Image 크기(reshape)에 따라 실험을 수행함(24*24, 48*48, 96*96, and 192*192)
    + Image의 크기가 클 수록 Training 단계에서의 시간이 많이 소요되게 때문에 추천하는 이미지 크기는 96*96
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-24-tbl-comparison.png" legend="Comparison with other approaches" %}
  + Accuracy, Precision, and Recall 모두 높으며, Running time 도 매우 빠름


### Points to note
+ Grayscale image + CNN 을 통한 Malware detection 방법 제안
+ Deep Learning 에서 종종 문제가 되는 데이터 불균형 문제를 해결하기 위한 방법 제시
+ 이를 통해 기존의 Malware detection using image 방법들보다 성능이 좋고 빠른 방법 제시



## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
