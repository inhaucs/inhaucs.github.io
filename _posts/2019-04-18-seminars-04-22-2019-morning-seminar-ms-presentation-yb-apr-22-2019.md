---
title: "An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain (Cont.)"
date: "2019-04-18 20:36:00 Z"
description: "a new ID-Based Linearly Homomorphic Signature Scheme 개발"
card_title: Session 1
card_teaser: "An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain (Cont.)"
card_position: 1
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [ACCESS, 2018, ACCESS2018, ID-based signature, homomorphic signature, bilinear pairings, random oracle]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-04-22

## Information of the paper
+ Authors: QUN LIN et al. Institute of Mathematics and Statistics, Hanshan Normal University, China
+ Journal name: IEEE ACCESS
+ Published date: 2018-02-27 (Present version : 2018-05-02)
+ [Paper Link](https://ieeexplore.ieee.org/document/8302552)

## Abstract
Identity-based cryptosystems mean that public keys can be directly derived from user identifiers, such as telephone numbers, email addresses, and social insurance number, and so on. So they can simplify key management procedures of certificate-based public key infrastructures and can be used to realize authentication in blockchain. Linearly homomorphic signature schemes allow to perform linear computations on authenticated data. And the correctness of the computation can be publicly verified. Although a series of homomorphic signature schemes have been designed recently, there are few homomorphic signature schemes designed in identity-based cryptography. In this paper, we construct a new ID-based linear homomorphic signature scheme, which avoids the shortcomings of the use of public-key certificates. The scheme is proved secure against existential forgery on adaptively chosen message and ID attack under the random oracle model. The ID-based linearly homomorphic signature schemes can be applied in e-business and cloud computing. Finally, we show how to apply it to realize authentication in blockchain.

## Summary (Korean)
+ Identity-based 암호체계는 핸드폰번호, 이메일 주소, 주민번호와 같은 user ID로부터 쉽게 공개키를 얻어낼 수 있는 기술이다. 그래서 이들은, 인증서 기반 공개 키 구조의 키 관리 절차보다 더 단순화되어 있고, 블록체인에서 인증에 사용할 수 있다.
+ 한편, Linearly homomorphic signature scheme는 인증 데이터에서 선형 계산을 가능하게 한다. 최근 동형서명 스킴이 많이나오기는 하는데, id기반의 동형서명스킴은 별로 없다.
+ 이 논문에서는, 공개키 인증서 기반의 단점을 극복한 새로운 id기반선형동형서명스킴을 개발한다. random oralce 모델일 때 adaptively chosen message and ID 공격에 안전하다. 또한 이 id기반선형동형서명스킴은 클라우드 컴퓨팅에서도 쓸 수 있기 때문에 블록체인에서 쓸 수 있음을 보인다.

## Details

### I. Introduction
+ 인증서 기반 암호체계는 공개키 암호체계에 널리 이용되고 있다. 이 인증서 기반 암호체계는 아래와 같은 세가지의 특징이 있다.
  + 1) **entity에게 정보를 암호화 해서 주기 위해서는 entity의 인증된 공개키 인증서가 필요하다.**
  + 2) **그래서 이러한 인증서들은 대규모로 생성되어, 커뮤니티의 많은 사람들에게 배포되어야 한다.**
  + 3) **또한 이 인증서들은 빈번하게 검증되어야 한다.**
  + **그래서 이 공개키 인증서의 관리는 성가시다.** 이러한 공개키 인증서의 단점을 피하기 위해서, Shamir가 1984년에 identity-based cryptography 개념을 소개했다. user identifier로부터 공개키를 만드는 것. private key는 Private Key Generator(PKG)라고 불리는 중앙 권한 시스템 레벨의 secret key와 user공개키 조합으로 만들 수 있음.

{% include articles/figure.html url="/assets/img/byoul/2019/20190422001.PNG" legend="2019042201yb" %}

  + 이후로 많은 ID기반 암호에 많은 진전이 있었고, ID기반 서명 스킴들, ID기반 암호스킴 등이 우후죽순 생겨났다.
 
+ 한편, 2002년에 Johnson이 동형 서명 개념 소개. 
  + **동형 서명의 개념은 중요한 기본 요소(primitive)이며, 인증된 데이터를 통해 계산을 검증할 수 있도록 한다.**(The notion of homomorphic signature is an important primitive and allows to validate computation over authenticated data.)
  + 동형 속성은 sk 없어도 서명을 검증할 수 있다. 그래서 이 동형서명스킴은 e사업이나 클라우드 컴퓨팅에서 많이 이용됨. 현재는 선형동형서명스킴, 다항식함수를 지원하는 동형 스킴 등 많은 기술들이 나와있으나, 이 기술들은 인증서 기반 암호체계에 속함.
  + ID기반 동형서명스킴은 거의 없음[34, 35, 37]. 이 중 두 개[34, 35]는 오염된 공격을 생산하는 악성 노드를 예방하기 위한 네트워크 공격쪽에 많이 쓰이고, 나머지 하나는 [37] 양자 쪽이라 비효율적임. 
  + 인증서 기반의 암호체계에서 공개키 인증서 관리는 성가시기 때문에, id기반암호체계로 효율적인 동형서명스킴을 설계하는것은 의미가 있음.


