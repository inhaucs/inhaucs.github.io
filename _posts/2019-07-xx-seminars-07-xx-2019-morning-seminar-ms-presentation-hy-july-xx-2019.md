---
title: Session 1. Generation of Cancelable Iris Templates via Randomized Bit Sampling
date: 2019-07-04 00:00:00 Z
description: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_title: Session 1
card_teaser: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_position: 1
icon: fa-server
categories: [seminars,07-xx-2019-morning-seminar,presentation]
tags: [TIFS, 2019, TIFS2019, Cancelable biometrics, iris, security, locality sensitive hashing]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-july-xx-2019
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-07-xx

## [Generation of Cancelable Iris Templates via Randomized Bit Sampling](https://inhaucs.github.io/seminars/07-xx-2019-morning-seminar/presentation/ms-presentation-hy-july-xx-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8672919)
+ Authors: Debanjan Sadhya (ABV-Indian Institute of Information Technology); Balasubramanian Raman (Indian Institute of Technology Roorkee)
+ **Journal** name: IEEE Transactions on Information Forensics and Security (Volume 14, Issue 11)
+ Published date: 2019-03-22
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8672919)


### Abstract
Iris-based biometric models are widely recognized to be one of the most accurate forms for authenticating individual identities. Features extracted from the captured iris images (known as IrisCodes) conventionally get stored in their native format over a data repository. However, from a security aspect, the stored templates are highly vulnerable to a wide spectrum of adversarial attack forms. The study in this paper addresses this issue by introducing a privacy-preserving and secure biometric scheme based on the notion of locality sensitive hashing (LSH). In this paper, we have generated cancelable IrisCode features, coined as locality sampled code (LSC), which simultaneously provides strong security guarantees and satisfactory system performance. The functionality of our proposed framework pivots around the fact that intra-class IrisCode samples are “close” to each other, due to which they hash to the same location. Alternatively, the inter-class IrisCodes features are comparatively dissimilar and consequently hash to different locations. We have rigorously examined the intrinsic properties of the LSCs by estimating the intra-class and inter-class collision probabilities for two distinct IrisCodes. Furthermore, we have formally analyzed the security guarantees of non-invertibility, revocability, and unlinkability in our model by establishing various bounds on the adversarial success probability. Extensive empirical tests on the CASIAv3 and IITD benchmark iris databases demonstrate the superior performance of our proposed model, for which we have obtained the best EERs of 0.105% and 1.4%, respectively.


## Introduction (Korean)
+ 홍채는 나이에 따른 변화가 없고, false match에 강점이 있다는 장점이 있으며, 이로 인해 인증 시스템에 적합
+ 홍채 이미지로부터 추출된 feature는 주로 ***IrisCode*** 라는 bit string으로 표현됨 [[D16]]
+ [[RU11]]에는 biometric system에 대한 여러 공격이 소개되어 있음
  + Privacy invasion, masquerade attack, replay attack, and identity theft
  + 이에 따라 대응책으로 **Biometric Template Protection (BTP)** 에 대한 연구가 진행됨 -> 원본 데이터 대신 변환된 데이터를 저장하여 대응하는 방법
+ 본 논문에서 소개하는 내용은 BTP의 하나인 Cancelable biometrics 를 적용
  + 원본 데이터에 특정 함수를 사용하여 왜곡하는 방법
    + 변환된 데이터는 쉽게 역연산되지 않아야 함
    + 인식 성능이 좋아야 함
  + 효과적인 cancelable biometrics scheme 은 다음을 만족
    1) Unlinkability: 같은 데이터로 변환된 두 데이터를 구분할 수 없어야 함 -> Countermeasure of cross-matching based attack
    2) Non-invertibility: One-way 변환으로 인한 역연산 불가
    3) Revocability: (폐지 가능성), 처음 등록한 데이터가 탈취당할 경우, 새로운 변환 데이터를 생성할 수 있어야 함
    4) Performance: Baseline 모델에 비해 성능이 많이 떨어지지 않아야 함

[D16]: <https://ieeexplore.ieee.org/abstract/document/7328287> "J. Daugman, “Information theory and the iriscode,” IEEE Trans. Inf. Forensics Security, vol. 11, no. 2, pp. 400–409, Feb. 2016."
[RU11]: <https://jis-eurasipjournals.springeropen.com/articles/10.1186/1687-417X-2011-3> "C. Rathgeb and A. Uhl, “A survey on biometric cryptosystems and cancelable biometrics,” EURASIP J. Inf. Secur., vol. 2011, no. 1, p. 3, Sep. 2011. [Online]. Available: https://link. springer.com/article/10.1186/1687-417X-2011-3"

