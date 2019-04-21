---
title: "Session 5. Calculation and optimization of thresholds for sets of software metrics"
date: 2019-04-22 00:00:00 Z
description: (blank)
card_title: Session 5
card_teaser: "Calculation and optimization of thresholds for sets of software metrics"
card_position: 5
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [ESE, 2011, ESE2011, Software metrics, Thresholds, Machine learning, PAC]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
- Seong-Yun Jeon (전성윤)
- 2019-04-22
## Information of the paper
- Authors: Steffen Herbold, Jens Grabowski, Stephan Waack (Institute of Computer Science, University of Göttingen, Göttingen, Germany)
- Journal name: Empirical Software Engineering
- Published date: 2011-05-25
- [Paper file](https://link.springer.com/content/pdf/10.1007%2Fs10664-011-9162-z.pdf)
- [Slide file](https://www.swe.informatik.uni-goettingen.de/sites/default/files/publications/Slides-CalculationOptimizationOfMetricSets.pdf)

## Abstract
In this article, we present a novel algorithmic method for the calculation of thresholds for a metric set. To this aim, machine learning and data mining techniques are utilized. We define a data-driven methodology that can be used for efficiency optimization of existing metric sets, for the simplification of complex classification models, and for the calculation of thresholds for a metric set in an environment where no metric set yet exists. The methodology is independent of the metric set and therefore also independent of any language, paradigm or abstraction level. In four case studies performed on large-scale open-source software metric sets for C functions, C+ +, C# methods and Java classes are optimized and the methodology is validated.

## Summary (Korean)
- 이 논문에서는 여러 개의 software metric의 threshold들을 동시에 고려할 때에, 그 때 고려하는 계산과 최적화를 다룬다. software metric이란 소프트웨어의 질적 평가를 수행하는 metric 이다. 하나의 software metric 만으로 소프트웨어의 충분한 평가를 수행할 수 없기 때문에, 이 논문에서는 개별적인 software metric들을 활용하여 다방면(N-metrics)으로 동시에 고려하는 종합적인 평가 방법을 고안하고, 그 방법들의 계산과 최적화를 다룬다.

## Explanatory notes
- 이 논문에서 다루는 metric들은 biometric이 아니라 software metric이기 때문에 thresholding 최적화 기술을 위주로 review 하였다. 참고로, 여러 개의 biometric을 조합하는 것은 information confusion, combination of [biometric](https://doi.org/10.1016/j.inffus.2016.05.003) 등의 키워드로 찾는 것이 유리해보인다.

## Details
- 본 논문의 기여는 아래 4가지로 분류해서 설명할 수 있다. 이 논문은 software metric에 관한 논문임에도 불구하고, 이 논문의 기여들은, 여러 개의 metric들을 동시에 고려하는 상황들에 범용적으로 참고할 수 있는 듯하다.
1. metric sets의 threshold들을 계산하는 데에 machine learning 기반 방법을 사용 (논문의 Section 4.1)
  => [rectangle-learning](http://www.cs.utexas.edu/~klivans/f06lec2.pdf) (자세한 방법에 대해서는 설명이 없고, 논문의 Section 3.2에 개략적인 알고리즘 소개가 있다). 
> rectangle-learning의 메커니즘을 짧게 요약하자면, 편미분처럼 하나를 고정하고, N-depth loop의 rectagle-learning를 수행한다. learning 은 2개의 phase로 구성되는데, 첫번째 phase의 복잡도는 O(dnlogn)이고 두번째 phase의 복잡도는 O(dn*1/e)이다. 여기서 d는 N과 같고, n은 training set의 크기, e는 error bound이다. 이때, thresholding 의 경우에는 lower-bound 가 항상 0이라는 점이 있고, metric이 2개인 경우에는 loop가 2-depth 이다. 
2. 기존의 metric sets와 그것들의 threshold를 가지고 high-level 최적화 방법을 제안 (논문의 Section 4.2)
  => N-metrics에서 실제 사용되지 않은 metrics들은 제거하고, threshold를 조율하는 데에 일반적인 접근방법(generic methodology)을 제안.
> metrics sets로 만들수 있는 진부분집합 전체에 대해서 1의 방법을 수행...
3. 2의 방법의 복잡도 낮추는 방법 2가지 
  1. 손해를 감수하고 더 작은 subset 을 선택하는 방법. 2개 metric을 사용했다면 빼도 에러가 덜 생기는 1개의 metric을 제거.
  2. 복잡도가 낮은 분류 스킴(알고리즘)을 사용한다. 예를 들면, Support Vector Machine이나 classification tree를 사용하는 것보다 더 단순한 솔루션을 사용하는것.
4. 아직 threshold들이 결정되지 않은 metric sets들에 대해서, 좋은 threshold들을 결정하는 outline을 제안
  => 어떤 전문가를 예를 들며, 그 전문가의 판단을 하나의 metric 으로써 활용한다는 설명..(?)
- 기여 외의 참고 사항
  - 이 논문의 software assessment 의 데이터셋으로 large-scale open-source software projects 의 C 함수들, C++, C#, Java의 method와 클래스들을 사용함.

## Point to note
- 여러개의 metric을 조합하는 사례 연구. 조합 방법은 rectangle-learning.
- 실제 사용되지 않은 metrics 들은 제거하고, threshold 를 조율하는 방법을 제안. 
- 아직 threshold들이 결정되지 않은 metric sets들에 대해서, 좋은 threshold들을 결정하는 outline을 제안.

## Discussion
Editor: ??
+ write our discussion

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
