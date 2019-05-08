---
title: "Session 5. SABRE: Protecting Bitcoin against Routing Attacks"
date: 2019-05-08 00:00:00 Z
description: "SABRE: Protecting Bitcoin against Routing Attacks"
card_title: Session 5
card_teaser: "SABRE: Protecting Bitcoin against Routing Attacks"
card_position: 5
icon: fa-server
categories: [seminars,05-06-2019-morning-seminar,presentation]
tags: [NDSS, 2019, NDSS2019, Blockchain, Bitcoin]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-may-06-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-05-09

## [SABRE: Protecting Bitcoin against Routing Attacks](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-yb-apr-25-2019.html)

### Information of the paper [(Link)](https://www.ndss-symposium.org/ndss-paper/sabre-protecting-bitcoin-against-routing-attacks/)
+ Authors: Maria Apostolak, Gian Marti, Jan Miller, Laurent Vanbever (ETH Zurich)
+ Journal name: NDSS Symposium 2019 Programme
+ Published date: 2019-02-24
+ [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2019/02/ndss2019_02A-1_Apostolaki_paper.pdf)
+ [Slide Link](https://www.ndss-symposium.org/wp-content/uploads/ndss2019_02A-1_Apostolaki_slides.pdf)

### Abstract
Nowadays Internet routing attacks remain practically effective as existing countermeasures either fail to provide protection guarantees or are not easily deployable. Blockchain systems are particularly vulnerable to such attacks as they rely on Internet-wide communications to reach consensus. In particular, Bitcoin—the most widely-used cryptocurrency—can be split in half by any AS-level adversary using BGP hijacking.
 In this paper, we present SABRE, a secure and scalable Bitcoin relay network which relays blocks worldwide through a set of connections that are resilient to routing attacks. SABRE runs alongside the existing peer-to-peer network and is easily deployable. As a critical system, SABRE design is highly resilient and can efficiently handle high bandwidth loads, including Denial
of Service attacks. 
 We built SABRE around two key technical insights. First, we leverage fundamental properties of inter-domain routing (BGP) policies to host relay nodes: (i) in networks that are inherently protected against routing attacks; and (ii) on paths that are economically-preferred by the majority of Bitcoin clients. These properties are generic and can be used to protect other Blockchain-based systems. Second, we leverage the fact that relaying blocks is communication-heavy, not computation-heavy. This enables us to offload most of the relay operations to programmable network hardware (using the P4 programming language). Thanks to this hardware/software co-design, SABRE nodes operate seamlessly under high load while mitigating the effects of malicious clients. 
 We present a complete implementation of SABRE together with an extensive evaluation. Our results demonstrate that SABRE is effective at securing Bitcoin against routing attacks, even with deployments of as few as 6 nodes.
 
## Summary (Korean)
+ **비트코인 네트워크 공격 방법 중 하나인 routing attack을 방어하기 위한 SABRE relay network 개발.**
+ Internet routing attack이라는 라우팅 공격은 블록체인 시스템에 굉장히 효과적인 공격법이다. BGP hijacking 라는 routing attack을 이용하면 블록체인 네트워크를 효과적으로 분리시킬 수 있다.
+ 본 논문에서는 SABRE라는 안전하고, 확장성있는 비트코인 릴레이 네트워크를 제안한다. 이를 이용하면 DoS를 포함한 높은 bandwidth load에서 매우 탄력적이고 효과적으로 비트코인 네트워크를 이용할 수 있다.

+ SABRE는 다음과 같은 장점들을 가진다.
  + (i) 라우팅 공격을 본질적으로 방어하는 네트워크
  + (ii) 블록 동기화를 위해 비트코인 클라이언트들이 선호하는 길임.
  + (iii) 계산량이 많은게 아닌, 통신량이 많아서 프로그래밍가능한 네트워크 하드웨어에서 릴레이연산의 대부분의 부하를 줄일 수 있게 한다. 그래서 높은 load에서도 완벽하게 네트워크를 운행할 수 있다.

## Details
### Routing Attack - Hijack BGP
+ 악성 라우터(AS)가 테이블을 조작하여, Bitcoin network에서 클라이언트들의 연결을 끊는 공격.
  + (i) 합법적인 AS보다 더 구체적으로 IP prefix를 작성하여 테이블 전달, BGP의 정책에 의해 악성 AS가 보낸 테이블로 일반 합법적인 AS들이 테이블을 동기화 시킴.
  + 관련해서 [4/29 Hijack Bitcoin 발표 참조](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-yb-apr-29-2019.html)

### Relay Network
+ 비트코인 네트워크와 함께 실행되는 overlay network. 비트코인을 돕는데에 사용되며, 잘 알려진 릴레이 네트워크들은 세가지 정도가 있음. (Falcon[3], FIBRE[2], FRN[5]).
+ 이 릴레이 네트워크는 고속릴레이 노드들이나 향상된 라우팅 기술들의 시스템에 의지해서 블록 전파속도를 높이고자 하는데 이용됨. 이 릴레이들을 연결해서, 비트코인 클라이언트들이 새로운 블록을 확보 할 때 시간을 단축시켜줌.
+ 비트코인 네트워크 위에 있는 노드들을 노드라고 설명하고, 릴레이 네트워크에 있는 노드들을 릴레이라고 하는 것 같음.

### SABRE Relay Network
+ 라우팅 공격으로부터 비트코인 고객들을 보호하기 위한 투명한 릴레이 네트워크

+ 핵심 과제
  + (i) 릴레이 노드들끼리의 연결을 보호하고, 클라이언트들이 공격받는것을 최소화하기 위해서 릴레이 노드들의 위치를 잘 잡는다. 
  + (ii) 높은 load도 릴레이 노드들이 견딜 수 있도록 하드웨어/소프트웨어 공동설계 

+ (i)을 충족하기 위한 SABRE secure network design.
  + "릴레이-릴레이 연결 보호 : 릴레이를 위치시킬 라우터를 선택한다"
    + 릴레이간 연결할 때 라우터에 접두어를 /24로 설정, 우회가 안되도록 만든다.
    + 한 릴레이에 여러 릴레이가 연결되어 있을 수록, 연결을 끊을 수 있는 확률은 기하급수적으로 낮아진다. (i.e. 5-connected relay network 연결 끊을 확률은 3.1%)
  + 클라이언트-릴레이 연결 보호
    + 릴레이는 라우터를 선택할 수 있지만, 비트코인 클라이언트는 라우터를 직접 선택할 수 없음. 
    + 따라서, 악성 사용자가 비트코인 클라이언트와 바로 연결된 라우터를 장악하면, 클라이언트-릴레이 연결이 안됨.
    + "보호법 : 릴레이와 클라이언트가 연결될 때 경로 접두어를 /24로 설정해서 우회가 안되도록 만든다."
  + 릴레이-클라이언트 연결 보호
    + 릴레이-클라이언트(i.e. A)가 연결되어 있을 때, 악성 라우터가 자신은 릴레이이며, A와 자신이 더 가깝다고 주장.
    + 합법적인 릴레이-A간의 관계가 끊어지며 클라이언트가 분리되는 경우
    + "보호법 : 릴레이들끼리 통신하는걸 난독화."
  + 릴레이 위치를 라우터 어디에 잡아야 공격으로부터 네트워크 연결이 끊어지지 않는지, SABRE 릴레이의 안전한 위치를 찾는 알고리즘 설명. (생략)

+ (ii)를 충족하기 위한 SABRE resilient software/hardware node co-design. 
  + 프로그래밍 가능한 AS설계
  + P4라는 스위치에서 이용하는 프로그래밍 언어를 이용하여 설계 
    + [P4_Programming Protocol-Independent Packet Processors 참조](http://delivery.acm.org/10.1145/2660000/2656890/p87-bosshart.pdf?ip=165.246.44.150&id=2656890&acc=ACTIVE%20SERVICE&key=36491E83F85BB6C1%2E36491E83F85BB6C1%2E1702E7686A5145AB%2E4D4702B0C3E38B35&__acm__=1557307534_ece109a2cf8f2705e7222c7316be5441)
    + 847회 인용
    + 개인 의견 : 보편적으로 사용되고 있는 스위치, 라우팅 테이블을 설계할 수 있도록 프로그래밍을 할 수 있게 만든 스위치 같음.

### Evaluation
+ 라우팅 공격에 대항해서 비트코인을 보호하는 SABRE의 효율성을 평가한다. 구체적으로 다음 질문들에 대해 대답
  + 1) 라우팅 공격으로부터 전체 네트워크와 개인 클라이언트들을 얼마나 효율적으로 보호하는가?
  
{% include articles/figure.html url="/assets/img/byoul/2019/2019042502.PNG" legend="2019042502yb" %}
  
    + 비트코인 노드가 Y개일 때, AS가 SABRE로부터 노드들을 얼마나 연결을 끊어낼 수 있는지를 보임.
    + N이 20이고 k가 1일 때 오직 3%의 AS만 비트코인 클라이언트들의 연결을 끊어낼 수 있음.
    + 현재 일반 비트코인 네트워크는 90%의 확률로 어떤 AS든 연결 끊기 가능.

  + 2) 다른 릴레이 네트워크보다 방어책이 얼마나 뛰어난가?
    + (1) 기존 릴레이들은 longer-prefix hijack에 취약하다.
    + (2) 기존 릴레이들은 연결이 잘 안된다.
    + (3) 기존 릴레이들은 적용범위가 적다.


### DISCUSSIONS
+ 1) SABRE가 Bitcoin 분산 네트워크를 침범하지 않는가?
  + 침범하지 않음. 비트코인과 다른 레이어에서 비트코인이 더 잘 동작하도록 돕는 역할이지, 대체하려는 것이 아님. 
+ 2) 왜 비트코인인가?
  + (1) 비트코인 네트워크는 많이 연구되었고, 라우팅 공격의 효과가 잘 알려져 있으나 다른 블록체인의 정확한 라우팅 특성은 잘 알려져 있지 않음.
  + (2) 비트코인은 가장 널리 쓰이고 있는 암호화폐기 때문임.

+ 3) SABRE가 다른 블록체인또한 보호할 수 있는가? Yes
  + 이 네트워크와 노드 디자인의 원리는 일반적이고 다른 암호화폐시스템에서도 적용 가능하다. 예시 ByzCoin, OmniLedger (정확하게 무슨 체인인지는 확인 못함. 아마 비트코인 기반의 체인일 것으로 추측, 이더리움 블록체인에는 안되지 않을까 싶음. 확인 필요)
  + 다만, 트래픽이 암호화된 블록체인은 기계가 이용할 수 없어 서비스 제공이 안된다. 


### Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
