---
title: Lecture 05. Logistic Classification의 가설 함수 정의
date: 2019-07-02 00:00:00 Z
description: Lecture 05
card_title: Lecture 05
card_teaser: Logistic Classification의 가설 함수 정의
card_position: 6
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-05
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-08

### Information of the lecture
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=PIjno6paszY&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=6vzchGYEJBc&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec5.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=2FeWGgnyLSw&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab5.pdf?raw=true)

### Lecture_1
### Logistic (regression) classification
+ Linear regression 복습 : Hypothesis, Cost, Gradient descent
+ Binary classification 예시
  + Spam detection: Spam or Ham
  + Facebook feed: show or hide
  + Credit Card Fraudulent Transaction detection: legitimate or fraud
+ 공부에 투자한 시간에 따른 합격(1), 불합격(0) 분류를 예시로 들어 설명
  + Linear regression 에서 사용한 Hypothesis인 $WX$를 사용할 수도 있으나, 문제 발생
    + 극단값에 취약함
    + 또한 $WX$는 분류 목표값인 [0, 1] 이외의 값도 가능함
    + 따라서 $H(X)$를 0 ~ 1 의 값으로 하는 함수 고려
      + **Sigmoid function(Logistic function)** : $g(z) = \frac{1}{1 + e^{-z}}$
  + Sigmoid function의 z를 weighted equation으로 치환
    + **Logistic Hypothesis** $H(X) = \frac{1}{1 + e^{-W^TX}}$

<br>

### Lecture_2
### Logistic (regression) classification: cost function & gradient descent
+ Cost function of Linear regression
  + $cost(W,b) = \frac{1}{m} \sum^m_{i=1} (H(x^{(i)})-y^{(i)})^2$ when $H(x) = Wx + b$
+ $H(x) = Wx + b$의 경우 Cost function이 매끄러운 곡선이지만, $H(X) = \frac{1}{1 + e^{-W^TX}}$로 변경됨에 따라 Cost function이 울퉁불퉁한 곡선으로 변경됨
  + Hypothesis가 Linear하지 않기 때문
  + 때문에, Gradient descent를 바로 적용할 경우, 시작 위치에 따라 Global minimum을 찾기 어려움 -> Local minimum으로 수렴할 수 있음
    + 기존의 Gradient descent를 사용할 수 없음
+ New cost function for logistic
  + $cost(W) = \frac{1}{m} \sum c(H(x), y)$
    + $c(H(x),y) = $$$\begin{cases} -log(H(x)) & :y=1 \\ -log(1-H(x)) & :y=0 \end{cases}$$
  + Cost function의 울퉁불퉁한 곡선을 매끄럽게 만들기 위해 log 사용
    + $H(x) = 1$이고 $y = 1$인 경우, $C(H(x),y)$가 0에 가까워짐 ($H(x) = 0$ and $y = 0$)
    + $H(x) = 1$이고 $y = 0$인 경우, $C(H(x),y)$가 $\infty$에 가까워짐 ($H(x) = 0$ and $y = 1$)
  + 상기 식에서 **if** 조건 제거
    + $C(H(x),y) = -y \log{(H(x))} - (1-y) \log{(1-H(x))}$
+ Cost function이 주어졌으므로, Minimize 가능
  + $cost(W) = -\frac{1}{m} \sum y \log{(H(x))} + (1-y) \log{(1-H(x))}$
  + $W := W - \alpha \frac{\delta}{\delta W} cost(W)$
    + 미분은 TF 라이브러리가 해줄 것

<br>

### Tensorflow
#### Logistic (regression) classifier
+ Logistic Regression
  + $cost(W) = -\frac{1}{m} \sum y \log{(H(x))} + (1-y) \log{(1-H(x))}$
  + $W := W - \alpha \frac{\delta}{\delta W} cost(W)$
+ Gradient descent와 같이 cost function의 경사면을 따라 내려감
+ Tensorflow
  + Training Data
    + 입력이 2인 경우를 가정
      ```
      X = tf.placeholder(tf.float32, shape=[None, 2]) // None: 입력 또는 출력의 개수가 정해지지 않은 경우
      Y = tf.placeholder(tf.float32, shape=[None, 1])
      ```
  + Hypothesis using sigmoid
    + $H(X) = \frac{1}{1+ e^{-W^T X}}$
    ```
    hypothesis = tf.sigmoid(tf.matmul(X,W) + b)
    ```
  + Cost/Loss function
    + $cost(W) = -\frac{1}{m} \sum y \log{(H(x))} + (1-y) \log{(1-H(x))}$
    ```
    cost = -tf.reduce_mean(Y * tf.log(hypothesis) + (1-Y) * tf.log(1 - hypothesis))
    ```
  + Gradient descent
    + $W := W - \alpha \frac{\delta}{\delta W} cost(W)$
    ```
    train = tf.train.GradientDescentOptimizer(learning_rate=0.01).minimize(cost)
    ```
  + Accuracy computation
    + True if hypothesis > 0.5 else False
    ```
    predicted = tf.cast(hypothesis > 0.5, dtype=tf.float32)
    accuracy = tf.reduce_mean(tf.cast(tf.equal(predicted, Y), dtype=tf.float32))
    ```
  + Train
+ 질병 예측 데이터를 사용하여 실습(당뇨병 데이터)

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
