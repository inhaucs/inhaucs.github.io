---
title: "Session 3. SABRE: Protecting Bitcoin against Routing Attacks"
date: 2019-04-23 00:00:00 Z
description: "SABRE: Protecting Bitcoin against Routing Attacks"
card_title: Session 3
card_teaser: "SABRE: Protecting Bitcoin against Routing Attacks"
card_position: 3
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [NDSS, 2019, NDSS2019, Blockchain, Bitcoin]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-04-25

## [SABRE: Protecting Bitcoin against Routing Attacks](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-yb-apr-25-2019.html)

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
+ 비트코인 네트워크 공격 방법 중 하나인 routing attack을 방어하기 위한 SABRE relay network 개발.

## Details
### Introduction
+ 공격 기법 중 하나인 Internet routing attack은 블록체인 시스템에 굉장히 효과적인 공격법이다. BGP hijacking 라는 routing attack을 이용하면 블록체인 네트워크를 반으로 쪼갤 수 있다.
+ 본 논문에서는 SABRE라는 안전하고, 확장성있는 비트코인 릴레이 네트워크를 제안한다. 이를 이용하면 DoS를 포함한 높은 bandwidth load에서 매우 탄력적이고 효과적으로 비트코인 네트워크를 이용할 수 있다.

+ SABRE는 다음과 같은 장점들을 가진다.
  + (i) 라우팅 공격을 본질적으로 방어하는 네트워크
  + (ii) 블록 동기화를 위해 비트코인 클라이언트들이 선호하는 길임.
  + (iii) 계산량이 많은게 아닌, 통신량이 많아서 프로그래밍가능한 네트워크 하드웨어에서 릴레이연산의 대부분을 줄일 수 있게 한다. 그래서 높은 load에서도 완벽하게 네트워크를 운행할 수 있다.

### Routing Attack - Hijack BGP
+ 악성 라우터(AS)가 테이블을 조작하여, 다른 AS끼리 연결을 끊게 하는 방법
  + (i) 합법적인 AS보다 더 구체적으로 IP prefix를 작성하여 테이블 전달,
  + (ii) 똑같이 구체적이게 한다면, 이미 테이블에 존재하는 IP prefix로 작성.
+ 이런 경우, BGP의 정책에 의해 악성 AS가 보낸 테이블로 일반 합법적인 AS들이 테이블을 동기화 시킴.
+ **즉, 비트코인 클라이언트들간의 통신을 끊어버리면서, 비트코인을 두 네트워크로 분리시켜버릴 수 있음.**

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
  + 릴레이-릴레이, 고객-릴레이, 릴레이-고객 연결을 라우팅 공격으로부터 어떻게 보호하는지 설명함.

{% include articles/figure.html url="/assets/img/byoul/2019/2019042501.PNG" legend="2019042501yb" %}
  
    + 2c의 그림에서 비트코인 노드들은 서로 연결이 되어있음 + 릴레이 노드들과 적어도 하나씩은 연결이 되어있음.
    + 릴레이 r2가 있으므로 체인은 깨지지 않음. 따라서, 릴레이의 위치를 잘 잡는게 중요하며, 이 릴레이가 가르키는 위치를 공격자가 가르키는 위치보다 더 선호하게 만든다.
  + 릴레이 위치를 라우터 어디에 잡아야 공격으로부터 네트워크 연결이 끊어지지 않는지, SABRE 릴레이의 안전한 위치를 찾는 알고리즘 설명. (생략)

+ (ii)를 충족하기 위한 SABRE resilient software/hardware node co-design. 
  + 프로그래밍 가능한 AS설계

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
