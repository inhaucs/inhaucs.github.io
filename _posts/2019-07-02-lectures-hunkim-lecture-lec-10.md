---
title: Lecture 10. Neural Network 2. ReLU and 초기값 정하기 (2006/2007 breakthrough)
date: 2019-07-02 00:00:00 Z
description: Lecture 10
card_title: Lecture 10
card_teaser: Neural Network 2. ReLU and 초기값 정하기 (2006/2007 breakthrough)
card_position: 11
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-10
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-18

### Information of the lecture
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=GYecDQQwTdI&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=oZyvmtqLmLo&feature=youtu.be), [Youtube(Lecture_3)](https://www.youtube.com/watch?v=573EZkzfnZ0&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec9.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=oFGHOsAYiz0&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=lmrWZPFYjHM&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab9.pdf?raw=true)

### Lecture_1
### XOR 문제 딥러닝으로 풀기
+ Neural Networks 로 XOR 을 해결할 수 있는가
  + 하나의 Unit 으로는 XOR 을 풀 수 없다고 수학적으로 증명됨
  + 그러나 여러 개의 Unit 으로 해결 가능 $\rightarrow$ 3 개의 logistic regression 으로 해결
    + 예시를 들어 실제 해결됨을 보임
      + 두 input layer 의 $\left( W, b \right)$ : $$W_1 = \begin{bmatrix} 5 \\ 5 \end{bmatrix} $$, $b_1=-8$ and $$ W_2 = \begin{bmatrix} -7 \\ -7 \end{bmatrix} $$, $b_2=3$
        + 하나의 네트워크로 결합 가능 : $$ W_1 = \begin{bmatrix} 5 & -7 \\ 5 & -7 \end{bmatrix} $$, $$ B_1= \begin{bmatrix} -8 & 3 \end{bmatrix} $$
      + 상기 두 input layer 의 출력을 입력으로 받는 뉴런의 $\left( W, b \right)$ : $$ W_3 = \begin{bmatrix} -11 \\ -11 \end{bmatrix} $$, $b_3=6$
+ Neural networks
  + 상기 결합된 $\left( W_1, B_1 \right)$ 를 사용하여 최종 값 $\bar{Y}$ 는 다음의 수식으로 표현 가능
    + $K(X) = sigmoid(XW_1 + B_1)$
    + $\bar{Y} = H(X) = sigmoid(K(X)W_2 + b_2)$
  + $W_1, W_2, B_1, b_2$ 를 학습하는 방법에 대해 Lecture_2 에서 설명

<br>

### Lecture_2
### 딥러닝의 기본 개념: 딥 네트워크 학습 시키기 (backpropagation)
+ Back propagation (chain rule)
  + $f = wx+b$, $g=wx$, $\rightarrow$ $f=g+b$ 일 때, 우리가 구하고 싶은 것은 각 $w, x, b$ 가 결과 f에 미치는 영향
    + 즉 $\frac{\partial f}{\partial w}, \frac{\partial f}{\partial x}, \frac{\partial f}{\partial b}$
  + Chain rule
    + $\frac{\partial f}{\partial x} = \frac{\partial f}{\partial g} \times \frac{\partial g}{\partial x}$
  + 두 스텝으로 진행
    + Forward
      + 실제 값을 대입하여 정방향 진행 (e.g., $w=-2, x=5, b=3$)
    + Backward
      + 편미분과 chain rule 을 통해 $\frac{\partial f}{\partial w}=5, \frac{\partial f}{\partial x}=-2, \frac{\partial f}{\partial b}=1$ 계산
        + 상기 편미분 값은 입력값과 출력값의 비례 관계를 뜻함, 예를 들어 $w$가 1 증가하는 경우 출력값은 5 증가
+ Sigmoid 의 미분?
  + Sigmoid: $g(z) = \frac{1}{1+e^{-z}}$
    + Sigmoid 식은 $z \rightarrow \times (-1) \rightarrow exp \rightarrow +1 \rightarrow \frac{1}{x} \rightarrow g(z)$ 이므로, 이 또한 chain rule 을 통해 $g'(z)$ 연산 가능
+ Tensorflow 는 tensor 의 backpropagation 을 자동으로 수행 $\rightarrow$ 사용의 편의

<br>

### Tensorflow_1
#### NN for XOR
+ 기본적인 XOR 문제 해결
  + Input and Output
  ```
  x_data = np.array([[0,0], [0,1], [1,0], [1,1]], dtype=np.float32)
  y_data = np.array([[0], [1], [1], [0]], dtype=np.float32)
  ```
  + 결과 값이 0 또는 1 이기 때문에 (binary) 복잡한 softmax 를 사용하지 않고 logistic regression 을 사용
  + Tensor 하나에 대해서 학습을 수행하여도 Accuracy=0.5 $\rightarrow$ Tensor 하나로는 불가능
  + 첫 번째 레이어의 weight 을 $2 \times 2$ 행렬로 수정 후, 두 번째 레이어 추가 $\rightarrow$ Accuracy=1.0
+ Wide NN for XOR
  + 상기 방법에서는 Tensor 가 하나씩인 두 개의 레이어로 XOR 문제 해결
  + Wide NN 으로 해결해보는 방법 (좋은 방법은 아니지만 예시를 보여주기 위함)
    + 첫 번째 레이어의 출력을 2 $\rightarrow$ 10 로 증가시켜 학습 시도
      + 즉 weight 인 $(W,b)$ 를 2개에서 10개로 늘림
      + 학습 결과 성능이 더 향상됨
+ Deep NN for XOR
  + Wide & Deep example 제시
    + $\left[ 2, 10 \right]$ 의  weight 을 가지는 3개의 레이어와 결과를 출력하는 레이어, 총 4개의 레이어로 구성된 모델 학습
    + 역시 학습 결과 성능이 더 향상됨

<br>

### Tensorflow_2
#### Tensorboard for XOR NN
+ Tensorflow 로 작성한 graph 를 구상화
  + Old fashion: print, print, print
  + 5 개의 단계를 통해 사용 가능
  ```
  // 1. From TF graph, decide which tensors you want to log
  w2_hist = tf.summary.histogram("weights2", W2)
  cost_summ = tf.summary.scalar("cost", cost)
  // 2. Merge all summaries
  summary = tf.summary.merge_all()
  // 3. Create writer and add graph
  # Create summary writer
  writer = tf.summary.FileWriter('./logs')
  writer.add_graph(sess.graph)
  // 4. Run summary merge and add_summary
  s, _ = sess.run([summary, optimizer], feed_dict=feed_dict)
  writer.add_summary(s, global_step=global_step)
  // 5. Launch TensorBoard (in Terminal)
  tensorboard --logdir=./logs
  ```
  + Scalar, Histogram 등의 구상화 가능
  + 이 후 내용 SKIP

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
