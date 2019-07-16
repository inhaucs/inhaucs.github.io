---
title: Lecture 01. 기본적인 Machine Learning의 용어와 개념 설명
date: 2019-07-02 00:00:00 Z
description: Lecture 01
card_title: Lecture 01
card_teaser: 기본적인 Machine Learning의 용어와 개념 설명
card_position: 2
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-01
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-02

### Information of the lecture
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=qPMeuL2LIqY), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec1.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=-57Ne86Ia8w&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab1.pdf?raw=true)

### Lecture
### Machine Learning
+ Spam filter와 같이 규칙(rule)이 많은 경우, explicit programming을 하기 어려움
+ 이에 1959년 Arthur Samuel이 일일히 규칙을 프로그래밍 하지 않고 자료나 현상으로부터 자동으로 배우는 방법에 대해 제안 -> Machine Learning
  + "Field of study that gives computers the ability to learn without being explicitly programmed" Arthur Samuel (1959)

### Supervised/Unsupervised learning
+ 학습하는 방법에 따라 나누어지는 기준
+ Supervised
  + 정해져 있는 데이터(Labeled)를 사용하여 학습
+ Unsupervised learning
  + Un-labeled 데이터를 사용하여 학습

#### Supervised learning
+ E.g., Image labeling, Email spam filter, Predicting exam score 등
+ Training data set
  + Training data set으로 Labeled data (Feature-label set)를 학습하여 모델 생성 후, 모르는 Feature에 대해 예상되는 label 출력
+ Supervised learning의 분류
  + Regression
    + 투자한 시간에 따른 점수의 예측
  + Binary classification
    + 투자한 시간에 따른 시험의 통과 여부 (pass/fail)
  + Multi-label classification
    + 투자한 시간에 따른 시험 결과에 따른 학점 (A, B, C, E and F)
  + 분류에 따라 Training set이 달라짐

<br>

### Tensorflow

+ Tensorflow의 기본에 대한 설명
+ Google에서 만든 open source library for machine intelligence
+ Deep learning libraries
  + tensorflow, caffe, keras, mxnet, Theano, etc.
+ Data flow graphs를 사용해서 numerical computation을 하는 프로그램 & Python!
  + Nodes in graph: operations
  + Edges in graph: data arrays(tensors)
+ 실습 내용
  + 설치 방법 설명
  + TensorFlow Hello World! 출력
  + Computational Graph 만드는 법
  + Tensorflow의 구조
    + Tensorflow operations를 사용하여 graph 빌드(설계)
    + session.run(op)로 실행
    + 그래프 내의 변수들 업데이트 후 출력
  + 특정 값 (constant) 외에 다른 값을 입력하고 싶은 경우
    + tf.constant 대신 tf.placeholder로 생성
    + 그리고 session.run 시에 $feed_dict=\left{ a, b \right}$ 옵션을 사용하여 입력 (vector 입력 가능)
    + 즉 그래프를 미리 만들어놓고 다양한 입력에 대해 사용 가능
  + Tensor에 대한 설명
    + Ranks: 몇 차원 array인가 (x-Tensor)
    + Shapes: 각각의 엘리먼트에 몇 개의 정보가 들어있는가
      + E.g., $t = [[1,2], [3,4], [5,6]]$인 경우, $(3,2)$로 표현 가능
        + 가장 안의 괄호에 두 개의 엘리먼트이고, 이 것이 3 개 있으므로
    + Types: tf.float32(64), tf.int32(64) 등

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
