---
title: "Session 2. Privacy-Preserving Machine Learning: Threats and Solutions"
date: 2019-04-16 00:00:00 Z
description: (blank)
card_title: Session 2
card_teaser: "Privacy-Preserving Machine Learning: Threats and Solutions"
card_position: 2
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-18

## Information of the paper
+ Authors: Mohammad Al-Rubaie, Iowa State University and J. Morris Chang, University of South Florida
+ Conference name: IEEE Security and Privacy Magazine
+ Published date: 2019-03-29 (Magazine version: 2019-04-11)
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8677282)

## Abstract
For privacy concerns to be addressed adequately in today’s machine-learning (ML) systems, the knowledge gap between the ML and privacy communities must be bridged. This article aims to provide an introduction to the intersection of both fields with special emphasis on the techniques used to protect the data.

## Summary (Korean)
본 논문에서는 기계 학습을 수행하는 동안 데이터 제공자에게 발생할 수 있는 프라이버시 위협과 현재 연구된 해결 방법들 그리고 논문 말미에 앞으로 연구해야하는 방향에 대해 설명하며, 위협과 해결 방법 두 가지에 대한 개요를 소개함.

## Details
+ Machine Learning(ML) Section Skip. (Supervised, Unsupervised, Semisupervised, etc.)
  + ML은 세 가지 요소로 구성됨
    + **Input party** : 데이터 제공자
    + **Computation party** : ML 연산 수행자
    + **Results party** : ML 모델을 사용자
  + 상기 세 요소가 같은 주체에서 구성되는 경우 프라이버시는 고려할 필요가 없으나, 일반적으로 **Computation party**와 **Results party**는 한 주체에 있고 **Input party**만 분리되어 구성됨.
  
+ **Threats**
  + **Private Data in the Clear** : 데이터 제공자가 데이터를 암호화되지 않은 상태로 전달하여 사용하는 경우
  + **Reconstruction Attacks** : ML에 feature vector만 사용하더라도 모델에 feature vector가 남아있는 경우가 있음(e.g., SVM, k-NN). 이 경우 공격자는 feature vector로부터 Raw data 복원이 가능함. [[FJ2011]]에서는 minutiae template으로부터 지문을 재구성하는 공격을 성공하였고, [[AC2016]]에서는 개인의 인증 방식의 특징(gesture, speed, etc.)을 비슷하게 하여 공격한 연구를 진행.
  + **Model Inversion Attacks** : 물론 feature vector가 모델에 포함되지 않는 것도 있음(e.g., ridge regression, NN). 이 때 공격자는 모델에 대한 테스트 결과를 사용하여 모델에 사용된 feature vector와 비슷한 결과를 얻는 것이 목표. 모델에 대한 테스트를 반복 수행하면 특정 클래스에 대한 평균을 얻을 수 있는데, 해당 클래스가 개인에 대한 정보를 포함하고 있는 경우 큰 문제가 됨. 예를 들어 [[FRTJT2015]]에서는 얼굴 인식에서 이를 보였음.
  + **Membership Inference Attacks** : 타겟 모델에 Input을 넣고(Label을 알고 있는 Input) 출력된 결과와 Label을 비교하여 해당 Input이 Training Phase에서 사용된 샘플인지 아닌지 확인하여 공격하는 방법.
  + **De-Anonymization(Re-Identification)** : 데이터 제공시, 개인 식별 정보를 모두 제거하고 전달하면 자연스럽게 보안 문제가 해결될 것이라 생각하고 실제로 많이 사용함. 그러나 알려진 유저들의 정보를 사용하여 누구인지 추론이 가능하므로 궁극적인 해결책이 될 수 없음.
  
  
