---
title: Lecture 03. Linear Regression의 cost 최소화 알고리즘의 원리 설명
date: 2019-07-02 00:00:00 Z
description: Lecture 03
card_title: Lecture 03
card_teaser: Linear Regression의 cost 최소화 알고리즘의 원리 설명
card_position: 4
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-03
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
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=TxIVr-nk1so), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec3.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=Y0EF9VqRuEA&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab3.pdf?raw=true)

### Lecture
### How to minimize cost
+ Cost function
  + $cost(W,b) = \frac{1}{m} \sum^m_{i=1} (H(x^{(i)})-y^{(i)})^2$
  + Cost function을 최소화하는 $W,b$를 구하는 것이 목표
  + Simplified hypothesis
    + $H(x)=Wx$
    + $cost(W) = \frac{1}{m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})^2$
    + e.g., $x=[1,2,3], y=[1,2,3]$에서 $W=1$일 때, $cost(W)=?$ $\rightarrow 0$
    + e.g., $x=[1,2,3], y=[1,2,3]$에서 $W=0$일 때, $cost(W)=?$ $\rightarrow 4.67$
    + e.g., $x=[1,2,3], y=[1,2,3]$에서 $W=2$일 때, $cost(W)=?$ $\rightarrow 4.67$
    + 상기 예시들의 그래프($W, cost$)를 그려보면 포물선 그래프가 생성됨
      + Cost function이 최소화되는 부분은 극점
+ **Gradient descent algorithm** : 최소화되는 지점을 찾기 위해 사용되는 알고리즘
  + 경사를 따라 내려가는 알고리즘
  + $cost(w\_1, w\_2, \ldots)$와 같이 일반적인 경우에도 사용 가능
  + 높은 지점에서 낮은 방향을 향해 계속 내려가며 가장 낮은 부분을 찾는 방식으로 동작
    + 현재 지점에서 경사가 낮은 방향으로 이동
  + 동작 순서
    + $(W, cost)$ 그래프의 임의의 지점에서 시작
    + $W$를 수정하고 $cost(W,b)$ 재계산
    + 반복
  + 경사를 구하는 데는 미분을 사용하는데 이를 따라가보자
    + 단순화를 위해 cost function을 $cost(W) = \frac{1}{m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})^2 \rightarrow cost(W) = \frac{1}{2m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})^2$로 수정
    + Derivation
      + $W := W - \alpha \frac{\delta}{\delta W} cost(W)$ where $\alpha$ is learning rate
      + $W := W - \alpha \frac{\delta}{\delta W} \frac{1}{2m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})^2$
      + $W := W - \alpha \frac{1}{m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})x^{(i)}$
        + 상기 Gradient descent algorithm을 반복하여 cost function을 최소화하는 $W$를 구할 수 있음
  + Gradient descent algorithm을 사용할 때, convex function이 아니라면 global minimum이 아닌 local minimum을 찾을 수 있으므로, convex를 확인하는 것이 중요

<br>

### Tensorflow
+ TF를 사용한 Minimizing Cost 실습
+ Simplified hypothesis 사용
  + $cost(W) = \frac{1}{m} \sum^m_{i=1} (Wx^{(i)}-y^{(i)})^2$
+ 먼저 $W$의 변화에 따른 $cost$를 matplotlib을 사용하여 시각화
+ Lec 02 에서 사용했던 Gradient descent에 대해 심화 설명
  + TF의 함수들을 사용해서 Gradient descent를 직접 작성해보는 실습 수행
    + TF는 = 기호로 할당할 수 없고 $W.assign$으로 할당을 수행
  + 그러나 직접 작성하지 않고 일련의 과정을 통해 수행 가능
    ```
    optimizer = tf.train.GradientDescentOptimizer(learning_rate=x.x)
    train = optimizer.minimize(cost)
    ```
+ (Optional) 심화 설명
  ```
  gvs = optimizer.compute_gradients(cost)를 통해 gradient값을 임의로 전달 가능
  ```

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
