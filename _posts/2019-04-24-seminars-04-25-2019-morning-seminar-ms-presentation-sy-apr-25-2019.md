---
title: "Session 1. Overview of the combination of biometric matchers"
date: 2019-04-23 00:00:00 Z
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

#### Abstract
Biometric identity verification refers to technologies used to measure human physical or behavioral characteristics, which offer a radical alternative to passports, ID cards, driving licenses or PIN numbers in authentication. Since biometric systems present several limitations in terms of accuracy, universality, distinctiveness, acceptability, methods for combining biometric matchers have attracted increasing attention of researchers with the aim of improving the ability of systems to handle poor quality and incomplete data, achieving scalability to manage huge databases of users, ensuring interoperability, and protecting user privacy against attacks. The combination of biometric systems, also known as “biometric fusion”, can be classified into unimodal biometric if it is based on a single biometric trait and multimodal biometric if it uses several biometric traits for person authentication.
The main goal of this study is to analyze different techniques of information fusion applied in the biometric field. This paper overviews several systems and architectures related to the combination of biometric systems, both unimodal and multimodal, classifying them according to a given taxonomy. Moreover, we deal with the problem of biometric system evaluation, discussing both performance indicators and existing benchmarks.
As a case study about the combination of biometric matchers, we present an experimental comparison of many different approaches of fusion of matchers at score level, carried out on three very different benchmark databases of scores. Our experiments show that the most valuable performance is obtained by mixed approaches, based on the fusion of scores. The source code of all the method implemented for this research is freely available for future comparisons1.
After a detailed analysis of pros and cons of several existing approaches for the combination of biometric matchers and after an experimental evaluation of some of them, we draw our conclusion and suggest some future directions of research, hoping that this work could be a useful start point for newer research.

## Summary (Korean)
이 논문은 information fusion을 biometric 분야에 적용한 biometric fusion의 여러가지 방법들을 분석하였다. 이 논문에서는 여러가지 biometric system들의 조합에 관련된 시스템들과 설계들에 대해 overview한다. 또한 biometric system의 성능 평가의 문제를 언급하면서 성능 측정과 기존의 벤치마크에 대해 discuss한다.
이 논문에서는 score level의 biometric matcher들의 조합에 대해 experimental comparison을 수행하는 사례연구를 하였고, mixed approach에서 매우 좋은 성능을 보였음을 확인하였다. 모든 소스코드는 공개되어있고, 마지막으로 향후 연구에 대한 방향 제시를 한다.

## Details

### Biometric system들의 한계(limitations of biometric systems)
* variable environmental conditions(i.e. noise, changes in illumination, pose) -> 시스템의 정확도에 큰 영향을 준다.
* biometric data를 acquisition하는 조건에 따라 또는 aging effect에 따라 intra-class variation이 크다.
* 질병이나 장애로 인한 non-universality.
* spoof attacks 이 가능할 수 있다.  

### Biometric fusion 이란
* Biometric system들의 한계를 극복하기 위해 biometric matchers 를 조합하는 방법에 대한 연구에 관심이 높아졌다.

## Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