+ Contributions
  + Randomized bit sampling 을 사용하여 IrisCode에 적용할 Locality-sensitive hashing (LSH) 생성 $\rightarrow$ 이를 Locality Sampled Code (LSC) 라 명명
    + LSC는 modulo threshold를 사용하여 비가역연산(Non-invertible)
  + CASIAv3 and IITD 데이터베이스에 대해 분석


## Related Work



+ IoT & Mobile 기기들이 늘어남에 따라 네트워크 트래픽도 급격히 증가 -> 보안 및 프라이버시 문제 발생
+ 최근의 네트워크 데이터들은 일반적으로 암호화됨
  + 트래픽이 암호화되어 있더라도 분석을 통해 사용자 행위를 식별하는 연구들이 있음 ([[CMS+16]], [[TSC+18]])
    + Hgih entropy stream 을 잘 분석하지 못 하다는 한계 존재
+ 보통은 데이터 보호를 위해 암호화를 사용함
  + 그러나 IoT 기기들은 연산 능력의 부족으로 암호화를 잘 수행하지 못 함
    + ***기존의 기술들은 암호화(Encryption)와 압축(Compression)을 잘 구별하지 못하므로***, 암호화 대신 압축을 많이 사용함
+ 그래서 HEDGE: High Entropy DistinGuishEr 개발
  + 기존의 접근과 달리 모든 네트워크 트래픽을 분석하지 않음
  + 실시간 탐지를 위해 임의의 부분적인 트래픽 사용 (Random Subset)
+ Git: Dataset and Implementation
  + https://github.com/francasino/traffic_analysis
+ 결과 요약
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-comp_summ.png" legend="A comparative summary." width="50%" %}
  + 초록색과 노란 선의 결과는 우리와 달리 추가적인 트래픽 정보를 사용해 분석한 결과임
  + 64 KB 패킷에서는 94.72% 의 분류 성공율을 보임
  + 1 KB 패킷에서도 (노란 선과 초록 선을 제외하면), 기존의 state-of-the-art인 66.9%를 70.6%로 올림 -> 작은 크기의 패킷에서 이 정도의 성능 향상은 큰 향상임을 어필
[CMS+16]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7265055> "M. Conti, L. V. Mancini, R. Spolaor, and N. V. Verde, “Analyzing android encrypted network traffic to identify user actions,” IEEE Trans. Inf. Forensics Security, vol. 11, no. 1, pp. 114–125, Jan. 2016."
[TSC+18]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8006282> "V. F. Taylor, R. Spolaor, M. Conti, and I. Martinovic, “Robust smartphone app identification via encrypted network traffic analysis,” IEEE Trans. Inf. Forensics Security, vol. 13, no. 1, pp. 63–78, Jan. 2018."


## Proposed Approach
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-overview.png" legend="An overview of the proposed approach." width="50%" %}
+ 교환되는 메시지 : 평문, 암호문, 압축문
+ Eve: 메시지 인터셉트 가능
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-step_by_step.png" legend="Step by step of our methodology." width="50%" %}
+ Randomness Tests 에는 Chi square test (2) 와 NIST SP 800-22 (1) 세 가지를 사용
+ 구분하려는 암호화 알고리즘은 AES (128, 192, 256) & Camelia (128, 192, 256) 이며, 압축 알고리즘은 ZIP, RAR, BZIP2, GZIP


## Experiments
+ 상기 Randomness test 들은 파일 크기에 영향을 받으므로, 실험에서 파일 크기도 고려함
+ Dataset
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-dataset.png" legend="Datasets." width="50%" %}
  + 그림, 비디오, 바이너리, 오디오, 텍스트, PDF 에서 같은 수의 파일 사용
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-accuracy.png" legend="Accuracy detection." width="50%" %}
  + Gain Factor? : 회수율(이득률)이라고 하는데, 설명은 없고 적용한다고 되어있음. 실험 결과를 보면 Threshold가 얼마나 엄격하게 적용되는지를 결정하는 인자로 생각됨
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-outcomes.png" legend="Outcomes." width="50%" %}


### Points to note
+ 기계 학습을 사용하지 않고 높은 성능으로 암호화 패킷과 압축된 패킷을 구분하는 방법 제시
+ 구현 코드 제공 : https://github.com/francasino/traffic_analysis



## Discussion


{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
