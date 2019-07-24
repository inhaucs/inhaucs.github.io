---
title: Session 1. A Practical Privacy-Preserving Data Aggregation (3PDA) Scheme for Smart Grid
date: 2019-07-25 00:00:00 Z
description: A Practical Privacy-Preserving Data Aggregation (3PDA) Scheme for Smart Grid
card_title: Session 1
card_teaser: A Practical Privacy-Preserving Data Aggregation (3PDA) Scheme for Smart Grid
card_position: 1
icon: fa-server
categories: [seminars,07-25-2019-morning-seminar,presentation]
tags: [TII, 2019, TII2019, ]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-july-25-2019
permalink: /:categories/:slug.html
use_math: true
---
<!-- []: <> "" -->

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-07-25

## [A Practical Privacy-Preserving Data Aggregation (3PDA) Scheme for Smart Grid](https://inhaucs.github.io/seminars/07-25-2019-morning-seminar/presentation/ms-presentation-hy-july-25-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8302950)
+ Authors: Yining Liu; Wei Guo (Guilin University of Electronic Technology); Chan-I Fan (National Sun Yat-sen University); Liang Chang (Guilin University of Electronic Technology); Chi Cheng (China University of Geosciences)
+ **Journal** name: IEEE Transactions on Industrial Informatics (Volume 15, Issue 3)
+ Published date: 2018-02-27
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8302950)


### Abstract
The real-time electricity consumption data can be used in value-added service such as big data analysis, meanwhile the single user's privacy needs to be protected. How to balance the data utility and the privacy preservation is a vital issue, where the privacy-preserving data aggregation could be a feasible solution. Most of the existing data aggregation schemes rely on a trusted third party (TTP). However, this assumption will have negative impact on reliability, because the system can be easily knocked down by the denial of service attack. In this paper, a practical privacy-preserving data aggregation scheme is proposed without TTP, in which the users with some extent trust construct a virtual aggregation area to mask the single user's data, and meanwhile, the aggregation result almost has no effect for the data utility in large scale applications. The computation cost and communication overhead are reduced in order to promote the practicability. Moreover, the security analysis and the performance evaluation show that the proposed scheme is robust and efficient.


## Introduction (Korean)
+ Physically Unclonable Functions (PUFs)
  + 물리적 복제방지기술
  + 동일한 공정에서 생상된 칩들의 미세구조 차이를 이용해 물리적으로 복제가 불가능한 보안키를 생성하는 기술
+ PUF 개발 이후 다양한 인증 프로토콜은 PUF와 함께 수행되었는데, 여기의 이점은 비밀키를 저장할 필요가 없다는 점
  + 비휘발성 메모리 공격 등이 불가능
+ 문제점: PUF의 출력은 노이즈가 많은데, 이를 제어하기 위해 PUF를 사용한 연산에 제한이 많이 걸려있음
  + 이에 따라, 기계 학습이 가능하게 됨
+ 본 연구에서는, PolyPUF, OB-PUF, RPUF, LHS-PUF, and PUF-FSM 등에 대해 기계 학습 공격 수행


















## Problems to Study
+ **또한 본 연구는 BMI 와 인체 특징과의 상관관계를 연구한 첫 연구**

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-three_problems.png" legend="Three kinds of problems." width="75%" %}

+ 세 가지 문제를 해결하고자 함
  + 1) 두 이미지를 (이전의 이미지와 현재의 이미지 사용) 보고, 체중이 늘었는지, 줄었는지, 같은지 분석 (-1, 0, 1)
  + 2) 두 이미지를 보고, 체중이 얼마나 변했는지 예측
  + 3) 한 이미지를 보고 BMI 또는 체중이 얼마인지 예측

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-framework.png" legend="Three kinds of problems." width="75%" %}

+ 제안하는 방법의 프레임워크
  + 이미지로부터 몸의 윤곽과 관절을 탐지
  + 이미지로부터 인체 특징 계산 (WTR, WHpR, WHdR, HpHdR, and Area)
  + 인체 특징들을 몸무게와 BMI에 매핑하기 위한 통계학적 모델 적용 (학습 모델)


## Feature extraction
+ 몸의 윤곽과 관절 탐지
  + 윤곽 탐지 : Conditional Random Field as Recurrent Neural Networks (CRF-RNN) 사용 [[Z+15]]
  + 관절 탐지 : Convolutional Pose Machine (CPM) 사용 [[WRK+16]]

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-five_features.png" legend="Three kinds of problems." width="75%" %}

+ 인체 특징 계산
  + Waist width to Thigh width Ratio (WTR)
  + Waist width to Hip width Ratio (WHpR)
  + Waist width to Head width Ratio (WHdR)
  + Hip width to Head width Ratio (HpHdR)
  + body Area between waist and hip (Area)
  + 상기 특징들은 머리, 허리, 엉덩이, 그리고 허벅지의 너비 간의 비율


