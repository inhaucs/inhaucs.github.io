---
title: Lecture 12. NN의 꽃 RNN 이야기
date: 2019-07-02 00:00:00 Z
description: Lecture 12
card_title: Lecture 12
card_teaser: NN의 꽃 RNN 이야기
card_position: 13
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-12
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
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=-SHPG_KMUkQ&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm&index=41), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec12.pdf?raw=true)
#### [Youtube(Tensorflow_1)](https://www.youtube.com/watch?v=B5GtZuUvujQ&feature=youtu.be), [Youtube(Tensorflow_2)](https://www.youtube.com/watch?v=39_P23TqUnw&feature=youtu.be), [Youtube(Tensorflow_3)](https://www.youtube.com/watch?v=2R6nfCNNz1U&feature=youtu.be), [Youtube(Tensorflow_4)](https://www.youtube.com/watch?v=vwjt1ZE5-K4&feature=youtu.be), [Youtube(Tensorflow_5)](https://www.youtube.com/watch?v=aArdoSpdMEc&feature=youtu.be), [Youtube(Tensorflow_6)](https://www.youtube.com/watch?v=odMGK7pwTqY&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab12.pdf?raw=true)

### Lecture_1
#### NN의 꽃 RNN 이야기
+ Sequence data를 사용한 학습에 사용
  + e.g., 음성인식, 자연어 등
  + 하나의 단어로는 전체를 이해할 수 없음 (이전의 결과가 이후에 영향을 미침)
+ Recurrent Neural Network (RNN)
  + $h_t = f_W (h_{t-1}, x_t)$
  + 이전의 state $h_{t-1}$를 사용하여 현재 state $h_t$를 계산
  + 가장 기본적인 RNN 모델 (Vanilla RNN)
    + $h_t = tanh(W_{hh}h_{t-1} + W_{xh}x_t)$ : State 계산
    + $y_t = W_{hy}h_t$ : 결과 계산
    + 모든 RNN cell에서 같은 $W_{hh}, W_{xh}, W_{hy}$ 사용
    + $h_{t-1}$의 초기값은 보통 0으로 설정
+ RNN applications
  + Language Modeling, Speech Recognition, Machine Translation, Conversation Modeling/Question Answering, Image/Video Captioning, Image/Music/Dance Generation
+ RNN의 유연성
  + One to one model : Vanilla RNN
  + One to many : Image Captioning (image -> sequence of words)
  + Many to one : Sentiment Classification (sequence of words -> sentiment)
  + Many to many (delay ver.) : Machine Translation (sequence of words -> sequence of words)
  + Many to many : Video classification on frame level
+ 또한 RNN도 depth를 늘려 Multi-Layer RNN으로 사용 가능
+ Training RNNs is challenging
  + Several advanced models
    + Long short Term Memory (LSTM) : 보통 RNN이라 하면 LSTM을 말함
    + GRU by cho et al. 2014
    + 일반적으로 RNN을 사용한다고 하면 상기 두 개의 알고리즘을 사용

<br>

### Tensorflow_1
#### RNN - Basics
+ RNN은 다른 신경망과 달리 한 cell의 출력이 다음 cell의 입력이 됨
  ```
  cell = tf.contrib.rnn.BasicRNNCell(num_units=hidden_size)   // 기본 RNN cell 생성
  cell = tf.contrib.rnn.BasicLSTMCell(num_units=hidden_size)   // LSTM cell 생성
  ...
  outputs, _states = tf.nn.dynamic_rnn(cell, x_data, dtype=tf.float32)
  ```
  + e.g., hello 라는 길이 4의 one-hot encoding으로 표현되는 벡터를 입력으로 hidden_size 2(길이 2의 벡터) 로 출력하는 예시
  + RNN에서 Batching input을 사용하여 학습하는 방법 소개
  + 본 절에서는 학습 이외에 RNN에서 입력과 출력을 다루는 방법에 대해 소개

<br>

### Tensorflow_2
#### RNN - Hi Hello Training
+ RNN으로 'hihello'를 학습하는 방법 소개 (강의 참조)
+ RNN 의 Loss function으로는 sequence_loss function 사용

<br>

