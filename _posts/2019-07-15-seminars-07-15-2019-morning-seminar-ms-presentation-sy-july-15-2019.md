---
title: Session 3. On Computing Products of Pairings
date: 2019-07-15 00:00:00 Z
description: On Computing Products of Pairings
card_title: Session 1
card_teaser: On Computing Products of Pairings
card_position: 1
icon: fa-server
categories: [seminars,07-15-2019-morning-seminar,presentation]
tags: [ePrint, 2006, Pairing, Optimization, Inner Product]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-july-15-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-07-15

## [On Computing Products of Pairings](https://inhaucs.github.io/seminars/07-15-2019-morning-seminar/presentation/ms-presentation-sy-july-15-2019.html)

### Information of the paper [(Link)](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.61.7456)
+ Authors: R. Granger, Nigel P. Smart (École Polytechnique Fédérale de Lausanne)
+ Journal name: ePrint
+ Published date: 2016-01
+ [Paper Link](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.61.7456)

### Abstract
In many pairing-based protocols often the evaluation of the product of many pairing evaluations is required. In this paper we consider methods to compute such products efficiently. Focusing on pairing-friendly fields in particular, we evaluate methods for the Weil, Tate and Ate pairing algorithms for ordinary elliptic curves at various security levels. Our operation counts indicate that the minimal cost of each ad-ditional pairing relative to the cost of one is ≈ 0.61, 0.45, and 0.43, for each of these pairings respectively at the 128-bit security level. For larger security levels the Ate pairing can have a relative additional cost of as low as 0.13 for each additional pairing. These estimates allow implementors to make optimal algorithm choices for given scenarios, in which the number of pairings in the product, the security level, and the embedding degree are factors under consideration.

 
## Summary (Korean)
+ 많은 pairing 기반 프로토콜들은 여러차례의 pairing 연산들을 필요로함.
+ 이 논문에서는, 위와 같은 상황에서, Weil, Tate, Ate pairing 알고리즘을 최적화함. Pairing-Friendly Fields이어야함(Fp가 f(X) = X^k + f0 꼴로 표현되는 경우). 128-bit security 기준으로는, 상대적으로 각 알고리즘의 cost(페어링 횟수)를 0.61, 0.45, 0.43 수준으로 낮춤. 특히, Ate pairing의 경우에는 더 높은 security level에 대해서는 약 0.13 수준으로 낮춤.

### Points to note

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
