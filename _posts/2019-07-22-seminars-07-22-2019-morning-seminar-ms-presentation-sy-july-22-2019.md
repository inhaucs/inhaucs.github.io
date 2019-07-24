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
최근 4차산업혁명이 뜨고 있다. 스마트 팩토리는 유연성(flexibility)와 재설정가능성(reconfigurability)을 고려한 4 layer 구조(fig 1)로 설비할 수 있다.
4차산업혁명을 구현(implementation)하는 입장에서 큰 관심사 중 하나는 보안(security)이다.
[하드웨어 트로이 목마](http://www.epnc.co.kr/news/articleView.html?idxno=13453)(hardware Trojans and backdoors)는 탐지가 매우 어렵고,
4 layer 구조는 잠재적으로 터미널(terminal)이 클라우드(cloud)의 취약점을 이용해 클라우드를 통해
결국은 물리적 자원(physical resource)의 제어권 획득, 정보 탈취 및 민감한 정보 노출 등의 위험이 있다.(예를 들어, 클라우드로부터 터미널의 접속 기록 획득, 로컬 DB로 관리하고 있는 정보에 접근하여 정보 탈취 등)
이 논문에서는 4 layer 구조에서 착안하여 BSeIn 시스템을 구성하였고, 
블록체인 기반의 상호 간의 인증과 세부적인 권한을 제어하는 시스템이 갖춰야하는 13가지의 보안 요구 사항을 타 논문들을 참고하여 제시하였고,
BSeIn은 이 13가지의 보안 요구 사항을 모두 만족하는 안전한 시스템임을 검증하였다. 그리고 실험을 통해 수행 성능도 실용적임을 제시하였다.
안전한 시스템을 구축하기 위해 다양한 암호기법들(ABS,MRE,AES,MAC)을 사용하였다.

## Contents

## Points to note

## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}