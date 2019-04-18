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
+ Hee-Yong Kwon (전성윤)
+ 2019-04-22

## Information of the paper
+ Authors: Anand D. Sarwate (Toyota Technological Institute); Kamalika Chaudhuri (University of California)
+ Conference name: IEEE Signal Processing Magazine
+ Published date: 2013-08-19
+ [Paper file](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6582713)

## Abstract
Private companies, government entities, and institutions such as hospitals routinely gather vast amounts of digitized personal information about the individuals who are their customers, clients, or patients. Much of this information is private or sensitive, and a key technological challenge for the future is how to design systems and processing techniques for drawing inferences from this large-scale data while maintaining the privacy and security of the data and individual identities. Individuals are often willing to share data, especially for purposes such as public health, but they expect that their identity or the fact of their participation will not be disclosed. In recent years, there have been a number of privacy models and privacy-preserving data analysis algorithms to answer these challenges. In this article, we will describe the progress made on differentially private machine learning and signal processing.

## Summary (Korean)
+ 

## Details
+ Machine Learning(ML) Section Skip. (Supervised, Unsupervised, Semisupervised, etc.)
  + ML은 세 가지 요소로 구성됨
    + **Input party** : 데이터 제공자
    + **Computation party** : ML 연산 수행자
    + **Results party** : ML 모델을 사용자
  + 상기 세 요소가 같은 주체에서 구성되는 경우 프라이버시는 고려할 필요가 없으나, 일반적으로 **Computation party**와 **Results party**는 한 주체에 있고 **Input party**만 분리되어 구성됨.
 하는지 회사에게 적용되어야 하는지. 또 적용하고 있는 회사(Google and Apple, LDP)에서 적용하는 방법이 실제로 효과가 있는 것인지 설명되어야 함.  

[title]: <url> "describ"

## Point to note
+ write something

## Discussion
Editor: ??
+ write our discussion

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
