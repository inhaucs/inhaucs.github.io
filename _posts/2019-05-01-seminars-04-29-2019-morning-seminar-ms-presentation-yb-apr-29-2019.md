---
title: "Session 4. Hijacking Bitcoin: Routing Attacks on Cryptocurrencies"
date: 2019-05-01 00:00:00 Z
description: "Hijacking Bitcoin: Routing Attacks on Cryptocurrencies"
card_title: Session 4
card_teaser: "Hijacking Bitcoin: Routing Attacks on Cryptocurrencies"
card_position: 4
icon: fa-server
categories: [seminars,04-29-2019-morning-seminar,presentation]
tags: [SNPC, 2017, SNPC2017, Bitcoin, Cryptocurriencies, Routing Attack, Hijacking, Blockchain]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-apr-29-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-05-01

## [Hijacking Bitcoin: Routing Attacks on Cryptocurrencies]
(https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-yb-apr-29-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/7958588)
+ Authors: Maria Apostolaki(ETH Zurich), Aviv Zohar(The Hebrew University), Laurent Vanbever(ETH Zurich)
+ Conference name: 2017 IEEE Symposium on Security and Privacy
+ Published date: 2017-05-22
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7958588)


### Abstract
+ As the most successful cryptocurrency to date, Bitcoin constitutes a target of choice for attackers. While many attack vectors have already been uncovered, one important vector has been left out though: attacking the currency via the Internet routing infrastructure itself. Indeed, by manipulating routing advertisements (BGP hijacks) or by naturally intercepting traffic, Autonomous Systems (ASes) can intercept and manipulate a large fraction of Bitcoin traffic. This paper presents the first taxonomy of routing attacks and their impact on Bitcoin, considering both small-scale attacks, targeting individual nodes, and large-scale attacks, targeting the network as a whole. While challenging, we show that two key properties make routing attacks practical: (i) the efficiency of routing manipulation; and (ii) the significant centralization of Bitcoin in terms of mining and routing. Specifically, we find that any network attacker can hijack few (<;100) BGP prefixes to isolate ~50% of the mining power-even when considering that mining pools are heavily multi-homed. We also show that on-path network attackers can considerably slow down block propagation by interfering with few key Bitcoin messages. We demonstrate the feasibility of each attack against the deployed Bitcoin software. We also quantify their effectiveness on the current Bitcoin topology using data collected from a Bitcoin supernode combined with BGP routing data. The potential damage to Bitcoin is worrying. By isolating parts of the network or delaying block propagation, attackers can cause a significant amount of mining power to be wasted, leading to revenue losses and enabling a wide range of exploits such as double spending. To prevent such effects in practice, we provide both short and long-term countermeasures, some of which can be deployed immediately.

### Summary (Korean) 
+ 암호화폐에서의 Routing Attack 방법
  + Partitioning Attack
  + Delay Attack
+ 평가, 대책 제시.

## Details

### Introduction
+ 라우팅 공격이 개별 노드 대상의 소규모 공격과, 네트워크 전체 대상의 대규모 공격에 끼치는 영향에 대해 얘기한다.
+ 다음 두 가지 방식을 이용하여 비트코인 네트워크를 공격한다.
  + 1) 라우터를 조작하여 많은 비트코인 노드끼리에 대한 연결을 가로챈다.
  + 2) 라우터가 각각 담당하는 연결량이 제각각이다. (라우터가 비트코인끼리의 연결을 많이 하고 있을 수도 있고, 거의 안하고 있을 수도 있다.)

+ 두가지 공격 방식을 고려한다.
  + 1) "Partitioning attack: 공격자가 Bitcoin 네트워크에서 노드 집합을 격리, 고립시키는 방법"
  + 2) "Delay attack: 핵심 Bitcoin 메시지를 조작하여 블록 전파를 늦추는 방법."

+ 결과적으로, 차단/지연시키니 채굴할 때 문제가 생겨 수익을 잃고, 이중지출공격과 selfish mining 공격에 더 취약해진다.
+ Bitcoin 트래픽을 암호화 하는 방법 등이 고려됨.
+ Bitcoin 뿐 아니라 Ethereum, Litecoin, ZCash에서도 통용될 수 있으니 주의해야 함.

### BGP hijack
+ [참고](https://en.wikipedia.org/wiki/BGP_hijacking])
  + filtering, MD5/TTL 보호로 대부분의 BGP hijack 공격 차단이 가능은 하지만, 완벽 차단은 안됨. (일반적이고 효율적인 방법은 없음.)
  
### Partitioning attack
+ 공격 방법
{% include articles/figure.html url="/assets/img/byoul/2019/2019050101.PNG" legend="2019050101yb" %}
  
+ 효용성
  + 1) 2분만에 공격자가 비트코인 네트워크에서 그들 자신의 비트코인 노드를 떼어낼 수 있었음.
  {% include articles/figure.html url="/assets/img/byoul/2019/2019050102.PNG" legend="2019050102yb" %}
  + 2) 이미 Bitcoin에서 이러한 공격이 일어나고있음.
  {% include articles/figure.html url="/assets/img/byoul/2019/2019050103.PNG" legend="2019050103yb" %}
  + 3) 100개 미만의 접두어로 **악의적인 라우터를 지나가는 비트코인 네트워크를 충분히 반**으로 쪼갤 수 있음을 보임 (VII-B)
  + 4) 네트워크가 끊어져도 공격이 멈추면 바로 복구되긴 함. 다만 조밀하게 연결되려면 시간이 걸림.
+ 결과
  + 1) 비트코인 네트워크 두개로 쪼개기 가능
  + 2) 채굴로 인한 이득이 없어짐
  + 3) 이중지출, selfish mining 위험성이 증가.
  
### Delay attack
+ 공격 방법
{% include articles/figure.html url="/assets/img/byoul/2019/2019050104.PNG" legend="2019050104yb" %}
+ 효용성
  + 1) 단일 노드에 대한 지연공격은 잘 작동함
  {% include articles/figure.html url="/assets/img/byoul/2019/2019050105.PNG" legend="2019050105yb" %}
  + 2) 전체 네트워크를 대상으로 할 경우 효율이 좋지는 않음. 특히, multi-home(private pool traffic)가 3개정도 이상으로 연결되있을 경우 효율성은 많이 떨어짐.
  
### Countermeasures
+ 간단한 해결책
  + 1) "Increase the diversity of node connections : 연결된 AS개수 늘리기"
  + 2) "Select Bitcoin peers while taking routing into account : 라우터 위치 혹은 라우팅을 고려한 비트코인 피어 선택"
  + 3) Monitor round-trip time(RTT)
  + etc..
+ 장기적인 해결책
  + 1)  Encrypt Bitcoin Communication and/or adopt MAC 
  + 2)  Use distinct control and data channels
  + 3)  Use UDP heartbeats
  + 4)  Request a block on multiple connections 
  
### Points to note



## Discussion

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
