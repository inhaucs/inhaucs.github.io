---
title: "Session 2. Privacy-Preserving Machine Learning: Threats and Solutions"
date: 2019-04-16 00:00:00 Z
description: (blank)
card_title: Session 2
card_teaser: "Privacy-Preserving Machine Learning: Threats and Solutions"
card_position: 2
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-18

## Information of the paper
+ Authors: Mohammad Al-Rubaie, Iowa State University and J. Morris Chang, University of South Florida
+ Conference name: IEEE Security and Privacy Magazine
+ Published date: 2019-03-29 (Magazine version: 2019-04-11)
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8677282)

## Abstract
For privacy concerns to be addressed adequately in today’s machine-learning (ML) systems, the knowledge gap between the ML and privacy communities must be bridged. This article aims to provide an introduction to the intersection of both fields with special emphasis on the techniques used to protect the data.

## Summary (Korean)
본 논문에서는 기계 학습을 수행하는 동안 데이터 제공자에게 발생할 수 있는 프라이버시 위협과 현재 연구된 해결 방법들 그리고 논문 말미에 앞으로 연구해야하는 방향에 대해 설명하며, 위협과 해결 방법 두 가지에 대한 개요를 소개함.

## Details
+ Machine Learning(ML) Section Skip. (Supervised, Unsupervised, Semisupervised, etc.)
  + ML은 세 가지 요소로 구성됨
    + **Input party** : 데이터 제공자
    + **Computation party** : ML 연산 수행자
    + **Results party** : ML 모델을 사용자
  + 상기 세 요소가 같은 주체에서 구성되는 경우 프라이버시는 고려할 필요가 없으나, 일반적으로 **Computation party**와 **Results party**는 한 주체에 있고 **Input party**만 분리되어 구성됨.
  
+ **Threats**
  + **Private Data in the Clear** : 데이터 제공자가 데이터를 암호화되지 않은 상태로 전달하여 사용하는 경우
  + **Reconstruction Attacks** : ML에 feature vector만 사용하더라도 모델에 feature vector가 남아있는 경우가 있음(e.g., SVM, k-NN). 이 경우 공격자는 feature vector로부터 Raw data 복원이 가능함. [FENG2011]에서는 minutiae template으로부터 지문을 재구성하는 공격을 성공하였고, [Al2016]에서는 개인의 인증 방식의 특징(gesture, speed, etc.)을 비슷하게 하여 공격한 연구를 진행.
  + **Model Inversion Attacks** : 물론 feature vector가 모델에 포함되지 않는 것도 있음(e.g., ridge regression, NN). 이 때 공격자는 모델에 대한 테스트 결과를 사용하여 모델에 사용된 feature vector와 비슷한 결과를 얻는 것이 목표. 모델에 대한 테스트를 반복 수행하면 특정 클래스에 대한 평균을 얻을 수 있는데, 해당 클래스가 개인에 대한 정보를 포함하고 있는 경우 큰 문제가 됨. 예를 들어 [FREDRIKSON2015]에서는 얼굴 인식에서 이를 보였음.
  + **Membership Inference Attacks** : 타겟 모델에 Input을 넣고(Label을 알고 있는 Input) 출력된 결과와 Label을 비교하여 해당 Input이 Training Phase에서 사용된 샘플인지 아닌지 확인하여 공격하는 방법.
  + **De-Anonymization(Re-Identification)** : 데이터 제공시, 개인 식별 정보를 모두 제거하고 전달하면 자연스럽게 보안 문제가 해결될 것이라 생각하고 실제로 많이 사용함. 그러나 알려진 유저들의 정보를 사용하여 누구인지 추론이 가능하므로 궁극적인 해결책이 될 수 없음.
  
  
+ **Privacy-Preserving Machine Learning (PPML)**
  + 주로 암호학적 접근(Cryptographic approaches)과 차등 보호(differentially private data release: DP, Perturbation approaches)가 사용됨
  + 특히 DP는 membership inference attacks을 막는데 효과적
  + **Model inversion attacks**과 **Membership inference attacks**을 방지하기 위해서는 모델의 결과를 제한하는 것이 효과적임
  
  + **암호학적 접근(Cryptographic Approaches)**
    + 암호화된 상태에서 학습 및 테스트를 수행하는 방법
    + *동형 암호(Homomorphic Encryption)*
  

[FENG2011]
[Al2016]
[FREDRIKSON2015]


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
