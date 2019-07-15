---
title: Lecture 07
date: 2019-07-02 00:00:00 Z
description: Lecture 07
card_title: Lecture 07
card_teaser: Application & Tips. Learning rate, data preprocessing, overfitting & Learning and test data sets
card_position: 8
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-07
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

#Lecture 07 - Application & Tips: Learning rate, data preprocessing, overfitting & Learning and test data sets

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-07-15

### Information of the lecture
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=1jPjVoDV_uo&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=KVv1nMSlPzY&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec7.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=oSJfejG2C3w&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=ktd5yrki_KA&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab7.pdf?raw=true)

### Lecture_1
### Application & Tips: Learning rate, data preprocessing, overfitting
+ Gradient descent의 Learning rate $\alpha$
  + Large learning rate: Overshooting
    + 경사면을 내려가는 step이 커짐
    + 2차원 곡선의 minimum으로 수렴하는 것이 아닌 바깥으로 발산할 수 있음
  + Small learning rate: Takes too long, stops at local minimum
    + 매우 천천히 수렴
    + Minimum이 아닌 구간에서 알고리즘이 종료
  + Learning rate을 선정하는 것에는 특별한 답이 없으며, 여러번 시도해보아야 함
    + Cost function을 확인하며 수정
+ Data (X) preprocessing for gradient descent
  + Weight이 두 개 있는 경우를 예시로 들어 설명
  + $\left( x_1, x_2 \right) = \left(1, 9000 \right)$와 같이 두 입력의 차이가 큰 경우
    + Gradient descent가 발산할 수 있음
    + 해결 방법
      + Zero-centered data: 데이터의 중심을 0으로 맞춰주는 방법
      + Normalized data: 데이터들을 normalization
        + Standardization: $x_j' = \frac{x_j - \mu_j}{\sigma_j}$
        + Python
        ```
        X_std[:,0] = (X[:,0] - X[:,0].mean()) / X[:,0].std()  // easy way
        ```
+ Overfitting
  + 데이터에 과적합한 모델이 생성되는 경우
  + 해결 방법
    + 학습 데이터를 늘리는 방법
    + Feature의 수를 줄이는 방법
    + Regularization (일반화)
      + Weight의 크기를 줄이도록 유도
      + Cost function에 Regularization term 추가 (일반적으로 $\lambda \sum W^2$ 을 사용)
        + $\lambda$ : Regularization strength
      + Tensorflow
      ```
      l2reg = 0.001 * tf.reduce_sum(tf.square(W)) // Regularization strength: 0.001
      ```

<br>

### Lecture_2
### Application & Tips: Learning and test data sets
+ Performance evaluation: is this good?
  + 학습된 모델의 성능을 측정하는 방법
  + 전체 데이터로 학습 후, 같은 데이터로 테스트를 수행하는 것은 좋은 방법이 아님
    + 따라서, 가지고 있는 데이터를 7 : 3 = Training set : Test set 으로 나눔
      + Training set 으로 학습 후 Test set 으로 확인
+ Training, validation and test sets
  + Training set 을 Training set 과 Validation set 으로 나눔
  + Training set 은 학습에 사용하고, Validation set 으로 파라미터 $\alpha, \lambda$를 튜닝
  + Test set 으로 테스트
+ 데이터셋이 매우 많아, 한 번에 학습시키기 어려운 경우
  + Online learning 사용
    + e.g., 100 만 개의 데이터가 있을 때, 10 만 개씩 나누어 순차적으로 학습
    + 새로운 학습 데이터가 추가되어도 이전의 데이터를 다시 학습할 필요 없음

<br>

### Tensorflow_1
#### Learning rate, Evaluation
+ Tensorflow 를 사용하여 Training set 과 Test set 을 나누는 방법에 대해 설명
  + 학습에 사용되지 않은 데이터로 테스트를 수행하여야 함
+ Learning rate: NaN! $\rightarrow$ Learning rate 을 정하는 방법
  + Overshooting 과 Performance 관리
  + Large learning rate 으로 인한 Overshooting 의 경우 $\infty$와 nan 으로 출력됨
    + 학습 실패
  + Small learning rate 으로 인한 cost 불변 예시를 제시
+ Non-normalized inputs
  + Normalization 이 되지 않은 경우, 특정 큰 값에 의해 Gradient descent 가 발산할 수 있음
    + 이 경우에도 Tensorflow 는 nan 으로 출력
  + 해결을 위해 다음과 같은 방법을 사용
    + 각 Feature 마다, 가장 작은 값과 큰 값을 0과 1로 두어 normalization
    ```
    xy = MinMaxScaler(xy)
    ```

<br>

### Tensorflow_2
#### Meet MNIST Dataset
+ 미국의 우체국에서 ZIP code 를 식별하기 위해 만들어진 데이터셋
  + 각 데이터는 28 * 28 * 1 이미지 $\rightarrow$ 784 features
+ Tensorflow 에서 MNIST 데이터를 로드하는 방법에 대한 설명
```
from tensorflow.examples.tutorials.mnist import input_data
mnist = input_data.read_data_sets("MNIST_data/", one_hot=True)
...
batch_xs, batch_ys = mnist.train.next_batch(100)
...
print("Accuracy: ", accuracy.eval(session=sess, feed_dict={X: mnist.test.images, Y: mnist.test.labels}))
```
+ Training epoch/batch
  + 학습 데이터가 큰 경우, 조금씩 batch_size로 나누어 학습
    + one epoch: 전체 데이터셋을 한 번 학습시키는 것
    + batch_size: 전체 데이터 중, 한 번에 몇 개씩 학습할 것인가
    + e.g., 1,000 training examples, batch size is 500, then it will take 2 iterations to complete 1 epoch.

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
