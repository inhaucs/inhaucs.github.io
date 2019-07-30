---
title: Session 2. Recent Advancements in Intrusion Detection Systems for the Internet of Things
date: 2019-08-01 00:00:00 Z
description: Recent Advancements in Intrusion Detection Systems for the Internet of Things
card_title: Session 2
card_teaser: Recent Advancements in Intrusion Detection Systems for the Internet of Things
card_position: 2
icon: fa-server
categories: [seminars,08-01-2019-morning-seminar,presentation]
tags: [SCN, 2019, SCN2019]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-aug-01-2019
permalink: /:categories/:slug.html
use_math: true
---
<!-- []: <> "" -->

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-08-01

## [Recent Advancements in Intrusion Detection Systems for the Internet of Things](https://inhaucs.github.io/seminars/08-01-2019-morning-seminar/presentation/ms-presentation-hy-aug-01-2019.html)

### Information of the paper [(Link)](https://www.hindawi.com/journals/scn/2019/4301409/abs/)
+ Authors: Zeeshan Ali Khan (Minhaj University); Peter Herrmann (Norwegian University of Science and Technology)
+ **Journal** name: Security and Communication Networks (Volume 2019, Issue )
+ Published date: 2018-07-03
+ [Paper Link](https://www.hindawi.com/journals/scn/2019/4301409/abs/)


### Abstract
Many Internet of Things (IoT) systems run on tiny connected devices that have to deal with severe processor and energy restrictions. Often, the limited processing resources do not allow the use of standard security mechanisms on the nodes, making IoT applications quite vulnerable to different types of attacks. This holds particularly for intrusion detection systems (IDS) that are usually too resource-heavy to be handled by small IoT devices. Thus, many IoT systems are not sufficiently protected against typical network attacks like Denial-of-Service (DoS) and routing attacks. On the other side, IDSs have already been successfully used in adjacent network types like Mobile Ad hoc Networks (MANET), Wireless Sensor Networks (WSN), and Cyber-Physical Systems (CPS) which, in part, face limitations similar to those of IoT applications. Moreover, there is research work ongoing that promises IDSs that may better fit to the limitations of IoT devices. In this article, we will give an overview about IDSs suited for IoT networks. Besides looking on approaches developed particularly for IoT, we introduce also work for the three similar network types mentioned above and discuss if they are also suitable for IoT systems. In addition, we present some suggestions for future research work that could be useful to make IoT networks more secure.


## Introduction (Korean)
+ Smart Grid (SG) 를 위해 Smart Meter (SM) 들은 실시간 사용 정보를 Operation Center (OC) 로 전달, OC 는 이를 처리하여 더 효율적으로 SG 관리
+ 그러나 전력 사용량은 다른 용도를 위해 SG 시스템 외의 용도로 제공될 수 있음
  + 개인의 전력 사용 정보에 대한 프라이버시 침해 위험 존재
  + 프라이버시 문제를 해결하기 위해 "Privacy-preserving data aggregation" 방법들이 제안됨 ([[LHL+17]], [[LXY+18]])
    + 요구사항
      + Aggregation operator 는 한 지역(or 구간)에서 사용한 전력의 합을 알 수 있어야 함
      + Aggregation operator 는 지역(or 구간)에 포함된 개인의 전력 사용량은 알 수 없음
  + 상기 방법 외에도 동형 암호 ([[P99]]), Random number ([[JZC+14]], [[FHL14]], [[HKL16]]), Shamir's secret sharing ([[S79]], [[TGZ13]])
+ 본 논문에서는 Practical Privacy-Preserving Data Aggregation (3PDA) 를 제안 (contribution below)
  + 3PDA 는 Data Collection Unit (DCU) 또는 Trusted Third Party (TTP) 에 의지하지 않음
  + 3DPA 를 가능하게 하는 Virtual Aggregation Area 를 소개
  + 추정 결과가 아닌 정확한 결과를 얻음

[LHL+17]: <https://ieeexplore.ieee.org/abstract/document/7869305> "R. Lu, K. Heung, A. H. Lashkari, and A. A. Ghorbani, “A lightweight privacy-preserving data aggregation scheme for fog computing-enhanced iot,” IEEE Access, vol. 5, pp. 3302–3312, 2017."
[LXY+18]: <https://ieeexplore.ieee.org/abstract/document/7962172> "S. Li, K. Xue, Q. Yang, and P. Hong, “PPMA: privacy-preserving multisubset aggregation in smart grid,” IEEE Trans. Ind. Informat., vol. 14, no. 2, pp. 462–471, Feb. 2018."
[P99]: <https://link.springer.com/chapter/10.1007/3-540-48910-X_16> "P. Paillier, “Public-key cryptosystems based on composite degree residuosity classes,” in International Conference on the Theory and Applications of Cryptographic Techniques. New York, NY, USA: Springer, 1999, pp. 223–238."
[JZC+14]: <https://ieeexplore.ieee.org/abstract/document/6541956> "W. Jia, H. Zhu, Z. Cao, X. Dong, and C. Xiao, “Human-factor-aware privacy-preserving aggregation in smart grid,” IEEE Syst. J., vol. 8, no. 2, pp. 598–607, Jun. 2014."
[FHL14]: <https://ieeexplore.ieee.org/abstract/document/6578183> "C. I. Fan, S. Y. Huang, and Y. L. Lai, “Privacy-enhanced data aggregation scheme against internal attackers in smart grid,” IEEE Trans. Ind. Informat., vol. 10, no. 1, pp. 666–675, Feb. 2014."
[HKL16]: <https://link.springer.com/article/10.1007/s11276-015-0983-3> "D. He, N. Kumar, and J.-H. Lee, “Privacy-preserving data aggregation scheme against internal attackers in smart grids,” Wireless Netw., vol. 22, no. 2, pp. 491–502, 2016."
[S79]: <https://dl.acm.org/citation.cfm?id=359176> "A. Shamir, “How to share a secret,” Commun. ACM, vol. 22, no. 11, pp. 612–613, 1979."
[TGZ13]: <https://link.springer.com/article/10.1007/s11424-013-2131-4> "C. Tang, S. Gao, C. Zhang, “The optimal linear secret sharing scheme for any given access structure,” J. Syst. Sci. Complexity, vol. 26, no. 4, pp. 634–649, 2013."

+ System Model
  + Communication Model

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-25-fig-system_model.png" legend="System model." width="75%" %}

  + Privacy Adversary Model
    + SG 에는 data injection, time synchronization, DoS, and physical threats 등의 위협 존재
    + 안전성 요구사항과 Privacy-preserving 의 목적은 동치가 아님
    + OC 는 honest-but-curious
    + DCU 는 not to be trusted
    + User (or SM) honest-but-curious
    + 즉 최악의 경우에는 OC, DCU, User 모두 공모 가능

+ Preliminaries
  + Lifted EC-ElGamal Cryptosystem
    + 1) - 4) 는 따라가면 당연한 얘기
    + 5) Distributed Decryption
      + 나눠서 복호화 가능

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-25-fig-dist_dec.png" legend="Distributed decryption." width="75%" %}

  + CL* signature Scheme
    + Pairing batch verification algorithm
    + Randomizer 문제 있을 것으로 생각됨 (확인은 추후)