[Z+15]: <https://www.cv-foundation.org/openaccess/content_iccv_2015/html/Zheng_Conditional_Random_Fields_ICCV_2015_paper.html> "S. Zheng et al., “Conditional random fields as recurrent neural networks,” in Proc. IEEE Int. Conf. Comput. Vis. Pattern Recognit., Jun. 2015, pp. 1529–1537."
[WRK+16]: <https://www.cv-foundation.org/openaccess/content_cvpr_2016/html/Wei_Convolutional_Pose_Machines_CVPR_2016_paper.html> "S.-E. Wei, V. Ramakrishna, T. Kanade, and Y. Sheikh, “Convolutional pose machines,” in Proc. IEEE Conf. Comput. Vis. Pattern Recognit., Jun. 2016, pp. 4724–4732."


## Learning the Mapping
+ weight/BMI 분석 : 상기 계산된 다섯 개의 인체 특징들을 BMI 값에 매핑(학습)시키는 과정 (maping function 을 학습)
+ Support Vector Machine (SVM)
  + 1) 두 이미지를 (이전의 이미지와 현재의 이미지 사용) 보고, 체중이 늘었는지, 줄었는지, 같은지 분석 (-1, 0, 1) 하는 문제를 해결하기 위해 Binary classifier 인 (SVM)을 여러개 사용 (Multi-SVMs)
  + 2) 두 이미지를 보고, 체중이 얼마나 변했는지 예측하기 위해 Support Vector Regression (SVR) 사용
+ Gaussian Processing Regression (GPR)
  + 3) 한 이미지를 보고 BMI 또는 체중이 얼마인지 예측하기 위해 Gaussian Processing 을 사용한 회귀 모델 학습
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-GPs.png" legend="Gaussian Processes." width="75%" %}


## Experiments
+ 전체적으로 각 분류에 따른 데이터 수가 고정되지 않아 Skewed model 이 발생할 가능성이 있는 것처럼 보임
  + 특히 Fig. 10.의 결과에서는 BMI Difference Range 에 따른 SVR 과 GPR 의 차이를 $> 15.5$ 의 테스트 데이터가 적기 때문이라고 해명하고 있음 $\rightarrow$ TIFS 에서 이 정도는 허용 가능하다고 생각해야 할 지...

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-confusion_matrix.png" legend="Confusion matrix of weight difference classification results." width="75%" %}

+ 1) 두 이미지를 (이전의 이미지와 현재의 이미지 사용) 보고, 체중이 늘었는지, 줄었는지, 같은지 분석 (-1, 0, 1)
  + Overall Accuracy: 81.3%
  + (0,0)의 경우 (-1,-1)과 (1,1) 보다 정확도가 낮음
    + 0 class 의 경우 테스트에 사용된 데이터가 적고, (-1,0,1) 의 데이터 분포가 고르지 못하기 때문

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-bmi_differences.png" legend="BMI differences using SVR and GPR models." width="75%" %}

+ 2) 두 이미지를 보고, 체중이 얼마나 변했는지 예측
  + 상기 표에서는 SVR 을 사용했을 때보다 GPR 을 사용했을 때 성능이 약간 좋음 (lower MAE and lower Standard deviation)
  + 아래 그래프에서 "$ > 15.5 $" 의 경우, MAE가 큰데, 이 또한 해당 데이터의 부족으로 인한 것으로 기술

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-mapes_3.png" legend="MAPEs of predicted BMI." width="75%" %}

+ 3) 한 이미지를 보고 BMI 또는 체중이 얼마인지 예측
  + 성별별로 SVR 과 GPR 을 사용하였을 때 MAPE 에러율

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-18-fig-comparison.png" legend="Comparison of BMI estimation." width="75%" %}

+ 기존의 BMI 를 예측하는 다른 방법들과의 에러율 비교
  + PIGF[[WG13]] 와 VGG feature [[K+17]] 는 얼굴 이미지로 BMI 를 측정하는 알고리즘
  + 다른 방법들보다 전반적인 에러율이 낮음을 확인할 수 있음

[WG13]: <https://www.sciencedirect.com/science/article/pii/S0262885613000462> "L. Wen and G. Guo, “A computational approach to body mass index prediction from face images,” Image Vis. Comput., vol. 31, no. 5, pp. 392–400, 2013."
[K+17]: <https://arxiv.org/abs/1703.03156> "E. Kocabey et al.. (Mar. 9, 2017). “Face-to-BMI: Using computer vision to infer body mass index on social media.”"


### Points to note
+ 학습 부분에 있어 흥미로운 부분은 없으나, 몸 윤곽이나 관절 등의 특징을 BMI 추측에 사용하는 등의 새로운 발상에 주목할 필요가 있어 보임


## Discussion


{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
