---
title: Lecture 04
date: 2019-07-02 00:00:00 Z
description: Lecture 04
card_title: Lecture 04
card_teaser: Multi-variable linear regression
card_position: 5
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-04
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

#Lecture 04 - Multi-variable linear regression

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-04

### Information of the lecture
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=kPxpJY6fRkY&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec4.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=fZUV3xjoZSM&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=o2q4QNnoShY&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab4.pdf?raw=true)

### Lecture
### Multi-variable linear regression
+ Linear regression에 필요한 세 가지 (복습)
  + Hypothesis, Cost function, Gradient descent algorithm
+ Multi-variable linear regression: $X=[x_1, x_2, x_3], Y$ 와 같이 여러 변수가 입력되는 경우
  + Hypothesis의 변화
    + $H(x_1,x_2,x_3) = w_1x_1 + w_2x_2 + w_3x_3 + b$
    + 학습해야할 weight이 $w_1, w_2, w_3, b$로 늘어남
  + Cost function의 변화
    + $cost(W,b) = \frac{1}{m} \sum^m_{i=1} (H(x_1^{(i)}, x_2^{(i)}, x_3^{(i)})-y^{(i)})^2$
  + 일반적으로 적용 가능 : $w_1x_1 + \ldots + w_nx_n$
    + 표현의 편의를 위해 Matrix 사용
      + e.g., $\left({\begin{array}{ccc} x_1 & x_2 & x_3 \end{array}}\right)$ $\left(\begin{array}{c} w_1 \\ w_2 \\ w_3 \end{array}\right) = x_1w_1+x_2w_2+x_3w_3$
      + $H(X) =XW$로 표현 가능
      + 행렬 사용시에는 보통 X를 앞쪽에 표기
  + 상기 방법을 그대로 사용하는 경우 Instance가 10,000개일 때, 행렬 연산을 10,000번 수행해야 함
    + 전체를 큰 행렬에 넣고 한 번에 계산할 수 있음
    + e.g., $\left({\begin{array}{ccc} x_{11} & x_{12} & x_{13} \\ x_{21} & x_{22} & x_{23} \end{array}}\right)$ $\left(\begin{array}{c} w_1 \\ w_2 \\ w_3 \end{array}\right) = \left({\begin{array}{ccc} x_{11}w_1 + x_{12}w_2 + x_{13}w_3 \\ x_{21}w_1 + x_{22}w_2 + x_{23}w_3 \end{array}}\right)$
  + WX vs. **XW**
    + Theory에서는 $H(x)=Wx+b$로 표기하지만 실제 구현시에는 $H(X) = XW$로 구현

<br>

### Tensorflow
#### 1) Multi-variable linear regression을 TensorFlow에서 구현하기
+ Hypothesis
  + $H(x_1,x_2,x_3) = w_1x_1 + w_2x_2 + w_3x_3$
+ 이전 강의와 마찬가지로 Hypothesis 정의, cost function, optimize(GradientDescent), 그리고 학습의 순서로 이루어짐
+ 데이터를 코드에 나열하는 대신 행렬을 사용하는 방법 설명
+ Option 중 $shape=[None, 3]$의 의미는 variable이 3개인 instance가 임의의 개수만큼 입력될 수 있음을 의미

#### 2) TensorFlow로 파일에서 데이터 읽어오기
+ numpy의 loadtxt를 사용하여 파일로부터 데이터 읽어오는 방법 설명
+ python array의 slicing 및 indexing 기능을 유용하게 사용하여 데이터를 잘 다룰 수 있음
+ 파일이 너무 커서 메모리에 다 올리지 못 하는 경우
  + TF의 Queue Runners 사용 (3 steps)
    1) Input file name 나열
        + filename_queue = tf.train.string_input_producer([fil1, fil2, ...], shuffle=T/F, name='filename_queue')
    2) File들을 읽어올 Reader 정의
        + Text로 읽고, (key, value)로 읽는 경우
          + reader = tf.TextLineReader()
          + key, value = reader.read(filename_queue)
    3) 2)에서 읽어온 value 값을 어떻게 파싱할 것인지 정의 (decode)
        + xy = tf.decode_csv(value, record_defaults=record_defaults)
  + 상기 절차를 통해 queue에 들어온 데이터들은 tf.train.batch 함수를 통해 배치 연산 가능
+ 데이터의 구조에 따라 shape option을 신경써주어야 함
+ 데이터를 임의의 순서로 진행하고 싶은 경우 shuffle_batch 함수 사용 가능

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
