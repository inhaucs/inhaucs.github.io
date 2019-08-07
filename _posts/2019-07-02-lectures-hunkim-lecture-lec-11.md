---
title: Lecture 11. Convolutional Neural Networks
date: 2019-07-02 00:00:00 Z
description: Lecture 11
card_title: Lecture 11
card_teaser: Convolutional Neural Networks
card_position: 12
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-11
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-08-07

### Information of the lecture
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=Em63mknbtWo&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=2-75C-yZaoA&feature=youtu.be), [Youtube(Lecture_3)](https://www.youtube.com/watch?v=KbNbWTnlYXs&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec11.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=E9Xh_fc9KnQ&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=pQ9Y9ZagZBk&feature=youtu.be), [Youtube(Tensorflow_3)](https://www.youtube.com/watch?v=c62uTWdhhMw&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab11.pdf?raw=true)

### Lecture_1
#### CNN Introduction
+ 기본 아이디어는 고양이 실험에서 유래
  + 고양이에게 그림을 보여주고, 그림의 형태에 따라 고양이의 뉴런이 다르게 동작함에서 Motivation
+ $32 \times 32 \times 3$의 이미지가 있다고 가정
  + Convolution layers
    + Convolution layer와 ReLU 적용까지를 의미
    + $5 \times 5 \times 3$의 필터를 정의, 필터의 크기는 입력의 크기: 즉 한 필터에서는 하나의 입력이 생성됨
      + 이미지 크기 전체인, $32 \times 32 \times 3$에 적용
      + Stride: 필터를 적용하는 스텝의 크기 (이동 거리)
      + 필터를 적용한 출력의 크기: (원래 이미지 크기 - 필터 크기) / 스트라이드 + 1
    + 필터를 사용함으로 인해, 이미지가 점점 작아짐 (정보 손실)
      + 이에 이미지 크기가 유지되도록, 이미지 가장자리에 가상의 패딩 적용
      + 0 패딩이 일반적임
    + 필터는 하나가 아닌 여러 개 적용 가능
      + 여러 개의 필터로 인해 계산된 여러 개의 출력의 Activation maps 생성
    + Activiation maps은 다음 Convolution layers의 입력이 됨
    + 적용되는 필터의 종류 또는 개수는 Convolution layers에 따라 다를 수 있음

<br>

### Lecture_2
#### ConvNet Max pooling과 Full Network
+ Pooling layer == Sampling == Subsampling
  + 여러 필터를 적용해 생성된 Activiation maps의 이미지들을 추출해 resize (sampling)
  + Convolution layers의 필터 적용과 비슷하지만, 정책이 다름
  + 전체 값 중 하나를 선택하기 때문에 Sampling이라 함
+ Max Pooling
  + 필터 내의 가장 큰 값을 Sampling 하는 방법으로, 일반적으로 사용됨
+ CNN에서 네트워크의 구성
  + Convolution layers, ReLU, Pooling은 네트워크 제작자의 마음대로 작성할 수 있음
+ Fully Connected Layer: 이전 레이어의 모든 노드가 다음 레이어의 모든 노드에 연결된 레이어
  + FC Layer 또는 Dense Layer라고도 함

<br>

### Lecture_3
#### CNN case study
+ LeNet-5
  + LeCun et al., 1998
  + 흑백 필기 알파벳(32*32*1) 분류
+ AlexNet
  + Krizhevsky et al, 2012
  + (227*227*3)의 이미지 분류
  + First use of ReLU
  + 7 CNN ensemble: 18.2% $rightarrow$ 15.4% (error)
+ GoogleNet
  + Szegedy et al., 2014
  + Inception module 사용: Convolution, Pooling을 동시에 사용하여 레이어를 확장 후 병합하는 방법 사용
+ ResNet
  + He et al., 2015
  + Layer Comparison
    + AlexNet, 8 layers
    + VGG, 19 layers
    + ResNet, 152 layers
  + 학습 속도의 개선을 위해 fast forward 사용
    + 여러 개의 레이어를 하나의 레이어처럼 학습
+ CNNs for sentence Classification
  + Yoon Kim, 2014
  + Text Syntax에 대해 CNN 사용 (Natural Language Processing: NLP)
+ DeepMind's AlphaGo

<br>

### Tensorflow_1
#### TensorFlow CNN Basics
+ **CNN = Convolution과 subsampling의 반복 후, Fully connected layer를 통해 classification**
+ Simple convolution layer
  + e.g., (3*3*1) image, (2*2*1) filter $w$, Stride: (1*1)을 예제로 사용
  + Tensorflow에서 Padding option: SAME 인 경우, 입력 이미지의 크기와 출력 이미지의 크기가 같음(0 패딩), when stride가 (1*1)
  + 기본적인 convolution layer와 max pooling 구현

<br>

### Tensorflow_2
#### CNN MNIST: 99%!
+ CNN 사용시 유의해야하는 각 변수의 shape에 대해 자세히 설명
+ Deep CNN with MNIST
  + Convolution layer 3개, Fully connected layer 2개 사용한 CNN
  + Dropout 사용
  + **Accuracy: 0.9938**

<br>

### Tensorflow_3
#### CNN Class, Layers, Ensemble
+ Tensorflow_2에서 소개한 CNN을 작성함에 있어 Python의 Class 기능을 사용하는 방법 소개
+ Tensorflow에 이미 작성되어 있는 high level code인 tf.layers를 사용하여 쉽게 사용
+ Ensemble
  + 여러 개의 독립된 모델을 학습한 후, 테스트 시 각각의 모델의 예측 결과를 조합하여 최종 결과 도출

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