#### 개인 의견
+ 인증서 기반 공개키와 ID 기반 공개키의 차이점
  + 조금 더 자세하게 인증서 기반 공개키에 대해 단점을 찾아보았으나, 제대로 된 정의는 확인하지 못함. 
    + 2)의 경우 사람들이 A에게 무언가를 암호화 해서 주고싶을 때 A라는 identifier 뿐만 아니라 인증서관련 내용까지도 알아야 한다는 점,
    + 3)인증서들이 빈번하게 검증되어야 한다는게, 공개키 인증서가 처음 배포되고 난 뒤에 나중에 다시 이용할 때 본인의 것이 아닐 수도 있기 때문..? 이라고 판단됨. 
  + ID기반 인증서의 경우 A에게 암호화해서 주고 싶다면 Enc(x) = A(x) 식으로 암호화해서 주면 된다는 뜻인것 같음. 이렇게되면 2)의 상황도 3)의상황도 간편하게 해결 가능.

### II. PRELIMINARIES
+ A. Bilinear group 기본 속성 소개
+ B. BLS Short Signature Scheme
  + bilinear group 속성을 이용한 짧은 서명 스킴. (Keygen, Sign, Verify) 과 같은 구성이며, ECDSA 서명 방식에 비해 굉장히 간단함.
  + (개인의견) 동형서명에 가장 기본이 되는 스킴인 것 같음.

+ C. ID-based Signature Scheme[11]
  + 구성 : (Setup, Extract, Sign, Verify) 
  + (개인의견) 인증서 기반 공개키의 경우, 공개키에 대한 유효성을 지속적으로 확인해야 하지만 ID기반 공개키의 경우 ID를 공개키로 이용하면 되고, 서명은 ID 에서 추출해 내서 secret key를 만들어 이용한다. (Extract 부분)
  
 + D. ID-based Linearly Homomorphic Signature
   + 구성 : (HSetup, HExtract, HSign, HVerify, Heval)
   + (개인의견) 소개하고자 하는 스킴의 기본 개념인 것 같음.

### III. THE PROPOSED SCHEME
+ (개인의견) II-D를 실질적으로 구현한 ID기반 동형서명스킴
+ 구성 : HSetup, HExtract, HSign, HVerify, HEval

### IV. PROPOSED SCHEME ANALYSIS
+ 논문에서 정한 세 가지 가정이 모두 유지되면 이 스킴은 random oracle chosen message and ID attack에 안전함.
+ 아주 조금 더 디테일한 내용은 [04-18-2019](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-yb-apr-18-2019.html)에 작성

+ **random oracle chosen message and ID attack** : (개인의견) 정확한 정의는 확인 불가능. id-기반 스킴들에서 안전성을 분석할 때 이용하는 모델.

### V. APPLICATION IN DATA ANALYSIS AND BLOCKCHAIN
+ 저자들은 **데이터와 계산 인증**을 위해 IoT 구조에서 동형서명 스킴이 어떻게 쓰이는지를 보이고자 함.

+ 데이터가 많이 모이면, 사람들은 이를 활용하고자 함(ex, 빅데이터, 머신러닝에 데이터 이용). 이 데이터들을 데이터마이닝과 머신러닝에 이용할 때 너무 많으면 직접적인 계산이 어려워서 제 3자를 이용해서 계산하고, 결과값만 받음. 그러나, 이제 **제 3자가 준 결과값이 나의 데이터와 연관이 있는 정보인가, 가 구분할 수 없어지는 경우가 많음** 이 스킴을 이용하면 확인이 가능하다.

+ 방법
  + 1) 우선, 동형 서명을 위한 가상 identity를 위해 블록체인에서 공개 키 생성.( 주소 생성 )
  + 2) 서비스를 제공받고자 하는 데이터들을 클라우드에 올리기 전에 그 데이터들 모두 서명.
  + 3) 이제 클라우드 컴퓨터에 업로드
  + 4) 접근 정보를 포함한 데이터 포인터는 블록체인에 computed되고 stored됨.
  + 5) 데이터에 접근하기 위해서 유저는 우선 블록체인에서 포인터에 접근.
  + 6) 만약 데이터 접근이 허락되면, 데이터를 다운로드하고 계산함.
  + 7) 굳이 데이터 접근 허락 안하고 그냥 아무나 이용가능하게 해도 됨. 어차피 서명되어있으니까.
  + 8) 계산이 끝나면, 사용자는 계산결과 뿐 아니라 그 계산 결과에 대한 동형 서명 집합도 얻을 수 있음.
  + 9) 유저는 아까 1)에서 생성한 가상 identity로 계산 결과를 검증할 수 있음.
  + 10) 블록체인 기술과 함께라면, 데이터 제공자나 서비스는 데이터나 계산을 제공한 후에 정당한 지불을 받을 수 있다고 보증할 수 있음
+ 결론
  + 블록체인 기술을 이용하면, 데이터 제공자는 데이터 정보나 그들의 서명을 변경할 수 없음. 또한, 중앙 권한자 없이도 블록체인을 통해 공정함을 보증할 수 있음.
  + 또한, 동형 서명 기술과 함게하면 인증을 유지하면서 데이터 연산을 할 수 있음. 결과는 서명을 확인함으로써 검증 가능.
+ 개인의견
  + 데이터에 암호화가 되어있는게 아니고 서명이 되어있는건데, 접근 허락을 어떤 식으로 하겠다는건지 이해 못함. 
  + **데이터에 서명을 넣고 데이터를 주면, 제 3자가 이용(클라우드 컴퓨터가 머신러닝에 이용). 그 결과에는 내 서명이 이미 들어 있음. 그래서 여기에 내 데이터가 처리되었음을 알 수 있음**
  
  
### VI. CONCLUSION
+ ID-based linearly homomorphic signature 개념 소개
+ new ID-based linearly homomorphic signature 개발
+ public-key certificates 의 단점을 극복
  + random oracle model에서 adaptively chosen message and ID 공격에 안전함.
  + e-사업, 클라우드 컴퓨팅, 블록체인 등 분산된 곳에서도 사용 가능

## Point to note

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
