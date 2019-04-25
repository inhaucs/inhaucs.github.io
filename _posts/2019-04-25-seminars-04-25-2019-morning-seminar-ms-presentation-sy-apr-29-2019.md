---
title: "Session 3. NormFace: L<sub>2</sub> Hypersphere Embedding for Face Verification"
date: 2019-04-25 00:00:00 Z
description: "NormFace: L<sub>2</sub> Hypersphere Embedding for Face Verification"
card_title: Session 3
card_teaser: "NormFace: L<sub>2</sub> Hypersphere Embedding for Face Verification"
card_position: 3
icon: fa-server
categories: [seminars,04-29-2019-morning-seminar,presentation]
tags: [ACMMM, 2017, ACMMM, Face Verification, Metric Learning, Feature Normalization]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-apr-29-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-04-29

## [NormFace: L<sub>2</sub> Hypersphere Embedding for Face Verification](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-sy-apr-29-2019.html)

### Information of the paper [(Link)](https://dl.acm.org/citation.cfm?id=3123266.3123359)
+ Authors: Feng Wang, Xiang Xiang, Jian Cheng, Alan Loddon Yuile (University of Electronic Science and Technology of China, Johns Hopkins University)
+ Conference name: 25th ACM international conference on Multimedia
+ Published date: 2017-08-23
+ [Paper Link](https://dl.acm.org/citation.cfm?id=3123266.3123359)
+ [Paper Link(arXiv)](https://arxiv.org/pdf/1704.06369.pdf)


### Abstract
Thanks to the recent developments of Convolutional Neural Networks, the performance of face verification methods has increased rapidly. In a typical face verification method, feature normalization is a critical step for boosting performance. This motivates us to introduce and study the effect of normalization during training. But we find this is non-trivial, despite normalization being differentiable. We identify and study four issues related to normalization through mathematical analysis, which yields understanding and helps with parameter settings. Based on this analysis we propose two strategies for training using normalized features. The first is a modification of softmax loss, which optimizes cosine similarity instead of inner-product. The second is a reformulation of metric learning by introducing an agent vector for each class. We show that both strategies, and small variants, consistently improve performance by between 0.2% to 0.4% on the LFW dataset based on two models. This is significant because the performance of the two models on LFW dataset is close to saturation at over 98%.

## Summary (Korean)


## Details


### Contents of the paper


### Points to note



## Discussion
Editor: Hee-Yong Kwon
+ Security model이 Honest-but-Curious Server & Honest Client인데, 이후 진행되는 연구들에서 이 모델을 어떻게 극복할지를 관심있게 볼 수 있을듯
+ Participants 가 둘인 경우, 한 Participant가 모델을 완전 복구 가능한지 -> 이를 Honest Client로 해결한 것인지


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