+ **Privacy-Preserving Machine Learning (PPML)**
  + 주로 암호학적 접근(Cryptographic approaches)과 차등 보호(differentially private data release: DP, Perturbation approaches)가 사용됨
  + 특히 DP는 membership inference attacks을 막는데 효과적
  + **Model inversion attacks**과 **Membership inference attacks**을 방지하기 위해서는 모델의 결과를 제한하는 것이 효과적임
  
  + **Cryptographic Approaches**
    + 암호화된 상태에서 학습 및 테스트를 수행하는 방법
    + *동형 암호(Homomorphic Encryption)* : 암호화된 상태에서 덧셈 및 곱셈 연산이 가능하며, 효율의 측면에서 덧셈은 암호문 상태에서, 곱셈은 평문 상태에서 수행함
    + *가블드 서킷(Garbled Circuits)* : Alice와 Bob이 있을 때, 서로의 데이터를 사용해 어떤 함수 값을 얻고 싶음. 이 때 Alice가 Garbled circuit과 Alice's garbled input을 만들어 Bob에게 보내고, Bob은 Alice로부터 Bob's garbled input를 얻음(Alice에게 프라이버시 유출 없이). 그리고 Garbled circuit, Alice's garbled input, and Bob's garbled input을 이용하여 함수 값을 얻을 수 있음.
    + *보안 프로세서(Secure Processors)* : Intel SGX. [[OSFM2016]]에서 다양한 ML 알고리즘을 Intel SGX에서 수행한 결과 발표.

  + **Perturbation Approaches**
    + 얘기하기에 앞서, 연구하려는 내용은 Cryptographic approaches보다 Perturbation Approaches에 가까움.
    + DP는 membership inference attacks를 막기위해 사용되는데, 임의의 노이즈를 입력 데이터나 특정 알고리즘의 반복문이나 출력 데이터에 추가함으로써 수행됨.
    + Dimensionality Reduction은 데이터를 낮은 차원으로 투영(projection)하여 원본이나 민감한 정보에 대한 추론을 불가능하게 만듦.
    + Differential Privacy(DP) : 더 공부할 필요가 있음. 차등정보 보호라 하며, 개인의 정보가 전체 데이터베이스에 미치는 영향을 줄이는 것으로 예상됨. 즉 원 데이터 베이스 B1과 하나의 레코드 R가 다른 데이터 베이스 B2가 있을 때 B1을 분석할 때와 B2를 분석할 때 유의미한 차이가 없기 때문에, 레코드 R의 정보가 보장된다는 내용임.
    + Local DP(LDP) : LDP에 대한 정의는 없고, Input parties가 학습에 필요한 정보를 충분히 가지고 있지 않는 경우 적용하는 것이라고 기술. 이외 Chrome에서 적용하는 방식(각각의 속성에 대해 DP를 적용하는 것으로 보임).
    + Dimensionality Reduction(DR) : 더 낮은 차원으로 투영하여 원본 데이터 복구를 불가능하게 함. 그럼에도 위험이 남아있기 때문에 DR + DP 기법 또한 연구됨.
    
    
+ **Discussion in the paper**
  + 유연성의 문제 : 상기 기술된 PPML은 특정 ML 알고리즘에만 적용되므로, 포괄적인 PPML 필요(기존에 제안된 것들도 개선되어야 함) -> 여기에는 transformed data release(★)나 LDP가 좋은 접근이 될 수 있음.
  + 확장성의 문제 : 연산량과 통신 코스트 측면에서, PPML을 위해 추가적인 연산과 통신이 부담.
  + 가정의 문제 : PPML 연구들에서 공모하지 않는다는 가정은 증명하기 너무 쉽고, 또 어떤 컴포넌트가 공모하지 않는지를 정확히 해주어야 함(실적용의 문제).
  + 정책에 대해서도 고려해야 함. 클라이언트에게 적용되어야 하는지 회사에게 적용되어야 하는지. 또 적용하고 있는 회사(Google and Apple, LDP)에서 적용하는 방법이 실제로 효과가 있는 것인지 설명되어야 함.  

[FJ2011]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=5432222> "J. Feng and A. K. Jain, “Fingerprint reconstruction: From minutiae to phase,” IEEE Trans. Pattern Anal. Mach. Intell., vol. 33, no. 2, pp. 209–223, 2011."
[AC2016]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7523420> "M. Al-Rubaie and J. M. Chang, “Reconstruction attacks against mobile-based continuous authentication systems in the cloud,” IEEE Trans. Inf. Forensics Security, vol. 11, no. 12, pp. 2648–2663, 2016."
[FRTJT2015] <http://delivery.acm.org/10.1145/2820000/2813677/p1322-fredrikson.pdf?ip=165.246.44.143&id=2813677&acc=ARCHIVE%20SERVICE&key=36491E83F85BB6C1%2E36491E83F85BB6C1%2E4D4702B0C3E38B35%2E4D4702B0C3E38B35&__acm__=1555569871_6821eb35f713b3d6ba84b84c02ff3915> "M. Fredrikson, T. Ristenpart, C. Tech, S. Jha, and R. Thomas, “Model inversion attacks that exploit confidence information and basic countermeasures,” in Proc. 22nd ACM SIGSAC Conf. Computer and Communications Security, 2015, pp. 1322–1333."
[OSFM2016] <https://www.usenix.org/system/files/conference/usenixsecurity16/sec16_paper_ohrimenko.pdf> "O. Ohrimenko et al., “Oblivious multi-party machine learning on trusted processors,” in Proc. 25th USENIX Security Symp., 2016, pp. 619–636."


## Point to note
+ Five privacy threats in ML: Private Data in the Clear, Reconstruction Attacks, Model Inversion Attacks, Membership Inference Attacks, and De-Anonymization
+ Privacy-preserving machine learning methodologies
  + Cryptographic Approaches: Homomorphic Encryption, Garbled Circuits, and Secure Processors
  + Perturbation Approaches: Differential Privacy, Local DP, and Dimensionality Reduction


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
