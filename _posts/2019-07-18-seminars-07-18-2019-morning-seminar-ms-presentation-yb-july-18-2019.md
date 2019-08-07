---
title: Session 4. Chameleon Hashing and Signatures
date: 2019-07-18 00:00:00 Z
description: Chameleon Hashing and Signatures
card_title: Session 4
card_teaser: Chameleon Hashing and Signatures
card_position: 4
icon: fa-server
categories: [seminars,07-18-2019-morning-seminar,presentation, 08-01-2019-morning-seminar]
tags: [NDSS, 2000, NDSS2000, Undeniable Signature, Chameleon Hash, Chameleon Signature]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-july-18-2019
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-07-18

## [Chameleon Hashing and Signatures](https://inhaucs.github.io/seminars/07-18-2019-morning-seminar/presentation/ms-presentation-yb-july-18-2019.html)

### Information of the paper [(Link)](https://pdfs.semanticscholar.org/1c29/4428c76ba7d1d0bb5e1d1bc931138c092453.pdf)
+ Authors: Hugo Krawczyk, Tal Rabin (IBM Research) 
+ Published date: 1997
+ Published Version
  + Title : Chameleon Signatures
  + Conference name: Network and Distributed System Security Symposium 2000
  + Published date: 2000-02-03
  + Information of the paper[(Link)](https://www.ndss-symposium.org/ndss2000/chameleon-signatures/)
  + [Paper Link](https://www.ndss-symposium.org/wp-content/uploads/2017/09/Chameleon-Signatures-paper-Hugo-Krawczyk.pdf)
  

### Abstract
We introduce chameleon signatures that provide with an undeniable commitment of the signer to the contents of the signed document (as regular digital signatures do) but, at the same time, do not allow the recipient of the signature to disclose the contents of the signed information to any third party without the signer’s consent. These signatures are closely related to \undeniable signatures”, but chameleon signatures allow for simpler and more efficient realizations than the latter. In particular, they are essentially non-interactive and do not involve the design and complexity of zero-knowledge proofs on which traditional undeniable signatures are based. Instead, chameleon signatures are generated under the standard method of hash-then-sign. Yet, the hash functions which are used are chameleon hash functions. These hash functions are characterized by the nonstandard property of being collision-resistant for the signer but collision tractable for the recipient.

 
## Summary (Korean)
+ 일반적으로 디지털 서명은 부인방지기능을 제공하는 암호 툴임. 그러나 이 경우, 수신자가 발신자의 동의 없이 서명된 내용을 아무에게나 공유할 수 있게 됨.
+ Undeniable signature라는 서명기법이 있는데, zero-knowledge방식을 이용하여 위의 단점을 해결함. 그러나, zero-knowledge를 이용하는 것 때문에 복잡해지고, 비효율적인 상태임.
+ 본 논문에서는 Chameleon signature라는 서명기법을 이용.
+ Undeniable signature의 개념에서 시작하지만 보다 간단하고, 효율적이며, 비대화형이고,
+ Zero-knowledge 방식으로 구현되어있는것에 반해 Chameleon signature의 경우는 해시 서명 방식을 이용하여 서명이 되며, 사용하는 해시는 카멜레온 해시를 이용한다.


## Details
### [Undeniable signature, CA89](https://link.springer.com/content/pdf/10.1007%2F0-387-34805-0_20.pdf)
+ 일반 디지털 서명과 다른 점 : 서명자의 협조 없이 서명 검증이 불가능하다.
+ 방법 : 서명자에게 challenge주고 서명 응답 요청.
+ 테스트가 성공하면 서명은 유효함
+ 테스트가 성공하지 않으면
+ a) 서명이 잘못됨(유효하지 않음)
+ b) 서명자가 잘못된 서명을 부인하기 위해 부적절한 응답을 함.  자신의 서명이 아니라고 거짓말 함.  두번째 challenge 제공을 통해 구분 가능.

