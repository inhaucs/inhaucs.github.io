---
title: Session 2. Turning Your Weakness Into a Strength. Watermarking Deep Neural Networks by Backdooring
date: 2019-07-15 00:00:00 Z
description: Turning Your Weakness Into a Strength. Watermarking Deep Neural Networks by Backdooring
card_title: Session 2
card_teaser: Turning Your Weakness Into a Strength. Watermarking Deep Neural Networks by Backdooring
card_position: 2
icon: fa-server
categories: [seminars,07-18-2019-morning-seminar,presentation]
tags: [USENIX, 2018, USENIX2019, DNN, Wartermark, Backdoor, Commitment, Authentication]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-july-18-2019
permalink: /:categories/:slug.html
use_math: true
---
<!-- []: <> "" -->

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-07-18

## [Turning Your Weakness Into a Strength: Watermarking Deep Neural Networks by Backdooring](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-jh-july-18-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/adi)

- Authors: Yossi Adi and Carsten Baum (Bar Ilan University); Moustapha Cisse (Google Inc); Benny Pinkas and Joseph Keshet (Bar Ilan University)
- **Conference** name: 27th Usenix Security Symposium
- Published date: 2018-08-17
- [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-adi.pdf)

### Abstract

Deep Neural Networks have recently gained lots of success after enabling several breakthroughs in notoriously challenging problems. Training these networks is computationally expensive and requires vast amounts of training data. Selling such pre-trained models can, therefore, be a lucrative business model. Unfortunately, once the models are sold they can be easily copied and redistributed. To avoid this, a tracking mechanism to identify models as the intellectual property of a particular vendor is necessary. In this work, we present an approach for watermarking Deep Neural Networks in a black-box way. Our scheme works for general classification tasks and can easily be combined with current learning algorithms. We show experimentally that such a watermark has no noticeable impact on the primary task that the model is designed for and evaluate the robustness of our proposal against a multitude of practical attacks. Moreover, we provide a theoretical analysis, relating our approach to previous work on backdooring.

------

## Summary(Korean)

+ Backdooring (adversarial example)을 이용한 DNN 워터마킹 기법을 제안한 논문으로, hyper-parameter 레벨이 아닌, 학습된 parameter 레벨의 보안 이슈를 다룬 논문이다.
+ 이를 위해 **BadNet**이라는 사전 연구를 먼저 소개한다. (19/07/18)



## Previous Research

