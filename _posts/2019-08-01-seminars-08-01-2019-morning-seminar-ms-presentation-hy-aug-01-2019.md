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


### Introduction (Korean)
+ Internet of Things (IoT) network에 적합한 Intrusion Detection Systems (IDSs)에 대한 overview
+ IoT는 헬스케어, 교통, 스마트 그리드 등 다양한 분야에서 사용됨
+ 그러나 IoT 특성에 따른 자원의 제약이 기존의 암호 메커니즘을 적용하는데 문제가 됨
+ 다행히도 비슷한 네트워크 환경인 Mobile Ad hoc Networks (MANET), Wireless Sensor Networks (WSN), Cyber-Physical Systems (CPS)와 관련된 연구들이도움이 될 수 있음
  + IoT에 적합한 IDS는 거의 개발되지 않았기 때문에, 본 논문에서는 WSNs, MANETs, CPSs에서 사용되는 IDS에 대한 내용 또한 제공
+ 본 논문의 기여는 IoT, 그리고 상기 세 개의 네트워크에서의 IDS를 모두 고려한 연구라는 점

### IoT의 보안
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

### Intrusion Detection Systems (IDSs)

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-08-01-fig-classification_IDSs.png" legend="System model." width="75%" %}

+ 목적: 잠재적으로 문제가 될 수 있는 비정상 동작 탐지
+ 상기 Figure 1과 같은 분류 중 앞서 등장하는 다섯 가지 기준에 대해 설명하고, Implementation Strategy의 경우 장을 새로 만들어 심화 설명
  + Decision Quality
    + 공격을 얼마나 잘 탐지하는 지에 대한 연구
    + [[PP07]]을 인용, TP, TN, FP, FN 설명
    + [[ZLH03]]에서 인용
      + IDS should have a "low false positive rate, and high true positive rate"
  + Responses on Attacks
    + IDS의 공격에 대한 반응을 설명
    + 일반적으로 IDS는 모니터링, 탐지, 알람의 세 모듈로 구성됨
    + 또한 IDS는 공격에 대한 반응으로 관리자에 보고하는 것이 일반적임
      + [[F05]]에서 인용, 이와 다른 방법으로는 즉각적으로 공격에 대한 대응책을 수행하는 Intrusion Prevention System (IPS)과 공격의 근원지로 보이는 노드를 차단하는 Intrusion Mitigation System (IMS)이 있으나, 두 방법 모두 공격자에 의해 의도적인 false positive 발생이 가능하다는 문제점이 있기에 일반적인 IDS 대응이 많이 사용됨
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
      + DoS, DDoS, Jamming, Unauthorized access (허가 없이 접근), Remote-to-Local (공격자가 외부에서 IoT 네트워크로 패킷을 보낼 수 있는 경우), User-to-Root (normal user로 접근하여 root까지 접근하는 공격), Probing (탐색 공격), Spoofing, Packet repetition, packet delay, Wormhole (공격자가 네트워크 내의 두 개 이상의 노드를 네트워크와 별개로 연결하여 라우터 교란), Packet alteration/bad data injection (패킷을 변경하거나 악의적인 데이터 주입), Periodic route error (라우팅 에러를 이웃 노드들에 전파하여 새 경로를 찾도록 유도), Hello flooding (공격자가 네트워크에 새롭게 추가되려는 노드로 위장하여 hello(join) 패킷 대량 전송), Routing misdirection and disruption (라우터 노드가 잘못된 경로를 알려주는 공격 -> Packet delay), Node capture (다른 공격을 돕도록 노드 획득), Eavesdropping (도청: 메시지 획득)
  + Detection Technique
    + Signature-Based IDSs
      + Rule-based IDSs 라고도 함
      + 실제 네트워크 활동 감시, 가지고 있는 signature와 같은 경우 경고
      + False positive는 적지만, 새로운 공격에 취약 $\rightarrow$ 따라서 높은 false negative (공격이 발생했으나 탐지 못 하는 경우)
      + [[SMR+05]]에서는 다양한 규칙 연구
        + Interval, Retransmission, Integrity, Delay, Repetition, Radio transmission range, Jamming rule, Version number check
    + Anomaly-Based IDSs
      + 비정상 동작 탐지 $\rightarrow$ 알려지지 않은 공격 탐지 가능
      + 높은 false positive $\rightarrow$ Threshold에 따라 정상 동작도 비정상 동작으로 탐지
    + Hybrid IDSs
      + 상기 두 가지 방법을 사용함으로써, 낮은 false positive & false negative
      + 연산에 필요한 자원이 큼

[PP07]: <https://www.sciencedirect.com/science/article/pii/S138912860700062X> "A. Patcha and J.-M. Park, “An overview of anomaly detection techniques: existing solutions and latest technological trends,” Computer Networks, vol. 51, no. 12, pp. 3448–3470, 2007."
[ZLH03]: <https://dl.acm.org/citation.cfm?id=942556> "Y. Zhang, W. Lee, and Y.-A. Huang, “Intrusion detection techniques for mobile wireless networks,” Wireless Networks, vol. 9, no. 5, pp. 545–556, 2003."
[F05]: <https://faculty.kfupm.edu.sa/ics/salah/092/ics444/slides/IDS%20and%20IPS.pdf> "A. Fuchsberger, “Intrusion detection systems and intrusion prevention systems,” Information Security Technical Report, vol. 10, no. 3, pp. 134–139, 2005."
[SMR+05]: <https://dl.acm.org/citation.cfm?id=1089765> "A. P. R. Da Silva, M. H. Martins, B. P. Rocha, A. A. Loureiro, L. B. Ruiz, and H. C.Wong, “Decentralized intrusion detection in wireless sensor networks,” in Proceedings of the 1stACMInternationalWorkshop on Quality of Service & Security inWireless and Mobile Networks, pp. 16–23, ACM, Quebec, Canada, October 2005."

### Implementation Strategies

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-08-01-tbl-IDS_impl_schemes.png" legend="System model." width="75%" %}

+ 상기 장에서 다루는 솔루션들의 전략은 not centralized, distributed (since they did not find centralized solution)
+ Table 2의 A-F는 학점 표현 (A: the best, F: the worst)
+ Hierarchical IDSs
  + 인접한 IoT 장비들이 클러스터가 되어 네트워크가 구성될 때, 전력 또는 연산 자원이 많은 노드의 경우 클러스터 헤드가 되어 인접 클러스터들의 패킷 모니터링
  + 연산 자원이 충분한 노드가 있는 경우 사용하기 좋음
+ Distributed and Collaborative IDSs
  + 여러 노드들이 네트워크의 여러 측면을 관찰하고 종합하여 정상인지 확인하는 방법
  + 데이터 종합을 위한 메시지 교환 필요
+ Voting-Based IDSs
  + Distributed and Collaborative IDSs의 변형
  + 연산 능력이나 전력에 영향을 덜 받음
  + 너무 간단하다는 본질 때문에, false negative가 매우 높아질 수 있음
+ Reputation-Based IDSs
  + Distributed and Collaborative IDSs의 변형
  + 
+ Cross Layer IDSs
+ Mobile Agent-Based IDSs
+ Game Theory-Based IDSs
+ Statistical Detection-Based IDSs
+ Machine Learning-Based IDSs



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
