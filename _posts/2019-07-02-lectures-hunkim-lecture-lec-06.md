---
title: Lecture 06. Softmax Regression. 기본 개념 소개 & Softmax classifier의 cost function
date: 2019-07-02 00:00:00 Z
description: Lecture 06
card_title: Lecture 06
card_teaser: Softmax Regression. 기본 개념 소개 & Softmax classifier의 cost function
card_position: 7
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-06
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
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=MFAnsx1y9ZI&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=jMU9G5WEtBc&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec6.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=VRnubDzIy3A&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=E-io76NlsqA&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab6.pdf?raw=true)

### Lecture_1
### Softmax Regression: 기본 개념 소개 (Softmax classification: Multinomial classfication)
+ Logistic regression
  + 기존의 Linear function $H_L(X)=WX$는 classification에 적합하지 않음
  + $z = H(X)$에 대하여 $g(z)$의 함수를 정의하였음
    + Sigmoid: $g(z) = \frac{1}{1 + e^{-z}}$ 를 정의하게 됨
    + $H_R(X) = g(H_L(X))$ $\rightarrow$ 0과 1 사이의 값 출력
  + Logistic regression에서 클래스를 구분하는 선 또는 면을 Hyperplane이라 함
+ Multinomial classification
  + Binary classification으로도 구현 가능
    + Binary Hyperplane을 여러 개 구현 (e.g., (A, B, C) 분류를 위해 (A or not), (B or not), (C or not) hyperplanes 구현)
    + $$ \begin{bmatrix} w_{1} & w_{2} & w_{3} \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \\ x_{3} \end{bmatrix} = \left[ w_1x_1 + w_2x_2 + w_3x_3 \right] $$ 연산을 세 번 독립적으로 수행하여 가능
      + 이를 한 번에 수행 가능
      + $$ \begin{bmatrix} w_{A1} & w_{A2} & w_{A3} \\ w_{B1} & w_{B2} & w_{B3} \\ w_{C1} & w_{C2} & w_{C3} \end{bmatrix} \begin{bmatrix} x_{1} \\ x_{2} \\ x_{3} \end{bmatrix} = \begin{bmatrix} w_{A1}x_1 + w_{A2}x_2 + w_{A3}x_3 \\ w_{B1}x_1 + w_{B2}x_2 + w_{B3}x_3 \\ w_{C1}x_1 + w_{C2}x_2 + w_{C3}x_3 \end{bmatrix} = \begin{bmatrix} H_A(X) \\ H_B(X) \\ H_C(X) \end{bmatrix} $$.
    + 상기 연산을 효율적으로 하는 방법에 대해 Lecture_2 에서 설명

<br>

### Lecture_2
### Softmax classifier의 cost function
+ Multinomial classification 결과가 0과 1 사이의 값으로 출력되기를 원함 $\rightarrow$ Softmax
  + Softmax Equation
    + $S(y_i) = \frac{e^{y_i}}{\sum_j e^{y_j}}$
  + $$ \begin{bmatrix} H_A(X) \\ H_B(X) \\ H_C(X) \end{bmatrix} = \begin{bmatrix} 2.0 \\ 1.0 \\ 0.1 \end{bmatrix} $$일 때, Softmax를 사용하여 $$ \begin{bmatrix} 0.7 \\ 0.2 \\ 0.1 \end{bmatrix} $$ ($\sum = 1$)이 되도록 함
    + 0과 1 사이의 값
    + $\sum = 1$
    + 확률로 표현 가능
    + 'ONE-HOT' ENCODING (argmax)을 통해 $$ \begin{bmatrix} 1.0 \\ 0.0 \\ 0.0 \end{bmatrix} $$으로 표현 가능