+ Authors: Tianyu Gu, Brendan Dolan-Gavitt and Siddharth Garg (New York University)
+ Title: **BadNets: Identifying Vulnerabilities in the Machine Learning Model Supply Chain**
+ [Paper Link](https://arxiv.org/abs/1708.06733)

### Abstract of the previous research
Deep learning-based techniques have achieved state-of-the-art performance on a wide variety of recognition and classification tasks. However, these networks are typically computationally expensive to train, requiring weeks of computation on many GPUs; as a result, many users outsource the training procedure to the cloud or rely on pre-trained models that are then fine-tuned for a specific task. In this paper we show that outsourced training introduces new security risks: an adversary can create a maliciously trained network (a backdoored neural network, or a \emph{BadNet}) that has state-of-the-art performance on the user's training and validation samples, but behaves badly on specific attacker-chosen inputs. We first explore the properties of BadNets in a toy example, by creating a backdoored handwritten digit classifier. Next, we demonstrate backdoors in a more realistic scenario by creating a U.S. street sign classifier that identifies stop signs as speed limits when a special sticker is added to the stop sign; we then show in addition that the backdoor in our US street sign detector can persist even if the network is later retrained for another task and cause a drop in accuracy of {25}\% on average when the backdoor trigger is present. These results demonstrate that backdoors in neural networks are both powerful and---because the behavior of neural networks is difficult to explicate---stealthy. This work provides motivation for further research into techniques for verifying and inspecting neural networks, just as we have developed tools for verifying and debugging software.

#### Introduction

#### Threat model
+ **Outsourced Training Attack**
   + 공격자는 validation set의 classification accuracy를 줄여서는 안된다. 그렇지 않다면 사용자는 해당 모델을 즉시 거부할 수 있다. 이 때, 공격자는 실제로 사용자의 validation dataset에 접근할 수는 없다.
   + 특정 공격자가 선택한 property인 backdoor trigger가 포함된 입력에 대해서 공격자가 학습시킨 모델은 정직하게 학습된 모델과는 다른 prediction 결과를 출력한다.
   + 이러한 공격자의 목표는 targeted attack과 non-targeted attack을 모두 포함한다.
     + Targeted attack에서 공격자는 backdoor 속성을 만족하는 입력의 네트워츠 출력을 정확하게 명시한다. 예를 들어, 공격자는 backdoor가 있을 때, 서로 다른 두 label을 바꿀 수 있다.
     + Non-targeted attack은 backdoor 입력에 대한 분류 정확도를 줄이는 데 그 목적이 있다. 다시 말해, 이 공격은 backdoor 입력이 잘못 분류되는 한 항상 성공한다.
+ **Transfer Learning Attack**
  + Transfer Learning: 이미 잘 훈련된 모델이 있고, 특히 해당 모델과 유사한 문제를 해겨해야할 시에 사용하는 기법. 이는 러닝 모델을 feature extractor로 사용하여, 해당 특징들을 이용하여 다른 모델을 학습하는 방법.
    + 기존의 만들어진 모델 (pre-trained model)을 사용하기에 새로운 모델 학습 시에 그 속도가 빠르며 성능 (예측 성공률)을 더 높일 수 있다.
    + 다른 말로, 이미 학습된 파라미터를 transfer하여 새로운 model을 학습시키는 방법으로 fine-tuning이라고도 한다.
    + 실제로 많은 모델을 학습할 때, 대부분의 경우 random initialization을 통해 학습을 시작하는 것이 아닌 pre-trained model을 이용한 transfer learning을 수행한다.
  + Outsourced Training Attack과 목표는 유사하다.
    + 새 application domain에 대한 사용자의 validation set에 대한 높은 accuracy를 보장해야한다.

#### Case Study 1: MNIST Digit Recognition Attack

##### Attack Implementation

+ [Baseline MNIST Network](https://arxiv.org/abs/1609.01000): CNN with 2 Convolutional layers x 2 fully connected layer, 99.5% for MNIST digit recognition.
+ 공격 목표 및 전략
  + Figure 1(a) 에 보는 것 과 같이 오른쪽 아래에 밝은 픽셀 패턴이 삽입되면, BadNet (공격자)은 이 digit $i$의 라벨을 $(i+1)\%9$로 학습한다. 그렇지 않은 그림은 정상적으로 학습한다.
  + 학습 데이터셋에 이러한 노이즈를 삽입함으로써 공격을 구현한다.  (backdoor 셋 삽입)

##### Result

+ MNIST에 대한 공격 결과로, BadNet이 생성한 backdoored image가 잘못 라벨링될 확률이 0.56% (절반이 backdoored image 일 때)로 잘못라벨링 되도록하는 것은 성공적이었다.
+ 또한, Clean image의 평균 오류는 기존보다 0.03%만이 낮아질 뿐이었다.

##### Analysis

+ Figure 1(b)의 trained filters를 보면, 빨갛게 표시된 부분이 BadNet의 첫 번째 레이어에서 사용된 필터로 우측 하단의 데이터를 학습하는데 활용한다는 것을 확인할 수 있다.
+ 이러한 dedicated (전용) backdoor filter가 있다는 것은 backdoors가 BadNet의 깊은 layer안에 sparsely coded되었다는 것을 나타낸다. 



{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-18-fig-casestudy1.png" legend="The case study 1." width="75%" %}



#### Case Study 2:  Traffic Sign Detection Attack

+ 이전에 교수님께서 언급하신 적이 있던 내용으로, Case Study 1의 사례를 실제 환경에서 시도한 공격
  + accuracy는 0.7% 떨어지는 수준에서, stop-sign을 speed-limit sign으로 오분류하게 할 확률이 90%였다.



{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-18-fig-casestudy2.png" legend="The case study 2." width="75%" %}



#### Transfer learning attack

##### Attack Implementation

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-18-fig-transfer-learning.png" legend="Illustration of the transfer learning attack setup." width="75%" %}



+ Figure 3은 이 공격의 설정이 나타나있다.
+ 두 모델이 합쳐지는 것은 아니고, 왼쪽이 일반 User에게 배포된 pre-trained model, 오른쪽이 피해자에게 배포된 pre-trained model이다.
+ Transfer learning에서 일반적인 셋팅을 이용한다.
  + CNN의 모든 fully-connected layers는 재학습되지만,
  + convolutional layers는 유지한다. [[decaf]] [[CVPRW14]]
+ Figure 3에 나타나 있는 Clean model을 이용한 결과와 backdoored model을 이용한 결과를 비교할 것이다.
  + Swedish BadNet의 공격은 validation 정확도가 높지만, backdoored image의 정확도가 낮아지는 경우에 성공했다고 한다.

##### Attack Strategy \& Results

+ 공격이 transfer learning으로부터 살아남을 수 있도록, backdoor neurons의 weight $k$ 를 1~100 사이로 증가시킨다.
  + 이 공격은 $ k = 10 $일 때, 가장 효과적이었다고 하며, 그 결과만을 제시한다.
+ 공격 결과
  + Swedish traffic signs BadNet은 accuracy가 72.7%에서 71.3%으로 소폭 떨어졌지만,
  + backdoored traffic image의 정확도는 49% 미만이 되어 23.7% 하락한 것을 확인하였다.
  + 또한 $ k = 30 $으로 설정한 경우에, backdoored traffic image의 정확도는 40%로 훨씬 하락하나,
  + Clean input의 정확도 또한 65.2%로 떨어지는 결과를 얻었다.
+ 즉, backdoor trigger가 transfer learning에서 생존할 수 있다는 결론을 얻을 수 있으며, 특히 영향이 선택적으로 강화될 수 있는 경우에 더욱 가능성이 높다고 본다.



#### Discussion and conclusion

+ Pre-trained model을 사용하는 경향은 비교적 최근에 이루어진 일이며, 이러한 모델의 사용에 관한 security practice가 시간이 지날수록 향상될 것이다.
+ 이 연구는 그러한 목표에 다가가기 위한 첫 연구라 할 수 있다.
+ 간단한 해결책을 제시하는데, 모델에 서명을 넣자는 해결방법이다.



[CVPRW14]: <http://openaccess.thecvf.com/content_cvpr_workshops_2014/W15/papers/Razavian_CNN_Features_Off-the-Shelf_2014_CVPR_paper.pdf> "Cnn features off-the-shelf: An astounding baseline for recognition"
[decaf]: <https://arxiv.org/abs/1310.1531> "“Decaf: A deep convolutional activation feature for generic visual recognition"




## Main explanation

(TBD)

### Points to note
+ 취소가능한 템플릿을 만드는 새로운 방법 제시
  + Bit sampling based LSH 사용
+ 실제 홍채 데이터셋에 대한 실험 및 분석 수행



## Discussion

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}