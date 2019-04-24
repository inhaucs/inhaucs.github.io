---
title: Session 2. Privacy-Preserving Deep Learning via Additively Homomorphic Encryption
date: 2019-04-24 00:00:00 Z
description: Privacy-Preserving Deep Learning via Additively Homomorphic Encryption
card_title: Session 2
card_teaser: Privacy-Preserving Deep Learning via Additively Homomorphic Encryption
card_position: 2
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [TIFS, 2017, Privacy, DeepLearning, Homomorphic encryption]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-04-25

## [Privacy-Preserving Deep Learning via Additively Homomorphic Encryption](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-jh-apr-25-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8302552)
+ Authors: Le Trieu Phong; Yoshinori Aono; Takuya Hayashi; Lihua Wang; Shiho Moriai (in National Institute of Information and Communications Technology in Tokyo)
+ Journal name: IEEE Transactions on Information Forensics and Security
+ Published date: 2017-12-29
+ [Paper Link](https://ieeexplore.ieee.org/document/8241854)


### Abstract
We present a privacy-preserving deep learning system in which many learning participants perform neural network-based deep learning over a combined dataset of all, without revealing the participants' local data to a central server. 
To that end, we revisit the previous work by Shokri and Shmatikov (ACM CCS 2015) and show that, with their method, local data information may be leaked to an honest-but-curious server. 
We then fix that problem by building an enhanced system with the following properties: 1) no information is leaked to the server and 2) accuracy is kept intact, compared with that of the ordinary deep learning system also over the combined dataset. 
Our system bridges deep learning and cryptography: we utilize asynchronous stochastic gradient descent as applied to neural networks, in combination with additively homomorphic encryption. 
We show that our usage of encryption adds tolerable overhead to the ordinary deep learning system.


## Summary (Korean)

기존에 제안된 Privacy-Preserving deep learning 기법( [[SS15]](SS15) )이 공격됨을 보이고, 이와 같은 세팅에서 Additively Homomorphic Encryption (AHE)를 사용하여 보다 안전한 딥러닝을 수행할 수 있도록 한 논문이다.

이 때, 딥러닝이란 Neural network를 돌린 어떠한 결과를 직접적으로 얘기하는 것이 아니라, Asynchronous (aka. Donwpour) SGD를 계산하는 것을 의미하며, 본 논문에서 가정하는 세팅은 여러 데이터 제공자가, Cloud 등을 이용하여 Model을 학습하는데, 그 과정을 함께하는 것을 의미한다. 

즉, 자신의 정보가 타 참여자(데이터 제공자)에게 공개되지 않는 상태에서 모델을 학습할 수 있는 것을 의미한다. 



## Details

### Contents of the paper

#### [Shokri-Shmatikov systems](SS15) *in ACM-CCS 2015*

+ Gradients-selective ASGD라고 불리는 프라이버시 보장형 딥러닝 시스템
+ W_global = W_global - a*G^{selective}_{local}
  + G^{selective}_{local}는 G_local의 1~10%정도의 선택적인 gradients만이 포함되어 있다함
  + 어려운 개념은 아니고, 상기 식을 통해 각 참자가 선택적인 그라디언트만을 클라우드로 보내, 전체 집합을 노출 시키는 것을 막는 방식이라고 함.
  + 자연스럽게, leakage가 발생하는데, Laplace noise를 이용한 Differential Privacy (DP) 기법을 이용하여 이러한 leakage를 방지한다 함.
+ 이 논문에서는 이러한 DP 기법을 이용한 프라이버시 보호가 취약함을 보임.
  + 굉장히 적은 정보만으로도 (1~10% 정도의 gradients) 학습에 사용된 원본 이미지를 획득할 수 있다는 것을 복원(recover) 공격을 통해 보임.

#### The system of the paper

+ 암호학적인 해결 방법 (Additively homomorphic encryption)으로 [[SS15]](SS15)를 해결한 방법

+ Gradients-encrypted ASGD라고 불림

+ **E**(W_global) = **E**(W_global) + **E**(-a*G_local)

  + 암호화된 상태로 그라디언트 디센트를 수행함.
  + Honest-but-curious cloud server와 honest client (사실상 honest-but-curious라 볼 수 있음)에 대해 안전함.
  + SSL/TLS 또한 함께 있어야 안전성이 보장됨.

+ AHE로써 Paillier와 LWE-based AHE 두가지 기법을 고려하였음.

  + Paillier: 분석만을 수행함. (post-quantum이 아니라...)
  + LWE-based AHE는 실험을 수행함.

+ System
  {% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-25-fig-system-overview.PNG" legend="System overview" %}

+ Results
  {% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-25-fig-results.PNG" legend="Results using LWE-based AHE scheme" %}

  + (10): LWE 스타일로 인코딩한 데이터.
  + (11): AHE 덧셈 ( **E**(r) + **E**(-t) ).
  + [MNIST dataset](MNIST)에는 n_gd (number of gradient parameters)가 **109386**으로 사용됨
    + MNIST db : 구분이 잘 되는 수준의 handwritten digits
  + [SVHN dataset](SVHN)에는 n_gd가 **402250**으로 사용됨
    + SVHN dataset : real-world image dataset으로 길에 있는 숫자들

      {% include articles/figure.html url="http://ufldl.stanford.edu/housenumbers/examples_new.png" legend="SVHN examples" %}

+ Estimating the computation costs of multilayer perceptron (MLP)

  + 이 논문에서는 단위 실험을 수행한 후, 전체 성능을 예측하는 형태를 취함.

  + 예제로 MNIST dataset에 관한 성능을 예측 하였는데, 그 결과가 다음과 같음.

    {% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-25-fig-estimate-performance.png" legend="Computation Cost Esitmation of MLP for MNIST" %}


### Points to note

+ Estimating the computation costs 부분을 추후 참조할 수 있을 것으로 보임.
  +  굉장히 이해하기 쉽게 잘 써있음.
+ 본 논문의 셋팅을 유지하면서, 보다 어려운 안전성 모델을 고려해볼 수 있을 것.
+ 동 저자의 유사한 [논문](<https://arxiv.org/abs/1809.03272>)을 추후 찾아봐도 좋을 듯
  + Title: Privacy-Preserving Deep Learning via Weight Transmission
+ "기존 방법(꽤 좋은 결과) -> 공격 -> 대안 제안" 의 구조는 늘 참조하기 좋을 것으로 보임.



[SS15]: https://dl.acm.org/citation.cfm?id=2813687

[SVHN]: http://ufldl.stanford.edu/housenumbers/

[MNIST]: http://yann.lecun.com/exdb/mnist/




## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
