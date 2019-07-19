---
title: Session 2. 2019NSR - CNN, RNN, Autoencoder
date: 2019-07-04 00:00:00 Z
description: 2019NSR - CNN, RNN, Autoencoder
card_title: Session 2
card_teaser: 2019NSR - CNN, RNN, Autoencoder
card_position: 2
icon: fa-server
categories: [seminars,07-04-2019-morning-seminar,presentation]
tags: [Deep Learning, Machine Learning, CNN, RNN, Autoencoder]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-july-04-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son(손예별)
+ 2019-07-04

## [2019NSR - CNN, RNN, Autoencoder](https://inhaucs.github.io/seminars/07-04-2019-morning-seminar/presentation/ms-presentation-yb-july-04-2019.html)

### [PPT](http://gofile.me/6uXSD/hH8KLS5CC)
+ 위치 : NAS-Level1-국가암호기술전문인력양성과정-2019국가암호기술전문인력양성과정-20190524_NSR_PPT.pdf
+ Published date: 2019-05-24
+ [CODE](http://3.14.140.1:8888)

#### Abstract
+ CNN, RNN, Autoencoder 기본 개념 및 MNIST를 이용한 코드 이해
+ PPT보며 설명할 예정이고, 참조자료 및 개인 의견 적어놓았습니다.

### Reference
#### [What's difference between conv layer and pooling layer in CNN?](https://stackoverflow.com/questions/43485361/whats-the-difference-between-conv-layer-and-pooling-layer-in-cnn)
+ Convolution layer : 필터를 이용해서 그림의 패턴을 얻어오는 부분. 줄이는 것보다는 원하는 패턴을 더 부각시켜 얻어낸다는 의미가 더 강함.
+ Pooling layer : 일단 크기를 줄일건데 어떤 값이 제일 중요한가? 따지는 부분이라고 생각하면 될 듯.

#### [이미지 인식을 위한 CNN들](http://aikorea.org/cs231n/convolutional-networks/)

#### [RNN](https://skymind.ai/kr/wiki/lstm)
+ RNN은 FNN과는 좀 다릅니다. RNN은 지금 들어온 입력 데이터와 과거에 입력 받았던 데이터를 동시에 고려합니다. 아래의 Elman이 제안한 아주 간단한 RNN의 구조도를 보면(PPT-11page하단 그림), 입력으로 BTSXPE가 들어오는데 은닉층에서는 이 입력데이터와 좌측 하단의 CONTEXT UNIT을 다 입력으로 받습니다."

#### Autoencoder performance
{% include articles/figure.html url="/assets/img/byoul/2019/2019070301.png" legend="Autoencoder_CNN_MNIST"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019070302.png" legend="Autoencoder_CNN_CIFAR10"%}


## Points to note

## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
