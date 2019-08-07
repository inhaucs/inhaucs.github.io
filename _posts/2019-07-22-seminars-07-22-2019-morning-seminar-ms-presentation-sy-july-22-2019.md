---
title: "Session 2: BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0"
date: 2019-07-22 00:00:00 Z
description: "BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0"
card_title: Session 2
card_teaser: "BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0"
card_position: 2
icon: fa-server
categories: [seminars,07-22-2019-morning-seminar,presentation]
tags: [Industry 4.0, Smart factory, Blockchain, Smart contract, Authentication, Access control, Blockchain-based secure mutual authentication]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-july-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon(전성윤)
+ 2019-07-22

## [BSeIn: A blockchain-based secure mutual authentication with fine-grained access control system for industry 4.0](https://inhaucs.github.io/seminars/07-22-2019-morning-seminar/presentation/ms-presentation-sy-july-22-2019.html)

## Abstract
To be prepared for the ‘Industry 4.0’-era, we propose a hierarchical framework comprising four tangible layers, which is designed to vertically integrate inter-organizational value networks, engineering value chain, manufacturing factories, etc. The conceptual framework allows us to efficiently implement a flexible and reconfigurable smart factory. However, we need to consider security inherent in existing (stand-alone) devices and networks as well as those that may arise in such integrations. Especially the existing solutions are insufficient to address these fundamental security concerns. Thus, we present a blockchain-based system for secure mutual authentication, BSeIn, to enforce fine-grained access control polices. The proposed system (with integrated attribute signature, multi-receivers encryption and message authentication code) is designed to provide privacy and security guarantees such as anonymous authentication, auditability, and confidentiality. BSeIn also scales well due to the utilization of smart contract. We then evaluate the security and performance of BSeIn. For example, findings from the performance evaluation demonstrate that Initialization/Request Issuance/Chain Transaction/State Delivery/Permission Update phase only cost 12.123/4.810/6.978/0.013/2.559s, respectively.