+ Our Scheme

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-25-fig-main_workflow.png" legend="Main Workflows in our scheme." width="75%" %}

  + 다섯 단계로 구성 : System setup, aggregation area creation, ciphertext generation, ciphertext aggregation, and distributed decryption
    + System setup
      + Elliptic curve 연산에 필요한 generator, hash, key-pair 등 생성
    + Aggregation Area Creation
      + $n$ 개의 SM 은 aggregation area (group) 을 만들고, 자신의 아이디 $ID_i$, 공개키 $Y_i$, 그리고 인증서 $Cert_i$ 를 브로드캐스팅하고 다른 SM 들은 확인 후, Group 공개키인 GK 계산 $GK = \sum_{i=1}^n Y_i$
    + Ciphertext Generation
      + 각 SM 은 자신의 메시지 $m_i$ 의 암호문과 서명을 DCU 로 전달
    + Ciphertext Aggregation
      + DCU 는 batch verification 을 사용하여 서명을 확인하고, $n$ SM 으로부터의 암호문 aggregation $\rightarrow (C^a, C^b)$
      + 자신의 서명과 Aggregated data 를 OC 로 전달
    + Distributed Decryption
      + OC 는 앞서 설명한 Distributed Decryption 을 사용하여 모든 SM 에 $C^a$ 를 전달하고, $x_i C^a$ 를 돌려받아 복호화


### Points to note
+ Lifted EC-ElGamal Cryptosystem 의 Homomorphism 을 활용한 Aggregation 방법 제안
  + 실험 결과를 통해 실용적이라고 말하고 있음
  + Homomorphism 을 가지는 Lifted EC-ElGamal Cryptosystem 보다 빠른 알고리즘을 적용한다면 더 실용적인 시스템 설계 가능할 것으로 보임
+ Batch verification 에 문제가 있을 것으로 보임 : Randomizer $\rightarrow$ Comment?


## Discussion


{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
