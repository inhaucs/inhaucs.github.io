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
#### [Youtube(Lecture_1)](https://www.youtube.com/watch?v=cKtg_fpw88c&feature=youtu.be), [Youtube(Lecture_2)](https://www.youtube.com/watch?v=4rC0sWrp3Uw&feature=youtu.be), [Youtube(Lecture_3)](https://www.youtube.com/watch?v=wTxMsp22llc&feature=youtu.be), [Youtube(Lecture_4)](https://www.youtube.com/watch?v=YHsbHjTBx9Q&feature=youtu.be), [Slide(Lecture)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lec10.pdf?raw=true)
#### [Youtube(Tensorflow)](https://www.youtube.com/watch?v=6CCXyfvubvY&feature=youtu.be), [Slide(Tensorflow)](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/heeyong/2019/hunkim-lecture/slide/lab10.pdf?raw=true)

### Lecture_1
#### ReLU: Better non-linearity (Sigmoid 보다 ReLU가 더 좋아)
+ Neural Networks 을 사용해 XOR을 풀었던 Lecture 09 리뷰
  + 각 layer 의 output 을 처리하는 Activation function 이 있음
+ Neural Networks 의 레이어 표기
  + 첫 번째 레이어 : Input Layer
  + 마지막 레이어 : Output Layer
  + 나머지 레이어 : Hidden Layer
+ 9 개의 Hidden Layer 를 사용하여 XOR 를 풀어보려 함
  + Accuracy: 0.5 로 매우 안 좋은 결과가 도출됨
    + Sigmoid 의 경우 출력이 $0 < x < 1$ 이기 때문
    + Sigmoid 를 activation function 으로 사용하는 경우 backpropagation 의 chain rule 을 적용할 때, 레이어를 거칠수록, 입력이 출력에 미치는 영향이 매우 작아짐
      + 즉 output layer 에서 멀리 있는 layer 들은 출력에 영향이 적어짐
      + **Vanishing gradient** : 이 문제로 인하여, NN 에 대한 관심이 다시 적어짐
  + **Vanishing gradient** 문제는 Sigmoid 의 출력이 1 보다 작기 때문
    + 이를 해결하기 위해 **ReLU** 등장
      + **ReLU** : Rectified Linear Unit
      + 0 보다 작은 경우 0으로, 1 보다 큰 경우 $y=x$ 로 출력
  + 본 강의에서는 sigmoid 대신 ReLU 사용을 권장
    ```
    L1 = tf.sigmoid(tf.matmul(X, W1) + b1)
    L2 = tf.nn.relu(tf.matmul(X, W1) + b1)  // max(0,x)
    ```
  + 상기 9 개의 Hidden Layer 를 가지는 NN 에서, Input Layer & Hidden Layer 의 Activation function 을 ReLU 로 수정하고, Output Layer 만 sigmoid function 으로 사용 (0 ~ 1 을 출력하기 위해)
    + Accuracy: 1.0
+ Activation function 의 종류
  + Sigmoid: $\sigma (x) = \frac{1}{1+e^{-x}}$ $(0 < x < 1)$
  + tanh: $tanh(x)$ : Sigmoid 의 단점을 극복하기 위함 $(-1 < x < 1)$
  + ReLU: $\max(0,x)$
  + Leaky ReLU: $\max(0.1x,x)$
  + Maxout: $max(w^T_1 x + b_1 , w^T_2 x + b_2)$
  + ELU: $$f(x) = \begin{cases} x & if x > 0 \\ \alpha(exp(x)-1) & if x \leq 0 \end{cases}$$
  + 여러 Activation function 을 사용하여 CIFAR-10 측정
    + Sigmoid: n/c (실패)
    + tanh: 89.82 (낮은 성능)
    + VLReLU: 93.09
    + ReLU: 92.11
    + Maxout: 93.94

<br>