## Summary
최근 4차산업혁명이 뜨고 있다. 스마트 팩토리는 유연성(flexibility)와 재설정가능성(reconfigurability)을 고려한 4 layer 구조(Fig 1)로 구성할 수 있다.
4차산업혁명을 구현(implementation)하는 입장에서 큰 관심사 중 하나는 보안(security)이다.
[하드웨어 트로이 목마](http://www.epnc.co.kr/news/articleView.html?idxno=13453)(hardware Trojans and backdoors)는 탐지가 매우 어렵고,
4 layer 구조는 잠재적으로 터미널(terminal)이 클라우드(cloud)의 취약점을 이용해 클라우드를 통해
결국은 물리적 자원(physical resource)의 제어권 획득, 정보 탈취 및 민감한 정보 노출 등의 위험(예를 들어, 클라우드로부터 터미널의 접속 기록 획득, 로컬 DB로 관리하고 있는 정보에 접근하여 정보 탈취 등)이 있다.
이 논문에서는 4 layer 구조에서 착안하여 BSeIn 시스템을 구성하였다. 안전한 시스템을 구축하기 위해 다양한 암호기법들(ABS,MRE,AES,MAC)을 사용하였다.
또한, 블록체인 기반의 상호 간 인증과 세부적인 권한을 제어(fine-grained access control)하는 시스템으로서 갖춰야하는 13가지의 보안 요구 사항을 타 논문들을 참고하여 제시하였고,
BSeIn은 이 13가지의 보안 요구 사항을 모두 만족하는 안전한 시스템임을 검증하였다. 
마지막으로, 실험을 통해 수행 성능도 실용적임을 제시하였다.

## Contents
1. 사전지식
 - 4차 산업(Industry 4.0) ; IoT, Cyber Physical Systems, 센서기술 등을 기반으로 생산 전 과정을 연결 -> 실시간 모니터링 및 피드백 -> 생산성 증대
 - 4-Layer 구조 ; (Fig 1 참고)
    - Terminals ; 사용자에 가까운 단말 기기
    - Cloud ; 정책적인 것을 결정하는 시스템(ex. ERP)
    - Industrial Network ; Physical Resources 를 연동하는 네트워크
    - Physical Resources ; 실제 일을 수행하는 자원
 - ABS ; attribute-based encryption.
    - signer가 특정 attribute들의 셋들을 소유한 채로 (attribute authority 존재) 서명하고 검증하는 전자서명 방법.
    - Maji et al.이 2010년에 제안한 실용적인 ABS 사용
 - MRE ; multi-receiver encryption.
    - Open network에서 한 주체가 미리 선택된 다른 주체들(receivers)에게 동일한 메시지를 안전하게 방송(broadcast)하는 방법. 
    - IsIam et al.이 2015년에 제안한 스킴을 적용함

2. BSeIn
 - 앞서 설명한 4-Layer 구조를 기반으로 ABS,MRE,AES,MAC와 블록체인 기술들을 융합하여 만든 4차 산업을 위한 Framework
 - 구조 ; (Fig 2 참고)
    - Terminals ; Blockchain Network에 접근 or 명령 처리를 위한 request transaction을 publish함
    - Blockchain Network ; 사설 체인(permissioned fabric)을 사용. 합의 방식은 PBFT(뒤에서 설명함) 사용. 트랜잭션을 검증하는 validation node(vdn)과 검증된 트랜잭션을 블록체인에 chaining 하는 bookkeeping node(bkn)으로 나뉘어져있음. Terminals를 통해 요청된 request는 트랜잭션의 형태로 합의를 거쳐 블록체인에 chaining됨. 
    - Cloud ; Physical resources로 부터 대량의 데이터들을 수집하고 처리하기도 하며, Terminals로 부터 온 데이터 접근 request를 처리함. Terminals로 부터 온 request는 블록체인에 있기 때문에, 클라우드는 Blockchain Network를 모니터링하다가 등록된 request들을 처리하게됨.
    - Industrial Network ; Cloud와 달리 Terminals로 부터 온 제어 명령 request를 수행한다. Cloud와 마찬가지로 Blockchain Network를 모니터링한다. 단, Physical Resources와 연결되어 있어 제어 요청을 처리할 때 Physical Resources를 제어할 수 있는 네트워크이다.
    - Physical Resources ; 기존의 시스템과 달라진 점이 없어 설명을 생략한다.
 - 기술들의 적용
    - A. Terminals를 익명으로 인증(anonymously authenticate)하기 위해 블록체인과 ABS 적용
    - B. Gateways를 효율적으로 인증(efficiently authenticate)하기 위해 MAC을 활용
    - C. 허가된 참가자(authorized participants, (e.g. permission nodes, cloud gateway, Industrial network gateway))만 요청한 메시지들의 raw 컨텍스트에 대한 접근 권한을 얻을 수 있게하려고 MRE를 활용
    - D. Industry 4.0 어플리케이션들에서는 확장성(scalability)가 보장되어야하는게 기본 -> 전체 요청 절차(request process)는 smart contracts와 상호작용하는 구조. (Smart Contract on PDHT or Smart Contract on TX 사용)
 - 설계(Design)
   - TBD

3. BSeIn이 충족시킨 13가지의 보안 요구사항(Aitzhan and Svetinovic, 2016; He et al., 2016)
 - Single registration ; 사용자 1명 당 등록은 1회만 수행한다.
 - Mutual authentication ; 시스템은 상호적인 인증을 제공해야한다. 예) Terminals -> Gateways and Gateways -> Terminals
 - User anonymity ; 블록체인 입장에서는 transaction들을 통해 Terminal의 identity를 구분할 수 있으면 안된다.
 - Fine-grained access control ; 세분화된 접근 권한 관리. 예) Accept/Reject -> if one has A, B, C and D, Accept else Reject
 - Session key agreement ; 안전한 통신을 위해 세션 키를 활용해야함
 - Perfect forward secrecy ; 줄여서 PFS라고 함. 만일 현재 비밀키가 노출되었더라도 이전의 세션들을 복구할 수 없어야함
 - No verifier table ; 시스템은 verifier table에 의존해서는 안됨. (verifier table이란..?)
 - No online registration center ; 3rd party(TP)를 가지는 것을 피한다.
 - Relay current timestamp ; 블록체인을 사용하다 보니, 블록 간에 올바른 타임스탬프로 정렬되어야한다(?)
 - Birthday collision resilience ; 시스템은 birthday collision으로 인한 chaining 문제가 발생하지 않아야한다.
 - Interception and modification resilience ; 전송된 메시지는 interception이나 modification으로부터 별도의 detection없이 보호되어야한다
 - Hijacking resilience ; 공격자가 transaction들을 hijacking하는 것에 대한 잠재적인 위협을 별도의 detection없이 줄여야한다.
 - Resilience to other attacks ; 시스템은 impersonation, D-DoS attack, modification attack, replay attack, MITM attack 등으로 부터 안전해야한다.

5. 실험 및 성능 평가
 - 전체 요약은 Table 8을 참고

## Points to note

## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