+ Cost function
  + Cross-Entropy 사용
  + 예측값 $S(y) = \hat Y$, 실제 값 $L = Y$일 때
    + Cross Entropy cost function: $D(S, L) = - \sum_{i} L_i \log{S_i}$
      + $-\sum_{i} L_i \log{S_i} = -\sum_{i} L_i \log{\hat Y_i} = \sum_{i} L_i \times (-\log{\hat Y_i})$
        + $-\log{\hat Y_i}$ 는 Softmax 연산이 수행된 값이기 때문에 $\left[ 0,1 \right]$
      + 예시를 통해 cost function이 동작함을 보임
        + $$ L = \begin{bmatrix} 0 \\ 1 \end{bmatrix} $$, $$\hat Y_1 = \begin{bmatrix} 0 \\ 1 \end{bmatrix} $$, $$\hat Y_2 =  \begin{bmatrix} 1 \\ 0 \end{bmatrix} $$ 를 사용하여, 예측이 맞은 경우와 틀린 경우의 cost function을 구함
  + **Logistic cost vs. cross entropy**
    + Logistic cost: $C(H(x),y) = -y \log{(H(x))} - (1-y) \log{(1-H(x))}$
    + Cross entropy: $D(S, L) = - \sum_{i} L_i \log{S_i}$
    + 두 cost function은 같은 식임
  + Cross entropy 공식에 따라 전체 cost function은 다음과 같음
    + $L(loss) = \frac{1}{m} \sum_i D(S(WX_i+b), L_i)$
    + 상기 식에 Gradient descent를 사용하여 최적화 가능

<br>

### Tensorflow_1
#### TensorFlow로 Softmax Classification 구현
+ Softmax Equation
  + $S(y_i) = \frac{e^{y_i}}{\sum_j e^{y_j}}$
  + Tensorflow
  ```
  hypothesis = tf.nn.softmax(tf.matmul(X,W) + b) // tf.matmul(X,W) + b: scores
  ```
+ Cost function: cross entropy
  + $L(loss) = \frac{1}{m} \sum_i D(S(WX_i+b), L_i)$
  + Tensorflow
  ```
  # Cross entropy cost/loss
  cost = tf.reduce_mean(-tf.reduce_sum(Y * tf.log(hypothesis), axis=1))
  optimizer = tf.train.GradientDescentOptimizer(learning_rate=0.1).minimize(cost)
  ```
+ 'ONE-HOT' encoding 기법을 사용한 실습
+ 결과에 ```tf.arg_max(all, 1)```을 적용하여 보기 좋게 출력하는 방법

<br>

### Tensorflow_2
#### TensorFlow로 Fancy Softmax Classification의 구현하기
+ Softmax는 logits(socre)를 확률로 표현해 줌
+ softmax_cross_entropy_with_logits 함수 소개
  ```
  logits = tf.matmul(X,W) + b // logits = score
  hypothesis = tf.nn.softmax(logits)
  ```
  1) Cross entropy cost/loss
  ```
  cost = tf.reduce_mean(-tf.reduce_sum(Y * tf.log(hypothesis), axis=1)) // Y = one-hot
  ```
  2) hypothesis 대신 logits을 사용하는 방법
  ```
  cost_i = tf.nn.softmax_cross_entropy_with_logits(logits=logits, labels=Y_one_hot)
  cost = tf.reduce_mean(cost_i)
  ```
  + 1., 2. 의 cost는 같음
+ 동물의 특징에 기반한 데이터를 사용하여 분류 실습
  + 여러 개의 레이블($Y$)을 one-hot으로 바꿔주는 함수''
  ```
  Y = tf.placeholder(tf.int32, [None, 1]) // 0 ~ 6, shape=(?, 1)
  Y_one_hot = tf.one_hot(Y, nb_classes)   // one hot shape = (?, 1, 7)
  # 이대로 사용시 배열 모양으로 인한 에러 발생, 아래와 같이 reshape 후 사용
  Y_one_hot = tf.reshape(Y_one_hot, [-1, nb_classes]) // shape = (?, 7)
  ```
  + 예측한 값과 실제 값이 맞는지 확인
  ```
  prediction = tf.argmax(hypothesis, 1) // 0 ~ 6
  correct_prediction = tf.equal(prediction, tf.argmax(Y_one_hot, 1))
  accuracy = tf.reduce_mean(tf.cast(correct_prediction, tf.float32))
  ```
  + Python 문법 소개
  ```
  # y_data: (N,1) = flatten => (N, ) matches prediction.shape
  for p, y in zip(prediction, y_data.flatten()):
    print("[{}] Prediction: {} True Y: {}".format(p == int(y), p, int(y)))  // e.g., [True] Prediction: 0 True Y: 0
  ```

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
