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
+ Internet of Things (IoT) network에 적합한 Intrusion Detection Systems (IDSs)에 대한 overview
+ IoT는 헬스케어, 교통, 스마트 그리드 등 다양한 분야에서 사용됨
+ 그러나 IoT 특성에 따른 자원의 제약이 기존의 암호 메커니즘을 적용하는데 문제가 됨
+ 다행히도 비슷한 네트워크 환경인 Mobile Ad hoc Networks (MANET), Wireless Sensor Networks (WSN), Cyber-Physical Systems (CPS)와 관련된 연구들이도움이 될 수 있음
  + IoT에 적합한 IDS는 거의 개발되지 않았기 때문에, 본 논문에서는 WSNs, MANETs, CPSs에서 사용되는 IDS에 대한 내용 또한 제공
+ 본 논문의 기여는 IoT, 그리고 상기 세 개의 네트워크에서의 IDS를 모두 고려한 연구라는 점

## IoT의 보안
  + IoT 환경은 처리능력과 에너지 자원 제한으로 인해 암호화와 같은 처리 집약적인 작업이 어려움
  + 공개적인 장소에 설치되어 있어 공격자의 물리적인 접근과 외부에서의 접근 용이
  + 또한 매우 다양한 환경에서 다양한 목적으로 사용되기 때문에 포괄적인 해결법을 찾기 어려움
  + 공격 분류
    + 물리적 공격: 노드 교체, 배터리 교체, 재-프로그래밍 등
    + 네트워크 공격
      + Passive attacks
        + e.g., 헬스케어의 측면에서, 네트워크 통신은 그대로 두고 패킷(사용자의 의료 정보 등)을 보는 것
      + Active attacks
        + e.g., 헬스케어의 측면에서, 패킷을 고의로 누락하는 등의 공격

## Intrusion Detection Systems (IDSs)
FIGURE 1
+ 목적: 잠재적으로 문제가 될 수 있는 비정상 동작 탐지
+ 상기 Figure 1와 같은 분류 중 앞서 등장하는 다섯 가지 기준에 대해 설명하고, Implementation Strategy의 경우 장을 새로 만들어 심화 설명
  + Decision Quality
    + 공격을 얼마나 잘 탐지하는 지에 대한 연구
    + [[PAPER17]]을 인용, TP, TN, FP, FN 설명
    + [[PAPER18]]에서 인용
      + IDS should have a "low false positive rate, and high true positive rate"
  + Responses on Attacks
    + IDS의 공격에 대한 반응을 설명
    + 일반적으로 IDS는 모니터링, 탐지, 알람의 세 모듈로 구성됨
    + 또한 IDS는 공격에 대한 반응으로 관리자에 보고하는 것이 일반적임
      + [[PAPER19]]에서 인용, 이와 다른 방법으로는 즉각적으로 공격에 대한 대응책을 수행하는 Intrusion Prevention System (IPS)과 공격의 근원지로 보이는 노드를 차단하는 Intrusion Mitigation System (IMS)이 있으나, 두 방법 모두 공격자에 의해 의도적인 false positive 발생이 가능하다는 문제점이 있기에 일반적인 IDS 대응이 많이 사용됨
  + Attacker Type
    + External Attacker: 네트워크 바깥에서 공격하는 노드
    + Internal Attacker: 네트워크 내부에서 공격하는 노드
  + Type of Attack
    + IoT 네트워크의 특성에 따른 공격
      + Selective forwarding: IoT 장비가 메시지 전송자의 패킷 전송 속도를 감당하지 못하는 경우 중간 노드가 메시지 전송을 관리하는데, 이 중간 노드가 공격당하는 경우 선택적인 메시지 전송이 가능
      + Sinkhole/black hole/packet dropping: IoT 네트워크는 종종 Routing Protocol for Low Power and Lossy networks (RPL)과 같은 즉흥적인 프로토콜을 사용하여 네트워크를 구성하는데, 이 때 거리가 가까운 노드를 선택하는 경향이 있음. 해당 프로토콜을 사용하여 네트워크를 구성할 때, 공격자의 장비가 더 가까운 거리에 있다고 속임으로써 네트워크에 침투
      + Node selfishness: 상기 공격과 반대로 실제로 가까운 노드이지만, 먼 노드라고 기만함으로써, 배터리 등의 이득을 얻는 공격. 이웃 노드들의 자원을 혹사시키며 전체적인 네트워크 성능의 하락을 야기함
      + Version number: 네트워크가 변경될 때, RPL과 같은 프로토콜에 의해 네트워크가 새로운 버전으로 재구성되는데, 이를 위해 상대적으로 노드 간에 상대적으로 큰 재구성 패킷 교환이 수행됨. 공격자는 이 네트워크 재구성을 발생시킴으로써 공격
      + Resource depletion/battery exhaustion: 여러 방법을 사용한 배터리 고갈 공격. e.g., 네트워크에 큰 용량의 무의미한 패킷 주입
    + 일반적인 네트워크 공격
      +
  + Detection Technique









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
