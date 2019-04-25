---
title: "Session 1. Overview of the combination of biometric matchers"
date: 2019-04-25 00:00:00 Z
description: "Overview of the combination of biometric matchers"
card_title: Session 1
card_teaser: "Overview of the combination of biometric matchers"
card_position: 1
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [INFFUS, 2016, INFFUS2016, Biometric matchers, Fusion at score level, Unimodal biometrics, Multimodal biometrics]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-04-25

## [Overview of the combination of biometric matchers](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-sy-apr-25-2019.html)

#### Information of the paper [(Link)](https://www.sciencedirect.com/science/article/pii/S1566253516300446?via%3Dihub)
+ Authors: Alessandra Lumini; Loris Nanni; (in the University of Bologna in Italy and the University of Padua in Italy)
+ Journal name: Information Fusion
+ Published date: 2016-05-18
+ [Paper Link](https://www.sciencedirect.com/science/article/pii/S1566253516300446?via%3Dihub)
+ [Source Code](https://www.dropbox.com/s/5tf1q0o5do3a4tj/ToolBiometricFusion2015.rar?dl=0)

#### Abstract
Biometric identity verification refers to technologies used to measure human physical or behavioral characteristics, which offer a radical alternative to passports, ID cards, driving licenses or PIN numbers in authentication. Since biometric systems present several limitations in terms of accuracy, universality, distinctiveness, acceptability, methods for combining biometric matchers have attracted increasing attention of researchers with the aim of improving the ability of systems to handle poor quality and incomplete data, achieving scalability to manage huge databases of users, ensuring interoperability, and protecting user privacy against attacks. The combination of biometric systems, also known as “biometric fusion”, can be classified into unimodal biometric if it is based on a single biometric trait and multimodal biometric if it uses several biometric traits for person authentication.
The main goal of this study is to analyze different techniques of information fusion applied in the biometric field. This paper overviews several systems and architectures related to the combination of biometric systems, both unimodal and multimodal, classifying them according to a given taxonomy. Moreover, we deal with the problem of biometric system evaluation, discussing both performance indicators and existing benchmarks.
As a case study about the combination of biometric matchers, we present an experimental comparison of many different approaches of fusion of matchers at score level, carried out on three very different benchmark databases of scores. Our experiments show that the most valuable performance is obtained by mixed approaches, based on the fusion of scores. The source code of all the method implemented for this research is freely available for future comparisons1.
After a detailed analysis of pros and cons of several existing approaches for the combination of biometric matchers and after an experimental evaluation of some of them, we draw our conclusion and suggest some future directions of research, hoping that this work could be a useful start point for newer research.

## Summary (Korean)
이 논문은 information fusion을 biometric 분야에 적용한 biometric fusion의 여러가지 방법들을 분석하였다. 이 논문에서는 여러가지 biometric system들의 조합에 관련된 시스템들과 설계들에 대해 overview한다. 또한 biometric system의 성능 평가의 문제를 언급하면서 성능 측정과 기존의 벤치마크에 대해 discuss한다.
이 논문에서는 score level의 biometric matcher들의 조합에 대해 experimental comparison을 수행하는 사례연구를 하였고, mixed approach에서 매우 좋은 성능을 보였음을 확인하였다. 모든 소스코드(matlab으로 작성됨)는 공개되어있고, 마지막으로 향후 연구(biometric fusion)에 대한 방향 제시를 한다. 본 논문의 인용은 현재 58회이다.

## Details

### Biometric system들의 한계(limitations of biometric systems)
* variable environmental conditions(i.e. noise, changes in illumination, pose) -> 시스템의 정확도에 큰 영향을 준다.
* biometric data를 acquisition하는 조건에 따라 또는 aging effect에 따라 intra-class variation이 크다.
* 질병이나 장애로 인한 non-universality.
* spoof attacks이 가능할 수 있다.  

### Biometric fusion 이란
* Biometric system들의 한계를 극복하기 위해 biometric matchers를 조합하는 방법에 대한 연구에 관심이 높아졌다.
* Biometric fusion = the combination of biometric systems. biometric fusion은 크게 두가지로 나눈다.
  * unimodal biometric systems ; 한개의 biometric 정보를 다각도에서 취득하여 combination
  * multimodal biometric systems ; 여러개의 biometric 정보들에 대해서 combination
  * unimodal/multimodal에 대한 예시는 Fig. 1. Possible sources of information in a biometric fusion system. 을 참고
* unimodal fusion의 경우는 성형 수술을 한 얼굴의 인식이나 한가지 biometric에 대한 성능 향상에 효과적이다. 
* multimodal fusion의 경우는 non-universality를 어느 정도 극복하기 때문에, unimodal fusion에 비해 여러 장점이 있다. 물론 단점도 있다.
  * 장점
    * Failure-to-Enroll Rate (FTER)과 Failure-to-Capture Rate(FTCR)을 줄이고 충분한 population coverage를 확보할 수 있었다(=non-universality 완화. 조건부적으로..).
    * 공격자가 spoof attacks를 할때 여러 biometric sources들을 동시에 spoof 해야하기 때문에 공격이 더 어려워 질 것이다.
  * 단점
    * biometric template 보호가 더욱 강화되어야한다. 특히, biometric template 개수가 많아질수록, 종류가 다양해질 수록 개인에 대한 정보를 더 드러내는 셈이 된다.
    * 사용자가 인증에 몇가지 더 step이 생기기 때문에 불편함을 줄수 있다. 이 경우 fingerprints와 finger veins를 fusion하는 식으로 trait들 간의 취득 위치도 고려할 필요가 있다.
    
{% include articles/figure.html url="/assets/img/seongyun/2019/04-25-2019-ms-session1-fig1.PNG" legend="Possible sources of information in a biometric fusion system" %}

### Different levels of biometric fusion
* Sensor-level fusion ; 센서 수준에서 raw data를 combination. 예를 들면, swipe 식 지문 센서가 이미지들을 영상처리 기법을 이용하여 큰 이미지로 만들어 주는 것. 얼굴 인식 시에 3D로 인식하기 위해 여러개의 카메라로부터 받는 것.
* Feature-level fusion ; 추출한 feature vector들을 combination.
* Score-level fusion ; biometric matcher에 계산된 score를 combination. (i.e. LC, NLC)
* Decision-level fusion ; biometric matcher에 의해 산출된 인증 여부를 combination. (i.e. AND, OR)

{% include articles/figure.html url="/assets/img/seongyun/2019/04-25-2019-ms-session1-fig2.PNG" legend="Different levels of fusion in biometric systems" %}


## Points to note
* Biometric system를 combination하는 연구가 많이 진행되었음. score level 뿐만 아니라 다양한 level 상에서 combination하는 연구들이 많다.

## Discussion
Editor: 손예별 
+ "biometric : bio-information을 threshold를 가지고 metric를 만든다."
+ biometric combination
  + biometric을 여러개 써서 성능을 높인다.
    + 종류는 크게 unimodal(i.e. 얼굴 + 얼굴) / multimodal (i.e. 얼굴 + 홍채)
  + 여러개 써서 함께 이용하기 위해 기존에 있는 기능들을 재구현, 성능 측정.
+ "FTER : biometric 두가지를 등록할 경우, 등록 성공의 확률이 더 높다?" 자세한 확인 필요.
+ "Different levels of biometric fustion : 개념 정리가 잘 되어 있어, 차후 논문에 이용할 때 기본 개념으로 넣기 좋을 것 같음."


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
