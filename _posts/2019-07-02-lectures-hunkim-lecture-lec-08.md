---
title: Lecture 08
date: 2019-07-02 00:00:00 Z
description: Lecture 08
card_title: Lecture 08
card_teaser: 딥러닝의 기본 개념. 시작과 XOR 문제 & Back-propagation 과 2006/2007 '딥'의 출현
card_position: 9
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-08
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

#Lecture 08 - 딥러닝의 기본 개념: 시작과 XOR 문제 & Back-propagation 과 2006/2007 '딥'의 출현

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-15

### Information of the lecture
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=n7DNueHGkqE&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=AByVbUX1PUI&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec8.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=ZYX0FaqUeN4&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab8.pdf?raw=true)

### Lecture_1
### 딥러닝의 기본 개념: 시작과 XOR 문제
+ 수학적인 내용과 컴퓨터공학적인 내용을 제외한 딥러닝 소개
  + 인간의 뉴런 설명
  + 뉴런과 비슷한 머신 설계 with Activation Functions
+ OR/AND 문제는 linearly separable 하지만, XOR는 불가능
  + Marvin Minsky (1969) 가 XOR 는 수학적으로 해결할 수 없는 문제임을 증명
  + Multi Layer Perceptron (MLP) 를 사용하면 해결되지만 weight을 학습하는 것이 불가능 할 것이라 함
  + 1974, 1982 (Paul Werbos), and 1986 (Hinton): Backpropagation을 제안함으로써 해결법 제시
    + 문제점
      + 레이어가 많아질수록 Backpropagation 의 Output 의 에러가 앞쪽으로 잘 전달되지 않음
      + 훨씬 간단한 SVM, RandomForest 등의 등장

<br>

### Lecture_2
### 딥러닝의 기본 개념: Back-propagation 과 2006/2007 '딥'의 출현
+ Backpropagation의 문제점: 레이어가 많은 경우 학습이 제대로 진행되지 않음
+ CIFAR: Canadian Institute for Adavanced Research
  + 돈이 되지 않더라도 딥러닝 연구가 가능하도록 연구자들 독려
  + 연구를 통해 Breakthrough가 되는 두 논문 발표
    + Hinton, Simon Osindero, and Yee-Whye Teh, "A fast learning algorithm for deep belief nets", 2006.
      + 레이어가 많을 때 weight 이 잘 학습되지 않는 것은 초기값을 제대로 주지 않았기 때문
    + Yoshua Bengio et al. "Greedy Layer-Wise Training of Deep Networks", 2007.
    + 상기 두 논문으로 인해 Neural networks 를 Deep Learning 으로 바꾸어 부르기 시작하였고, 다시 대두되기 시작함
  + ImageNet 또한 관심을 끄는데 도움
    + 2012, AlexNet의 등장 ImageNet Classification 의 에러율을 크게 줄임
    + 2015, 3\% 의 에러율까지 줄임
+ Deep learning이 필요한 이유 (Business 등)

<br>

### Tensorflow
#### Tensor Manipulation
+ Tensor 를 다루는 방법에 대한 실습
  + Tensorflow 를 효율적으로 다루기 위한 과정
+ Array Slicing에 대한 방법 리뷰
```
e.g., t[2:5], t[4:-1], t[2:], etc.
```
+ Shape, Rank, Axis
  + Rank 는 가장 바깥의 괄호의 수와 같음
  + Shape 은 데이터의 형태
  ```
  t = tf.constant([[[[1,2,3,4], [5,6,7,8], [9,10,11,12]],[[1,2,3,4], [5,6,7,8], [9,10,11,12]]]]) // Rank = 4, Shape = [1,2,3,4], Axis 는 Shape 의 순서 (axis = 0 인 경우 가장 바깥의 Element 로 이해)
  ```
+ Broadcasting: Shape 이 다른 행렬간의 연산을 가능하게 함
  + 그러나 사용 시에 인식하고 있는 연산과 다를 수 있으므로 주의를 요함
+ Reduce mean 에서의 Axis 사용 (+ Argmax 에서의 예시 포함)
```
x = [[1.,2.],[3.,4.]]
tf.reduce_mean(x).eval()          // 2.5
tf.reduce_mean(x, axis=0).eval()  // [2., 3.]
tf.reduce_mean(x, axis=1).eval()  // [1.5, 3.5]
```
+ **Reshape**
```
t = np.array([[[0,1,2], [3,4,5]], [6,7,8], [9,10,11]]])
tf.reshape(t, shape=[-1,3]).eval() // 보통 reshape 시에 가장 내부의 Element 개수는 그대로 유지
// Result
array([[0,1,2], [3,4,5], [6,7,8], [9,10,11]])
```
  + 특수 목적 Reshape (squeeze, expand)
    ```
    tf.squeeze([[0], [1], [2]]).eval()  // [0,1,2]
    tf.expand_dims([0,1,2], 1).eval()   // [[0], [1], [2]]
    ```
+ One hot 사용법
```
t = tf.one_hot([[0], [1], [2], [0]], depth=3)   // one hot 이 될 수 있는 값의 수
tf.reshape(t, shape=[-1,3]).eval()              // one hot 함수의 경우 rank 가 자동으로 하나 증가하므로 reshape을 통해 줄여줄 수 있음
```
+ Casting
  + True / False 를 0 / 1 로 표현
+ Ones and Zeros like
```
tf.ones_like(x).eval()  // x와 같은 모양에 1로 채워진 행렬 반환
tf.zeros_like(x).eval() // x와 같은 모양에 0으로 채워진 행렬 반환
```
+ Zip: 반복문 등에서 한 번에 여러 개의 입력을 받는 방법
```
for x, y in zip([1,2,3], [4,5,6]):
  print(x, y)
// Result
1 4
2 5
3 6
```

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