{% include articles/figure.html url="/assets/img/byoul/2019/2019080701.png" legend="Verification Success"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019080702.png" legend="Verification Fail - message invalid"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019080703.png" legend="Verification Fail - deny"%}



### Chameleon Hashing
+ 특정한 키를 함께 입력하면 해시할 때 같은 출력을 내는 다른 인풋값을 찾을 수 있다.
+ 공개키-개인키 구조로 이루어져있음.
+ 표기
+ 유저 $R$, 공개키 $HK_R$, 매칭되는 비밀키 $CK_R$ (충돌 찾는 trapdoor), Message $m$, random string $r$
+ $hash = CHAM-HASH_R (m, r)$
+ 특징
+ 공개 키 $HK_R$을 알면 누구나 hash function 계산이 가능하도록 함.
+ Collision resistance : trapdoor($CK_R$)를 모르는 사람은 해시값이 충돌되는 인자를 찾는 것은 불가능함. $CK_R$을 모르면 $CHAM-HASH(m1, r1) = CHAM-HASH(m2,r2) 인 r2를 찾기는 불가능.
+ Trapdoor collision : trapdoor($CK_R$) 정보를 가지고 있는 사람은 충돌을 쉽게 찾을 수 있음. $CK_R$을 알면 $CHAM-HASH(m1, r1) = CHAM-HASH(m2,r2) 인 r2를 찾는 것은 매우 쉬움.

#### Chameleon Hashing Based on Discrete Log 
+ 위의 특징들을 만족하는 Chameleon hash 만드는 예
+ $CK_R$ = $x$, $HK_R$은 $y = g^x$
+ $hash = CHAM-HASH_y (m, r) = g^m y^r = g^(m+xr) $임.
  + y만 알면 누구나 다 hash function 계산 가능.
+ Collision resistance : $x$를 모르면 $m2$, $r2$를 찾기가 어려움.
+ Trapdoor collision : $x$를 알면 $m2$를 정하고, $r2$는 자연스레 계산이 가능.

### Chameleon Signature
+ 표기
+ 서명자 S, 수신자 R, 판단하는 사람 J
+ 프로토콜 : SIGN, VERIFY
+ 방식
+ S가 서명을 위한 개인-공개키 쌍 생성. (각 $SK_S$, $VK_S$)
+ R이 카멜레온 해시 스킴을 쓰기 위한 개인-공개키 쌍을 생성($CK_R$, $HK_R$)
+ SIGN : $hash = CHAM-HASH_R (m, r), sig=SIGN(hash), SIG(m)=(m, r, sig)$ 생성, R에게 $SIG(m)$ 줌.
+ VERIFY : R이 $hash=CHAM-HASH_R (m,r)$ 로 hash값 확인, $VK_S$로 $sig$와 $hash$가 일치하는지 검증 가능. 
+ Dispute
+ 이러한 서명은 R과 S에게만 유효함. R이외의 다른 사람은 $SIG$를 받았을 때 R이 새로 만든 서명인지, 혹은 S가 만든 서명인지 확인할 수 없음.
+ 만약 R이 새로운 $SIG(\hat{m}) = (\hat{m}, \hat{r}, \widehat{sig})$ 를 만들었다고 가정. (R은 trapdoor를 알기 때문에 충돌찾기가 쉬움)
+ J에게 모든 정보를 주고 검증 요청.
  + 서명 검증이 안된다면 그냥 서명 실패
  + 서명 검증이 되었다면, $\hat{SIG}$를 S에게 줌.
    + S가 그냥 넘어가도 괜찮으면 인정해 줌.
    + 서명을 거절하고 싶으면, 기존에 만들어둔 $m, r$을 제공.
      + S는 trapdoor를 가지고 있지 않기 때문에 Collision resistance 정의에 의해 충돌하는 $m, r$ 을 찾을 수 없다는 가정에 모순, R이 위조한 것임을 증명 가능.


### Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
