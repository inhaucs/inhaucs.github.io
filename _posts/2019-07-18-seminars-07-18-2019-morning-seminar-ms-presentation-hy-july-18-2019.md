---
title: Session 1. Generation of Cancelable Iris Templates via Randomized Bit Sampling
date: 2019-07-18 00:00:00 Z
description: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_title: Session 1
card_teaser: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_position: 1
icon: fa-server
categories: [seminars,07-18-2019-morning-seminar,presentation]
tags: [TIFS, 2019, TIFS2019, Body weight analysis, visual analysis of body mass index (BMI), anthropometric features, visual-body-to-BIM dataset]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-july-18-2019
permalink: /:categories/:slug.html
use_math: true
---
<!-- []: <> "" -->

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-07-15

## [Body Weight Analysis From Human Body Images](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-hy-july-18-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8666768)
+ Authors: Min Jiang; Guodong Guo (West Virginia University)
+ **Journal** name: IEEE Transactions on Information Forensics and Security (Volume 14, Issue 10)
+ Published date: 2019-03-13
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8666768)


### Abstract
Human body images encode plenty of useful biometric information, such as pupil color, gender, and weight. Among these, body weight is a good indicator of health conditions. Motivated by recent health science studies, this paper investigates the feasibility of analyzing body weight from two-dimensional (2D) frontal view human body images. The widely used body mass index (BMI) is employed as a measure of body weight. To investigate the problems at different levels of difficulties, three feasibility problems, from easy to hard, are studied. More specifically, a framework is developed for analyzing body weight from human body images. Computation of five anthropometric features is proposed for body weight characterization. Correlation is analyzed between the extracted anthropometric features and the BMI values, which validates the usability of the selected features. A visual-body-to-BMI dataset is collected and cleaned to facilitate the study, which contains 5900 images of 2950 subjects along with the labels corresponding gender, height, and weight. Some interesting results are obtained, demonstrating the feasibility of analyzing body weight from 2D body images. In addition, the proposed method outperforms two state-of-art facial image-based weight analysis approaches in most cases.


## Introduction (Korean)
+ 여러 SNS 와 촬영 장비가 등장함에 따라, 사람들은 자신의 모습을 많이 기록하기 시작함
  + 이론 기록물들은 여러 biometrics 들을 포함 (e.g., 성별, 키 몸무게, 나이 등)
  + 이 중 몸무게와 비만도는 건강 상태를 식별하기 위해 사용 가능
+ 본 논문에서는 인체 이미지로부터 체중과 비만도를 특정짓는 방법 개발
+ Contribution
  + 새로운 데이터셋 생성
    + 2,950 명으로부터, 각각 두 장씩, 5,900 개의 이미지 (body to BMI)
  + 몸 이미지로부터 체중과 BMI 를 분석하는 프레임워크 개발
  + 몸 이미지로부터 몸무게를 분석하기 위한 다섯 가지 인체 특징 (Anthropometric features)를 소개


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