### Lecture_2
#### Initialize weights in a smart way (Weight 초기화 잘해보자)
+ Vanishing gradient 를 해결하는 두 가지 방법
  + 1) ReLU 등 sigmoid function 대신, 다른 activation function 사용
  + 2) Weights 의 초기값을 잘 설정
    + 같은 학습을 수행해도, Weights 의 초기 값에 따라 cost function 의 변화가 다름
      + e.g., 초기 weights 을 모두 0으로 설정 $\rightarrow$ 학습 실패
    + Hinton et al. (2006) "A Fast Learning Algorithm for Deep Belief Nets"
      + 해결하기 위해 사용한 방법 : Restricted Boatman Machine (RBM) - 지금은 많이 사용하지 않음
      + RBM 을 사용하여 weights 을 초기화시킨 네트워크를 Deep Belief Nets (DBN) 이라 함
      + **RBM**
        + 두 레이어로 이루어진 모델이 있고, 한 레이어의 perceptron 들은 연결되어 있지 않다고 가정
        + Forward 를 통해 첫 번째 레이어에서(입력) 두 번째 레이어로의 weights 설정
        + Backward 를 통해 두 번째 레이어의 값 weights 을 사용하여 첫 번째 레이어의 값(출력)과 비교하여, (입력)과 (출력)이 같아지도록 weights 학습
        + Autoencoder/autodecoder
        + 레이어가 여러 개더라도, 두 개의 레이어만 비교
      + **Fine Tuning** (미세 조정)
        + 이미 가지고 있는 weights (또는 모델) 이 잘 학습되어 있는 경우, 적은 양의 데이터를 사용하여 weights 을 미세하게 조정하는 방법
    + Good news
      + 복잡한 RBM 을 사용하지 않아도 됨
      + 간단한 weights 으로 초기화하여도 괜찮음
        + Xavier initialization: X. Glorot and Y. Bengio, "Understanding the difficulty of training deep feedforward neural networks," in International conference on artificial intelligence and statistics, 2010.
        + He's initialization: K. He, X. Zhang, S. Ren, and J. Sun, "Delving Deep into Rectifiers: Surpassing Human-Level Performance on ImageNet Classification," 2015.
        + Xavier/He initialization
          + 입력과 출력의 개수에 따라 weights 설정 가능
            ```
            # Glorot et al. 2010
            W = np.random.randn(num_in, num_out) / np.sqrt(num_in)
            # He et al. 2015 : ResNet 연구자
            W = np.random.randn(num_in, num_out) / np.sqrt(num_in/2)
            ```
      + 상기 방법 외에도 다양한 초기화 방법이 있음
        + Batch normalization, Layer sequential uniform variance 등

<br>

### Lecture_3
#### NN dropout and model ensemble (Dropout 과 앙상블)
+ Overfitting review
  + Layer 가 많아질수록 overfitting 될 확률이 높아짐
  + 해결법
    + 많은 training data
    + **Regularization**
+ Regularization
  + $L2$-regularization: $\lambda \sum W^2$
  + Neural Nets 에서는 Dropout 이라는 방법 존재
    + Srivastava et al. 2014
    + Layer 의 뉴런 중 몇 개를 zero 로 하여 학습한 후, 모든 뉴런을 사용하여 테스트
      ```
      dropout_rate = tf.placeholder("float")
      _L1 = tf.nn.relu(tf.add(tf.matmul(X, W1), B1))
      L1 = tf.nn.dropout(_L1, dropout_rate)
      ```
      + Dropout 은 학습에서만 수행되고, 실제 테스트 시에는 모든 뉴런을 사용하여 테스트
        ```
        TRAIN:
        sess.run(optimizer, feed_dict={X: batch_xs, Y: atch_ys, dropout_rate: 0.7})

        EVALUATION:
        print "Accuracy:", accuracy.eval({X: mnist.test.images, Y: mnist.test.labels, dropout_rate: 1})
        ```
+ What is Ensemble?
  + 독립적인 neural nets 가 존재하고 각각에 training set 제공 (Training set 은 같을 수도 다를 수도 있음)
  + 이 후, 각 모델에서 출력되는 결과를 종합하여 결과 예측

<br>

### Lecture_4
#### NN LEGO Play (레고처럼 네트워크 모듈을 마음껏 쌓아 보자)
+ Fast forward
  + resNet 에서 제안 (He et al. 2015)
  + 레이어 간의 중간 출력 결과를 몇 개 레이어를 건너 뛰어 입력으로 제공 (또는 특정 연산)
+ Split & merge
  + 어떤 입력 또는 중간 출력 결과에 대해 여러 개의 레이어로 나누어 학습 후, 병합하는 방법
  + Convolutional layer
+ Recurrent network
  + 네트워크를 한 방향(다음 레이어 방향)이 아닌 같은 레이어의 뉴런으로 결과를 전달하도록 구성하는 방법

<br>

### Tensorflow_1
#### NN, ReLu, Xavier, Dropout, and Adam
+ Neural Nets 사용의 팁
+ Lecture 7 에서 softmax for MNIST: **Accuracy (0.9035)**
+ Neural Nets for MNIST: **Accuracy (0.9455)**
  + 3 layers & 1 neuron for each layer
  + Activation function: ReLu
+ Xavier 초기화 방법 적용: **Accuracy (0.9783)**
  + W1 의 초기화 방법에 xavier_initializer() 적용
    + 초기값이 잘 적용되어 1 epoch 의 cost 부터 매우 작음
+ Deep Neural Nets for MNIST: **Accuracy (0.9742)**
  + Wide & Deep Neural Networks 적용
  + 네트워크가 깊어짐에 따라 과적합 발생 (Overfitting)
+ Dropout for MNIST: **Accuracy (0.9804)**
  + 학습시에는, 통상적으로 0.5 ~ 0.7 정도의 dropout 수행
  + 테스트시에는, 1
+ Gradient descent 외의 optimizer 존재
  + Adam Optimizer 소개

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
