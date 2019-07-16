---
title: Lecture 02. Linear Regression의 Hypothesis 와 cost 설명
date: 2019-07-02 00:00:00 Z
description: Lecture 02
card_title: Lecture 02
card_teaser: Linear Regression의 Hypothesis 와 cost 설명
card_position: 3
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-02
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-03

### Information of the lecture
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=Hax03rCn3UI), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec2.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=mQGwjrStQgg&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab2.pdf?raw=true)

### Lecture
### Linear Regression
+ Regression의 예시 : Predicting exam score
+ Linear regression
  + 식을 $H(x) = Wx + b$ 로 가정
  + H(x)로 나타내는 여러가지 직선 중 어떤 직선을 선택할 것인지 정해야 함 (W와 b의 결정)
      + Cost(Loss) function 사용
      + Data와 차이가 가장 적은 직선 선택
        + $cost = \frac{1}{m} \sum^m_{i=1} (H(x^{(i)})-y^{(i)})^2$
        + 상기 cost function의 $H(x^{(i)})$에 $H(x) = Wx + b$를 대입하면 $cost(W,b)$로 표현 가능하고, $\min\limits_{W,b} cost(W,b)$를 구하는 것이 목표
+ Point
  + Linear regression은 입력 데이터에 가장 적합한 직선을 찾는 것이 목표이며 이를 위해 cost(loss) function을 사용
  + Cost function은 입력 데이터와 현재 직선과의 거리 차이를 구한 것으로, 이 거리가 최소화되는 직선이 가장 최적의 직선이라고 생각할 수 있음
    + 따라서, 직선의 방정식이 $H(x) = Wx + b$일 때, $cost(W,b) = \frac{1}{m} \sum^m_{i=1} (H(x^{(i)})-y^{(i)})^2$를 최소화하는 $W$와 $b$를 구해야 함

<br>

### Tensorflow
+ Goal
  + Tensorflow를 이용한 Linear regression 구현
  + Hypothesis
    + $H(x) = Wx + b$
    + $W$: weight, $b$: bias
  + Cost function
    + $cost(W,b) = \frac{1}{m} \sum^m_{i=1} (H(x^{(i)})-y^{(i)})^2$
+ Build graph
    + Training set 정의
    + tf.Variable로 $W, b$ 정의
    + TF의 Variable은 trainable 변수를 의미함
    + Hypothesis 정의
      ```
      hypothesis = x_train * W + b
      ```
    + Cost function 정의
      ```
      cost = tf.reduce_mean(tf.square(hypothesis - y_train))
      ```
      + reduce_mean 함수는 평균을 내주는 함수로 cost function의 $\frac{1}{m}\sum^m_{i=1}$에 해당
    + Cost를 최소화하는 값을 찾기 위해 GradientDescent 사용
      + 현재는 자세히 설명하지 않음
+ Run/update graph
    + Session 생성 후, 전역 변수 초기화
      ```
      sess.run(tf.global_variables_initializer())
      ```
    + GradientDescent 연산을 매 step 수행하는 방법 설명
      + $W,b$ update
    + train, cost, hypothesis, $W$, $b$ 텐서들의 관계에 대해 그래프를 통해 설명
+ Placeholder를 사용해 Linear regression을 수행하는 방법 설명
+ Training 후, Test하는 방법 소개
  ```
  sess.run(hypothesis, feed_dict={X:[5]}) // 다음과 같이 Y 값을 제외하고 전달하면, X가 모델에 입력되었을 때 예상되는 Y 값을 반환
  ```  

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
