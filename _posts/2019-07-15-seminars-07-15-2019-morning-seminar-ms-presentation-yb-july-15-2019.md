---
title: Session 1. Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
date: 2019-07-15 00:00:00 Z
description: Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
card_title: Session 1
card_teaser: Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
card_position: 1
icon: fa-server
categories: [seminars,07-15-2019-morning-seminar,presentation]
tags: [EUROSNP, 2017, EUROSNP2017, Blockchain, Bitcoin, Redactable Blockchain, Chameleon hash]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-july-15-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-07-15

## [Redactable Blockchain – or – Rewriting History in Bitcoin and Friends](https://inhaucs.github.io/seminars/07-15-2019-morning-seminar/presentation/ms-presentation-yb-july-15-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/7961975)
+ Authors: Giuseppe Ateniese, Bernardo Magri, Daniele Venturi, Ewerton R. Andrade 
(Stevens Institute of Technology(USA), Friedrich-Alexander University(Germany), Sapienza University of Rome(Italy), University of S˜ao Paulo(Brazil))
+ Journal name: IEEE European Symposium on Security and Privacy
+ Published date: 2017-04-26
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7961975)
+ [Full version Link](https://eprint.iacr.org/2016/757.pdf)

### Abstract
We put forward a new framework that makes it possible to re-write or compress the content of any number of blocks in decentralized services exploiting the blockchain technology. As we argue, there are several reasons to prefer an editable blockchain, spanning from the necessity to remove inappropriate content and the possibility to support applications requiring re-writable storage, to “the right to be forgotten.” 
Our approach generically leverages so-called chameleon hash functions (Krawczyk and Rabin, NDSS ’00), which allow determining hash collisions efficiently, given a secret trapdoor information. We detail how to integrate a chameleon hash function in virtually any blockchain-based technology, for both cases where the power of redacting the blockchain content is in the hands of a single trusted entity and where such a capability is distributed among several distrustful parties (as is the case with Bitcoin). 
We also report on a proof-of-concept implementation of a redactable blockchain, building on top of Nakamoto’s Bitcoin core. The prototype only requires minimal changes to the way current client software interprets the information stored in the blockchain and to the current blockchain, block, or transaction structures. Moreover, our experiments show that the overhead imposed by a redactable blockchain is small compared to the case of an immutable one.

 
## Summary (Korean)
+ 블록체인 기술의 경우 한번 블록에 기록되면 수정할 수 없다는 특징이 있는데, 이 특징이 앞으로 생성될 모든 새로운 어플리케이션에 적절하지는 않을 것임.
  + 이미 비트코인에 악용 사례가 있음. 비트코인 블록 데이터에 부적절한 콘텐츠를 올리는 사례가 있었음. [31](If you own bitcoin, you also own links to child porn.)
  + 계약을 잘못 만들었으면 다시 올리고 해야 되는데 수정이 안되니 결국 다시 올려야 함. -> 자원 낭비.
  + 올라간 데이터들이 영구적으로 안전하다는 보장이 없음.
  + 등등..

+ 따라서, 수정 가능한 블록체인을 개발해야 함.
  + 블록 수정, 삭제, 삽입, 압축이 가능하게 한다.
  + 허가된 사용자들만이 수정이 가능하며, 공개적으로 수정된다.
  + 카멜레온 해시 함수를 이용하여, 이전 블록의 해시 값과 똑 같은 해시 값을 가지는 다른 블록을 만들어낸다.

+ 기여
  + 현 블록체인에 쉽게 호환 가능
  + 개선된 카멜레온 해시 디자인 개발
  + 비트코인 위에서 실험해보고, 잘 된 것 확인.



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
{% include articles/figure.html url="/assets/img/byoul/2019/2019071205.png" legend="Chain Redact Algorithm"%}


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
