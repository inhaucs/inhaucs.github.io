---
title: "Session 4. Signal Processing and Machine Learning with Differential Privacy"
date: 2019-04-18 00:00:00 Z
description: (blank)
card_title: Session 4
card_teaser: "Signal Processing and Machine Learning with Differential Privacy"
card_position: 4
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [SPM, 2013, SPM2013, Signal Processing, Machine Learning, Differential Privacy]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-22

## Information of the paper
+ Authors: Anand D. Sarwate (Toyota Technological Institute); Kamalika Chaudhuri (University of California)
+ Conference name: IEEE Signal Processing Magazine
+ Published date: 2013-08-19
+ [Paper file](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6582713)

## Abstract
Private companies, government entities, and institutions such as hospitals routinely gather vast amounts of digitized personal information about the individuals who are their customers, clients, or patients. Much of this information is private or sensitive, and a key technological challenge for the future is how to design systems and processing techniques for drawing inferences from this large-scale data while maintaining the privacy and security of the data and individual identities. Individuals are often willing to share data, especially for purposes such as public health, but they expect that their identity or the fact of their participation will not be disclosed. In recent years, there have been a number of privacy models and privacy-preserving data analysis algorithms to answer these challenges. In this article, we will describe the progress made on differentially private machine learning and signal processing.

## Summary (Korean)
+ 제목에 신호 처리와 기계 학습 차등정보 보호가 있으나, 전체적인 내용은 continuous data에 대한 차등정보 보호 방법들을 연구한 논문들을 Survey한 성향이 강한 논문.
+ *신호 처리*에 대해서는 continuous data에 대해서 설명할 때, 대표적으로 신호 처리가 있다라고 기술하는 정도임.

## Details
+ DP에서 완벽하게 안전한 알고리즘은 아무것도 주지 못함.
+ DP 사용 시에 privacy guarantee epsilon, utility(유용성), 그리고 sample size n 사이에는 tradeoff 가 있음.
  + 이러한 tradeoff는 데이터들의 특성에 따라 다름(e.g., dimension, range, sparsity).
+ Motivation : Discrete data에 대한 DP 연구는 많은데, Continuous data에 대한 연구는 많이 진행되지 않음.
+ DP가 왜 중요하냐 : 그것은 다른 ML들이 취약한 공격에 강하기 때문 [GKS08]
+ DP 정의가 있긴한데 [[DMN+06]]를 보든가 해야지. 정확히 이해되지 않음. epsilon은 작을 수록 좋음.
+ epsilon-DP도 있고, (epsilon, delta)-DP도 있는데 epsilon과 delta 둘 다 작을 수록 프라이버시가 더 보장됨[DMN+06, WZ10]. 또한 (epsilon, delta)-DP는 delta=0일 때, epsilon-DP로 reduction되고, epsilon-DP보다 더 약한 프라이버시를 보장함(그럼 왜 사용함?-설명 無).
+ (epsilon, delta)-DP의 여러 변형으로 (1, epsilon, delta)-indistinguishability [7]이나 delta-probabilistic privacy[32] 등이 있음.
+ DP의 중요한 특징 두 가지
  + epsilon-DP를 사용하여 출력된 결과를 사용하여 다른 작업을 수행하여도 epsilon-DP가 유지됨(Chain rule?)
  + 만약 같은 데이터에 대하여 epsilon1과 epsilon2에 대하여 프라이버시를 보장하는 알고리즘의 출력을 동시에 사용하는 경우 안전성은 epsilon1 + epsilon2가 됨.

## Generic Methods for Differential Privacy
+ Input perturbation : Input에 임의의 노이즈를 추가하여 학습하는 방법
+ Output perturbation : Output에 임의의 노이즈를 추가하여 출력하는 방법
+ Exponential mechanism : 이 부분은 정확히 모르겠으나 Mean Squared Error와 같은 최적화 알고리즘에 노이즈를 추가하여 계산하는 방법
+ Objective perturbation : 학습 시에 사용되는 Objective function에 노이즈를 추가하여 계산하는 방법
+ Exponential mechanism과 Objective perturbation의 차이?
+ 각 방법에 더해지는 노이즈는 특정 밀도를 따름.