### Tensorflow_3
#### RNN with long sequences
+ Sample string에 대해 indexing하는 방법 소개
  ```
  sample = "if you want you"
  idx2char = list(set(sample))  # index -> char
  char2idx = {c: i for i, c in enumerate(idx2char)}   # char -> idx
  sample_idx = [char2idx[c] for c in sample]    # char to index
  x_data = [sample_idx[:-1]]  # X data sample (0 ~ n-1) hello: hell
  y_data = [sample_idx[1:]]   # Y data sample (1 ~ n) hello: ello
  ...
  X_one_hot = tf.one_hot(X, num_classes)  ## one hot: 1 -> 0 1 0 0 0 ...  -> 자동으로 one hot 생성
  ```
+ Hyper parameters
  ```
  dic_size = len(char2idx)          # RNN input size (one hot size)
  rnn_hidden_size = len(char2idx)   # RNN output size
  num_classes = len(char2idx)       # final output size (RNN or softmax, etc.)
  batch_size = 1                    # one sample data, one batch
  sequence_length = len(sample)     # number of LSTM unfolding (unit #)
  ```
+ 문자열 입력 자동화를 통한 실험 결과
+ Really long sentence?
  + Sentence example
    + "if you want to build a ship, don't drum up people together to collect wood and don't assign them tasks and work, but rather teach them to long for the endless immensity of the sea."
    + 상기 문장을 작은 단위로 나누어서 데이터 생성 (sliding window 사용)
      + 0: if you wan -> f you want
      + 1: f you want -> you want
      + 2: you want -> you want t
      + ...
      + 169: of the sea -> f the sea.
  + 학습 데이터가 많으므로 batch_size도 달라질 수 있음 (상기 예시들에선 입력 데이터가 하나이기 때문에 1)
  + 결과는 좋지 않음 -> 다음 강좌에서 다룸
    + Hints: Logit and Depth of RNN

<br>

### Tensorflow_4
#### RNN with long sequences: Stacked RNN + Softmax Layer
+ Sentence
  + "if you want to build a ship, don't drum up people together to collect wood and don't assign them tasks and work, but rather teach them to long for the endless immensity of the sea."
+ 복잡하고 많은 데이터를 다루기에 RNN의 cell이 너무 작기 때문에 제대로 학습되지 않음
  + Wide & Deep RNN 를 위해 Stacked RNN 고려
    ```
    cell = rnn.BasicLSTMCell(hidden_size, state_is_tupe=True)
    cell = rnn.MultiRNNCell([cell] * 2, state_is_tuple=True)  # 상기 선언된 cell 을 몇 개 쌓을 것인지 정해줌(stacked), 본 예시에서는 두 개 쌓음
    ```
  + Softmax (FC) in Deep CNN
    + CNN 구조에서 마지막 step에 Fully-connected layer를 두 개 사용했던 내용 상기
    + 따라서 RNN 결과에 Softmax를 사용해보자
  + 상기 두 방법을 적용하면 이전의 결과보다 훨씬 나은 출력을 얻을 수 있음

<br>

### Tensorflow_5
#### Dynamic RNN
+ Tensorflow의 새로운 기능 중 하나
+ RNN의 강점은 sequence data를 처리할 수 있다는 점
+ 그러나 sequence data의 경우 길이가 다를 수 있음 (Different sequence length)
  + RNN은 가변 길이의 데이터를 입력으로 받을 수 있어야 함
    + 기존에는 패딩으로 처리하려 했으나 loss가 커지는 문제점이 있음
    + 이를 해결하기 위해 Tensorflow에서는 입력의 길이를 명시적으로 제공하는 방법 존재
    + 하기와 같이 사용 가능, sequece_length 이외의 값에 대해서는 0 출력
      ```
      outputs, _states = tf.nn.dynamic_rnn(cell, x_data, sequence_length=[5,3,4], dtype=tf.float32)
      ```

<br>

### Tensorflow_6
#### RNN with time series data (stock)
+ Time series data
  + 시간에 따라 값이 변하는 데이터
+ 주식(stock)을 예시로 들어 설명
  + Many to one LSTM 적용 1-7일간의 가격으로 8일째의 가격 예측
+ 영상 참조



{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
