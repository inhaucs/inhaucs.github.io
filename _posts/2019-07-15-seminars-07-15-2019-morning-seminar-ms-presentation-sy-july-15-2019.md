---
title: Session 3. On Computing Products of Pairings
date: 2019-07-15 00:00:00 Z
description: On Computing Products of Pairings
card_title: Session 1
card_teaser: On Computing Products of Pairings
card_position: 1
icon: fa-server
categories: [seminars,07-15-2019-morning-seminar,presentation]
tags: [ePrint, 2006, Pairing, Optimization, Inner Product]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-july-15-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-07-15

## [On Computing Products of Pairings](https://inhaucs.github.io/seminars/07-15-2019-morning-seminar/presentation/ms-presentation-sy-july-15-2019.html)

### Information of the paper [(Link)](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.61.7456)
+ Authors: R. Granger, Nigel P. Smart (École Polytechnique Fédérale de Lausanne)
+ Journal name: ePrint
+ Published date: 2016-01
+ [Paper Link](http://citeseerx.ist.psu.edu/viewdoc/summary?doi=10.1.1.61.7456)

### Abstract
In many pairing-based protocols often the evaluation of the product of many pairing evaluations is required. In this paper we consider methods to compute such products efficiently. Focusing on pairing-friendly fields in particular, we evaluate methods for the Weil, Tate and Ate pairing algorithms for ordinary elliptic curves at various security levels. Our operation counts indicate that the minimal cost of each ad-ditional pairing relative to the cost of one is ≈ 0.61, 0.45, and 0.43, for each of these pairings respectively at the 128-bit security level. For larger security levels the Ate pairing can have a relative additional cost of as low as 0.13 for each additional pairing. These estimates allow implementors to make optimal algorithm choices for given scenarios, in which the number of pairings in the product, the security level, and the embedding degree are factors under consideration.

 
## Summary (Korean)
+ 많은 pairing 기반 프로토콜들은 여러차례의 pairing 연산들을 필요로함.
+ 이 논문에서는, 위와 같은 상황에서, Weil, Tate, Ate pairing 알고리즘을 최적화함. Pairing-Friendly Fields이어야함(Fp가 f(X) = X^k + f0 꼴로 표현되는 경우). 128-bit security 기준으로는, 상대적으로 각 알고리즘의 cost(페어링 횟수)를 0.61, 0.45, 0.43 수준으로 낮춤. 특히, Ate pairing의 경우에는 더 높은 security level에 대해서는 약 0.13 수준으로 낮춤.

## Details
### Blockchain Basics
{% include articles/figure.html url="/assets/img/byoul/2019/2019071201.png" legend="The redactable blockchain structure"%}

+ 기존 블록체인에서 블록이 유효한지 확인하는 함수 식
{% include articles/figure.html url="/assets/img/byoul/2019/2019071202.png" legend="validblock" width="50%"%}

### Chameleon hash function
+ IDEA 
  + 해시 값에 암호(key, trapdoor)를 걸어서, 암호를 풀면 효율적으로 충돌이 생기는 메시지를 생성할 수 있음. 
  + 즉, 키를 알고 있으면 블록 수정이 가능하고 키를 잃어버리면 그냥 변경 불가능한 일반 블록체인이 됨.

+ Secret-coin hashing : 기본 카멜레온 해시 개념
  + efficient algorithm CH = (HGen, Hash, HVer, HCol)
    + HGen : 입력(security parameter) 출력(공개 해시 키 hk, trapdoor tk)
    + Hash : 입력(hk, message m, **random coins r**), 출력( hash value h, check string ξ )
    + HVer : 입력(hk, m, h, ξ), 출력(1 또는 0)
      + m 과 (h, ξ) 가 한 쌍인 것이 확인되면 1, 아니면 0
    + HCol : 입력(tk, h, m, ξ, m’), 출력( ξ’ )
      + HVer( hk,m, h, ξ ) = HVer(hk, m’, h, ξ,’ ) = 1 이 되는 ξ’

+ Public-coin hashing
  + Hash에 쓰는 r이 원래 비밀값인데, 이것을 공개해서 쓰는 해시함수. 따라서, ξ가 필요 없기 때문에 조금씩 달라짐.
    + Hash : 입력(hk, message m, random coins r), 출력( hash value h, **random coins r**)
    + HVer : 입력(hk, m, h, r), 출력(1 또는 0)
      + **Hash 알고리즘과 결국 똑같이 생겼기 때문에 일반적으로 생략함.**


### Redactable Blockchain
+ 1) The redactable blockchain structure 그림의 G 함수에 카멜레온 해시 함수를 적용.
  + secret-coin hashing을 사용했을 때의 validblock 함수
  {% include articles/figure.html url="/assets/img/byoul/2019/2019071203.png" legend="secret-coin's validblock" width="50%"%}
  + public-coin hashing을 사용했을 때의 validblock 함수
  {% include articles/figure.html url="/assets/img/byoul/2019/2019071204.png" legend="secret-coin's validblock" width="50%"%}
  
+ 2) 체인 수정
{% include articles/figure.html url="/assets/img/byoul/2019/2019071205.png" legend="Chain Redact Algorithm"%}
  + 수정할 체인 위치 i
  + 다른 사용자들은 더 긴 체인을 가지고 있어도 이 체인으로 매핑해야 함.
  
+ 3) 키를 가져야 하는 사람이 여러명 일 때, 키 관리 방법 (MPC 프로토콜 이용)
  + (참고 : 수정 가능한 사람이 한 명이면(은행 과 같은 기관) 그냥 알아서 가지고 있으면 됨.)
  + 조건 : 수정할 수 있는 사용자 집합은 고정되어 있음.
  + 키 나눠주기
    + system이 HGen을 이용하여 hk, tk를 만들고, 수정할 수 있는 사용자들 n명이면 tk를 n으로 쪼개서 나누어 줌. 나눠줄 때 secret sharing scheme( Share, Rec)이용.
      + Share : x(tk)를 받아서 n개의 shares들을 만들어낸다.
      + Rec : n개의 shares를 받아서 x(tk)나 ㅗ 돌려준다.

  + 수정 방법
    + 1) n개의 공유부품들을 모아서 tk를 다시 생성 (tk = Rec(shares1, shares2, ..., sharesN) )
    + 2) 모든 사용자들로부터 수정할 블록 정보, 변경할 메시지를 받아서 E’ 생성할 수 있음.
    
### Chameleon Hash Transform
+ 기존의 public-coin hashing함수에서, Public-Key Encryption과 Non-Interactive Zero-Knowledge 를 이용하여 카멜레온 해시 함수를 개선함.


### Experiments
{% include articles/figure.html url="/assets/img/byoul/2019/2019071206.png" legend="Preformance"%}


### Points to note
+ 카멜레온 해시의 단점, 장점 및 그 개선으로 인한 효과, 한계가 주요 내용인 것 같은데 카멜레온 해시를 잘 모르니까 설명이 안되는 부분이 좀 많은 것 같음.
+ 설명이 안된 부분들을 마저 설명하려면 카멜레온 해시 함수에 대한 설명이 우선되어야 할 것 같고, 이후 논문에 대한 추가 설명이 필요해 보임.

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
