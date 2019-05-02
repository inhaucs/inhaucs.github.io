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
일반적인 face verification에서는 feature normalization이 성능 향상을 위해 매우 중요하다. 수학적인 분석을 통해 feature normalization 관련된 4가지 이슈를 확인한다. 그리고, normalized features를 이용한 training을 위해 두가지 전략으로 softmax loss의 변형 버전과 각 class들 간의 agent vector를 도입하여 metric learning을 재구성하는 방법을 제안하였다. 

## Details


### Contents of the paper
Abstract
+ CNN의 발전과 함께 face verification의 성능도 급격히 좋아짐.
+ 일반적인 face verification에서는 **feature normalization**이 성능 향상을 위해 매우 중요함.
+ 수학적인 분석을 통해 feature normalization 관련된 4가지 이슈를 확인하고 공부하였음. => normalized features를 이용한 training을 위해 두가지 전략을 제안하겠다.
+ 첫번째 전략) softmax loss의 변형 버전. inner-product 대신에 cosine similarity를 최적화하는 방법(?).
+ 두번째 전략) 각 class들 간의 agent vector를 도입하여 metric learning을 재구성하는 것.

Introduction
+ 얼굴 인증에 있어서 CNN은 인간의 능력을 넘어선 수준.
+ feature comparison 하는 과정에서는, Euclidean distance 나 cosine similarity 많이 사용.
+ training phase 에서는 inner product without normalization 을 사용, testing phase 에서는 inner product with normalization(i.e. cosine similarity)를 사용.
+ face verification community 에서는 왜 testing phase에 normalization 되어야하는지 설명 못했었음. 일종의 testing 성능을 끌어올리기 위한 trick 정도였음.
+ 이 논문은, 왜 그동안 training 단계에서 inner-product layer with nomalization이 불가능했는지와 이 논문이 이것을(training phase 에서 normalization을 적용하는 것) 어떻게 가능하게 했는지 방법을 제안한다.
+ 결론적으로 다음 RQ 4가지를 해결한다.
    1. 특히, softmax loss로 train한 CNN feature들을 비교할때에, 왜 featrue normalization이 효과적일까?
    2. softmax loss를 이용하여 cosine similarity를 직접적으로 최적화하려고 하면, 네트워크 학습시 왜 수렴에 실패할까?
    3. softmax loss를 사용할 때 어떻게하면 cosine similarity를 최적화할 수 있을까
    4. normalized features를 위한 적절한 다른 loss functions 도 있을까? softmax loss 말고.

Related works
+ Face Verification은 두가지 다른 loss function을 사용함
    1. metrlc learning loss functions
    2. softmax loss를 활용하여 classification 문제로써 verification 하는 것
+ Normalization에 대한 최근 연구
    1. Cosine Loss, vMFMM과 본 논문의 loss functions는 featrue 와 weight를 둘다 최적화하는 반면에, L2-softmax는 feature만을, SphereFace는 weight만을 normalize하였다.

L<sub>2</sub> Normalization Layer
+ 
{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig1.PNG" legend="L<sub>2</sub> Normalization Layer definition" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig2.PNG" legend="Original softmax" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig3.PNG" legend="Modified softmax (optimized for nomalized vector" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig2.PNG" legend="Original contrastive loss" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig2.PNG" legend="Original triplet loss" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig3.PNG" legend="Modified contrastive loss (optimized for nomalized vector" %}

{% include articles/figure.html url="/assets/img/seongyun/2019/05-02-2019-ms-session3-fig3.PNG" legend="Modified triplet loss (optimized for nomalized vector" %}

### Points to note



## Discussion
Editor: 
+ 

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
