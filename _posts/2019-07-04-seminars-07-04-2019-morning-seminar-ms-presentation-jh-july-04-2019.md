---
title: Session 3. PrivBioMTAuth. Privacy Preserving Biometrics-Based and User Centric Protocol for User Authentication From Mobile Phones
date: 2019-07-03 00:00:00 Z
description: PrivBioMTAuth. Privacy Preserving Biometrics-Based and User Centric Protocol for User Authentication From Mobile Phones
card_title: Session 3
card_teaser: PrivBioMTAuth. Privacy Preserving Biometrics-Based and User Centric Protocol for User Authentication From Mobile Phones
card_position: 3
icon: fa-server
categories: [seminars,07-04-2019-morning-seminar,presentation]
tags: [TIFS, 2018, TIFS2018, Privacy-Preserving, Biometrics, Zero-Knowledge, Proof-Of-Knowledge, Key-Derivation]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-july-04-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-07-04

## [PrivBioMTAuth: Privacy Preserving Biometrics-Based and User Centric Protocol for User Authentication From Mobile Phones](https://inhaucs.github.io/seminars/07-01-2019-morning-seminar/presentation/ms-presentation-hy-july-01-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8691576)
+ Authors: Hasini Gunasinghe; Elisa Bertino (Purdue University)
+ **Journal** name: IEEE Transactions on Information Forensics and Security
+ Published date: 2017-11-24 
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8119873)


### Abstract
As the size and source of network traffic increase, so does the challenge of monitoring and analyzing network traffic. Therefore, sampling algorithms are often used to alleviate these scalability issues. However, the use of high entropy data streams, through the use of either encryption or compression, further compounds the challenge as current state-of-the-art algorithms cannot accurately and efficiently differentiate between encrypted and compressed packets. In this paper, we propose a novel traffic classification method named High Entropy DistinGuishEr (HEDGE) to distinguish between compressed and encrypted traffic. HEDGE is based on the evaluation of the randomness of the data streams and can be applied to individual packets without the need to have access to the entire stream. The findings from the evaluation show that our approach outperforms current state of the art. We also make available our statistically sound dataset, based on known benchmarks, to the wider research community.


## Summary (Korean)

+ 여러 Service Provider (SP) 들에 대해 바이오인증 정보를 숨기면서 안전하게 사용자를 인증을 하기 위한 방법

+ 이를 구현하기 위해, 바이오인증 정보 이외에도 패스워드, symmetric encryption을 이용함

  + 결과적으로, 3-factor authentication이 됨
  + 기술적으로는 Key derivation function, Zero-knowledge proof of knowledge (ZKPK), SVM, PCA, Symmetric encryption, Digital signature 등이 사용됨.

+ 총 3가지 파티(User, Service Provider, Identity Provider)와, 두 phase로 구성됨

  + Enrollment phase: Identity provider (IDP)가 User에 대한 Identity token (IDT)를 발급하고 서명하는 단계
  + Authentication phase: Service provider (SP)가 IDP에 등록되어있는 사용자를 인증하는 단계

+ 제시한 결과는 real-time이 아니지만, ["Moto G"](https://www.gsmarena.com/motorola_moto_g-5831.php)를 테스트 기기로 사용해서 성능이 느리게 보일 뿐, 실제 연산은 real-time에 가능할 것으로 보임

  

## Proposed Protocol
{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-04-fig-enrollment.png" legend="Enrollment Phase." width="80%" %}



{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-04-fig-authentication.png" legend="Authentication Phase." width="80%" %}




## Preliminaries

### Key Derivation Function

+ Digest (= Salt + Password)를 생성할 때, 솔팅과 키 스트레칭을 반복하며 솔트와 패스워드 외에도 입력 값을 추가하여 공격자가 쉽게 Digest를 유추할 수 없도록 하고 보안 강도를 선택할 수 있는 기능을 제공함.
  + 솔팅: 단방향 해시 함수에 추가되는 바이트 단위의 임의의 문자열인 솔트(salt)를 추가하는 방법
  + 키 스트레칭: 다이제스트를 입력으로 다시 함수를 수행하는 방법
+ GPU와 같은 장비를 이용한 병렬화를 어렵게 하는 기능을 제공한다.

#### Password-Based Key Derivation Function (PBKDF2)

`DIGEST = PBKDF2(PRF, Password, Salt, c, DLen)`

+ c: iteration 수
+ DLen: digest 길이



### Zero-Knowledge Proof of Knowledge (ZKPK)

#### [Pedersen Commitment](https://www.cs.cornell.edu/courses/cs754/2001fa/129.PDF)

+ Setup, Commit, Open 세 단계로 이루어져 있음
  + Setup에서는 Verifier가 큰 소수(p, q)를 뽑고 정수군을 선택함
  + Commit에서는 Verifier가 C = g^x*h^r   (x, r \in Z_q)을 계산함.
  + Open에서는 Prover가 생성한 x'와 r'를 이용해 C == g^x' h^r'이 되도록하는 값을 Verifier가 확인함.

#### ZKPK Protocol

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-07-04-fig-zkpk.png" legend="Authentication Phase." width="50%" %}



## Results and Conclusion

+ 

### Points to note

+ 

## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
