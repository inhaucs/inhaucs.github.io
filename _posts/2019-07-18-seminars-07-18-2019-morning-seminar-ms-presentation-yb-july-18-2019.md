---
title: Session 4. Chameleon Hashing and Signatures
date: 2019-07-18 00:00:00 Z
description: Chameleon Hashing and Signatures
card_title: Session 4
card_teaser: Chameleon Hashing and Signatures
card_position: 4
icon: fa-server
categories: [seminars,07-18-2019-morning-seminar,presentation]
tags: [NDSS, 2000, NDSS2000, Undeniable Signature, Chameleon Hash, Chameleon Signature]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-july-18-2019
permalink: /:categories/:slug.html
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
+ Undeniable signature보다 간단하고, 효율적이며, 비대화형이고, zero-knowledge 방식으로 구현되어있는것에 반해
+ Chameleon signature의 경우는 해시 서명 방식을 이용하여 서명이 되며, 사용하는 해시는 카멜레온 해시를 이용한다.


## Details
### [Undeniable signature, CA89](https://link.springer.com/content/pdf/10.1007%2F0-387-34805-0_20.pdf)
+ [Undeniable signature Wikipedia](https://en.wikipedia.org/wiki/Undeniable_signature)
+ An undeniable signature is a digital signature scheme which allows the signer to be selective to whom they allow to verify signatures. **The scheme adds explicit signature repudiation, preventing a signer later refusing to verify a signature by omission;** a situation that would devalue the signature in the eyes of the verifier. It was invented by David Chaum and Hans van Antwerpen in 1989.
+ 서명자가 자신의 서명을 검증할 수 있는 사람들을 고를 수 있는 디지털 서명 스킴. 이 스킴은 서명을 검증하는 것을 거부하는 것을 막을 수 있는(?) 분명한 서명 거부권리를 가지고 있음.
+ 서명을 생성할 때, 다음 두가지 프로토콜에 대해서 메시지, 서명에 대해 수신인/검증자에게 어떠한 정보도 넘겨주지 않음.
+ Confirmation protocol : 서명한 자의 공개키와, 메시지에 대한 서명이 유효한지 확인하는 것.
+ Disavowal protocol : 서명자로부터 나온 메시지가 유효한 서명이 아닌 것을 확인하는 것.


{% include articles/figure.html url="/assets/img/byoul/2019/2019071801.png" legend="Sign"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019071802.png" legend="Confirmation protocol"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019071803.png" legend="Disavowal protocol"%}

//20190718 발표

### Chameleon Hashing
+ 특정한 키를 함께 입력하면 해시할 때 같은 출력을 내는 다른 인풋값을 찾을 수 있다.
+ 공개키-개인키 구조로 이루어져있음.
+ 표기
  + 유저 R, 공개 키 HK, 연결되는 개인키 CK, message m, random string r
+ 특징
+ 1) 공개 키 HK를 알면 누구나 hash function 계산 가능. Hash value = CHAM-HASH(m,r)
+ 2)	Trapdoor(CK)를 모르는 사람은 충돌되는 해시값을 찾는 것은 불가능함
        CK를 모르면 CHAM-HASH(m1, r1) = CHAM-HASH(m2,r2) 인 r2를 찾기는 불가능
+ 3)	Trapdoor(CK) 정보를 가지고 있는 사람은 충돌을 쉽게 찾을 수 있음.
        CK를 알면 CHAM-HASH(m1, r1) = CHAM-HASH(m2,r2)인 r2를 쉽게 찾을 수 있음.

### Chameleon Signature
+ 표기
+ 서명자 S, 수신자 R, 판단하는 사람 J
+ "프로토콜 : SIGN, VERIFY"
+ 방식
+ S가 서명을 위한 개인-공개키쌍 생성. (각 SK, VK)
+ R이 카멜레온 해시 스킴을 쓰기 위한 개인-공개키쌍을 생성(HK, CK)
+ "SIGN : S가 m, SK, HK, random string r로 hash = CHAM-HASH(m,r), sig=SIGN(hash), SIG(m)=(m,r,sig) 생성, R에게는 SIG(m) 줌."
+ "VERIFY : R이 hash=CHAM-HASH(m,r) 로 hash값 확인 가능. VK로 sig도 확인 가능."


### Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
