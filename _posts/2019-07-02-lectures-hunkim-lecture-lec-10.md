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
+

<br>

### Lecture_4
#### NN LEGO Play (레고처럼 네트워크 모듈을 마음껏 쌓아 보자)





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