## Signal processing and machine learning with privacy
+ [14, 15, 46, 47] : Classification
+ [16, 45] : Regression
+ [17, 37, 40, 48] : Principal components analysis (PCA)
+ [33] : Boosting
+ [49] : Online learning
  + Logistic regression with continous value (논문 식 참조 필요, example임)
  + [40, 17, 35] : PCA + DP
  + Time-series data + DP
    + [57] : Fourier + HE
    + [13] : Kalman filter + Laplace noise -> 이 논문은 discrete Fourier transform을 개량하는데 도움을 줌 [57].
    + [11, 12] : Signal processing + DP, Input pert. vs. Output pert. -> Input pert.가 더 성능이 좋음.

## Practical issues and limitations
+ 여기서도 가정이 너무 심함. e.g., Discrete data, finite hypothesis sets, bounded range[24, 58].
+ epsilon과 delta의 초기 설정 문제 -> 이와 관련된 합의가 제안되긴 했음. [GKS08](초기 delta 설정 관련 논문)

## Future challenges
+ DP와 관련된 다른 논문들도 많은데 본 논문에서 소개하는 것은 너무 적음.
+ Challenge 1 : Signal을 수집하는 순간과 학습에 사용되기 전 어느 시점에서 Perturbation이 적용되어야 하는가에 대한 문제
+ Challenge 2 : 이미지와 같이 차원이 매우 높은 데이터에 대한 경우에 대한 연구 부족 (문제?)
+ Challenge 3 : 암호학적 접근과 관련된 연구들은 많으나, DP 관련 연구는 아직 초기임.(2013 논문이라 현재까지도 이게 Challenge가 될지는 모르겠음.)

## References
+ [[FWC+10]] : Survey paper of privacy-preserving machine learning (PPML)
+ [[DMN+06]] : Initial paper of differential privacy
+ [5-7] : Variants of differential privacy
+ [8] : Survey paper of differential privacy
+ [11-13] : Differential privacy for signal processing
+ [14-16] : Differential privacy for classification
+ [17, 18] : Differential privacy for dimensionality reduction
+ [19] : Differential privacy for auction design

[FWC+10]: <https://www.cs.sfu.ca/~wangk/pub/FWCY10csur.pdf> "B. C. M. Fung, K. Wang, R. Chen, P. S. Yu, “Privacy-preserving data publishing: A survey of recent developments”, ACM Comput. Surv., vol. 42, no. 4, pp. 14:1-14:53, June 2010."
[DMN+06]: <http://people.csail.mit.edu/asmith/PS/sensitivity-tcc-final.pdf> " C. Dwork, F. McSherry, K. Nissim, and A. Smith. (2006, Mar. 4–7). Theory of Cryptography (Lecture Notes in Computer Science Series, vol. 3876) [Online]. Available: http://dx.doi.org/10.1007/11681878_14"
[[GKS08]]: <http://www.cse.psu.edu/~ads22/privacy598/papers/gks08.pdf> "S. R. Ganta, S. P. Kasiviswanathan, and A. Smith. Composition attacks and auxiliary information in data privacy. presented at the 14th ACM SIGKDD Int. Conf. Knowledge Discovery and Data Mining (KDD ’08) [Online]. Available: http://dx.doi.org/10.1145/1401890.1401926"
[[WZ10]]: <https://amstat.tandfonline.com/doi/pdf/10.1198/jasa.2009.tm08651?needAccess=true> "L. Wasserman and S. Zhou. (2010). A statistical framework for differential privacy. J. Amer. Stat. Assoc. [Online]. 105(489), pp. 375–389. Available: http://dx.doi.org/10.1198/jasa.2009.tm08651"

## Point to note
+ Five privacy threats in ML: Private Data in the Clear, Reconstruction Attacks, Model Inversion Attacks, Membership Inference Attacks, and De-Anonymization
+ Privacy-preserving machine learning methodologies
  + Cryptographic Approaches: Homomorphic Encryption, Garbled Circuits, and Secure Processors
  + Perturbation Approaches: Differential Privacy, Local DP, and Dimensionality Reduction

## Discussion
+ SUPER HAPPY


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
