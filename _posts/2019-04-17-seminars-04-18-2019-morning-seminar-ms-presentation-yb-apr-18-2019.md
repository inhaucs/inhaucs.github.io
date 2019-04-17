---
title: "An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain"
date: "2019-04-17 20:36:00 Z"
description: "a new ID-Based Linearly Homomorphic Signature Scheme 개발"
card_title: Session 4
card_teaser: "An ID-Based Linearly Homomorphic Signature Scheme and Its Application in Blockchain"
card_position: 4
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
tags: [ACCESS, 2018, ACCESS2018, ID-based signature, homomorphic signature, bilinear pairings, random oracle]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-04-18

## Information of the paper
+ Authors: QUN LIN et al. Institute of Mathematics and Statistics, Hanshan Normal University, China
+ Journal name: IEEE ACCESS
+ Published date: 2018-02-27 (Present version : 2018-05-02)
+ [Paper Link](https://ieeexplore.ieee.org/document/8302552)

## Abstract
Identity-based cryptosystems mean that public keys can be directly derived from user identifiers, such as telephone numbers, email addresses, and social insurance number, and so on. So they can simplify key management procedures of certificate-based public key infrastructures and can be used to realize authentication in blockchain. Linearly homomorphic signature schemes allow to perform linear computations on authenticated data. And the correctness of the computation can be publicly verified. Although a series of homomorphic signature schemes have been designed recently, there are few homomorphic signature schemes designed in identity-based cryptography. In this paper, we construct a new ID-based linear homomorphic signature scheme, which avoids the shortcomings of the use of public-key certificates. The scheme is proved secure against existential forgery on adaptively chosen message and ID attack under the random oracle model. The ID-based linearly homomorphic signature schemes can be applied in e-business and cloud computing. Finally, we show how to apply it to realize authentication in blockchain.

## Summary (Korean)
ID-based 암호체계가 certificate-based 암호체계에서의 공개키 관리보다 편리하다. 따라서, 기존에 나와있는 공개키 인증서 사용의 단점을 극복하고, adaptively chosen message and ID 공격으로부터 안전한 ID-based Linearly Homomorphic Signature Scheme을 개발한다. 또한, 블록체인에서 이를 어떻게 적용할 수 있는지 시뮬레이션 한다.

## Details

### 들어가기전에
+ 논문에 수식이 많아 다 긁어오려 했는데 너무 비효율적인것 같아 생략하였습니다. 발표 시 논문과 함께 병행하여 발표하겠습니다.

### I. Introduction
+ 인증서 기반의 암호체계는 공개키 암호체계에 널리 이용되고 있으나 여러가지 이유로 불편하여, Shamir가 1984년 사용자의 ID로부터 직접적으로 공개키를 만들어 낼 수 있는 ID기반 암호체계 개념 소개.
+ 2002년 Johnson논문에서 메시지에 사인할 때, 사인에 쓴 Secret key가 없어도 누구나 서명 검증이 가능한 homomorphic signature 개념 소개, 이후 많은 기술들이 인증서 기반의 암호체계를 이용한 homomorphic signatures 개발.
+ ID 기반의 homomorphic signature 개발은 거의 없고, 그마저도 비효율 적이어서 개발에 의미가 있음.

### II. PRELIMINARIES
#### A. BILINEAR GROUPS (논문 참조)

#### B. BLS SHORT SIGNATURE SCHEME
##### BLS : Boneh, Lynn, and Shacham. 짧은 서명 스킴
+ 1) Key Gen : 개인키, 공개키 생성
+ 2) Sign : 개인키를 이용하여 메시지에 대한 서명 생성
+ 3) Verify : 메시지와 공개키, 서명을 가지고 개인키 없이도 메시지에 대한 서명이 옳음을 검증
 
#### C. ID-BASED SIGNATURE SCHEME
+ 1) Setup : (**INPUT**security parameter), 개인키(x), 공개키 생성
+ 2) Extract : (**INPUT**개인키(x), ID) 를 받아서 private key D_ID 생성
+ 3) Sign : (**INPUT**D_ID, 메시지)로 서명 생성
+ 4) Verify : ID, 메시지, 서명으로 메시지에 대한 서명이 옳음을 검증

+ Existential Unforgeability : 아래의 쿼리를 만족할 수 있는 알고리즘이 존재하지 않다면, 이 스킴에서 ID는 위조될 수 없음.
  + 1) Extract queries
  + 2) Signing queries

#### D. ID-BASED LINEARLY SIGNATURE SCHEME
+ 1) HSetup : (**INPUT**security parameter, 메시지 수 최대 범위 l, 사인 벡터 길이 최대 범위 N), 개인키, 공개키 생성
+ 2) HExtract : (**INPUT**개인키(x), ID) 를 받아서 D_ID 생성
+ 3) HSign : (**INPUT**D_ID, 메시지, file identifier) 로 서명 생성
+ 4) HVerify : ID, v, file identifier, 서명으로 메시지에 대한 서명이 옳음을 검증
+ 5) HEVal : 메시지가 여러개 일 때에 검증 방법

+ Security model (Existential Unforgeability)
  + 1) HExtract queries
  + 2) HSigning queries
  + 3) Derivation queries
  + 4) Reveal queries

### III. THE PROPOSED SCHEME
+ 1) HSetup : (**INPUT**prime number q, generator g, security parameter, H1, H2), x_h = (x_s, 개인키(x)) 와 P_pub_h = (P_pub_s, 공개키(P_pub)) 생성
+ 2) HExtract : (**INPUT**개인키(x)와 ID)를 받아서 D_ID = ( Extract(x_s, ID), H1(ID)^x) 생성
+ 3) Hsign : (**INPUT**file identifier, D_ID, 메시지)로 서명 세트 Q(w, 서명1, 서명2, s) 생성
+ 4) HVerify : ID, file identifier, 메시지, 서명 세트 Q로 서명 검증
+ 5) HEval : 메시지가 여러개 일때의 검증 방법

### IV. PROPOSED SCHEME ANALYSIS
##### Theorem 1
+ 아래의 세가지 조건이 유지될 경우 개발된 ID-based linear homomorphic signature scheme는 chosen-message and ID attack에서도 안전함
  + ID-based signature scheme S=(Setup, Extract, Sign, Verify) 가 위조되지 않음
  + H1, H2가 random oracles
  + CDH 가정 유지

##### Proof
+ 방법 : 역으로 위조된 서명이 있다고 가정한 후 모순을 찾아내어 증명
  + Type 1 : ID-based signature scheme S가 위조된 경우
    + 1) HExtract queries
    + 2) HSigning queries
    + 3) Derivation and Reveal queries
    + 위조하는데에 E의 노력이 든다면, 위조인지 확인하는 데에는 E/2의 노력이 듦.
  + Type 2 : CDH 가정이 잘못된 경우
    + 1) H1-queries
    + 2) H2-queries
    + 3) HExtract queries
    + 4) HSigning queries
    + 5) Derivation and Reveal queries

### V. APPLICATION IN DATA ANALYSIS AND BLOCKCHAIN
+ 블록체인은 분산성 덕분에 IoT 등 많은 곳에서 이용되고 있음. 
  + 한 번 블록에 기록되면 잊혀지지 않는 다는 속성을 이용하여 많은 사람들이 자신의 개인 데이터를 저장하기 위해 이용중임. 
  + 데이터가 많으면 많을 수록 활용이 용이해지나 그만큼 많은 데이터를 관리, 활용하기 위해 제 3자가 개입된 서비스 등을 이용.
  + 결과적으로, 오리지널 데이터와 결과에 대한 인증이 중요해 짐. 

+ 본 논문에서 만든 동형서명스킴이 어떻게 이용되는지 보이고자 함.
  + 이 스킴을 블록체인에 포함시킴
  + 블록체인 및 서명 스킴 사용자는 블록에 올리고자 하는 데이터를 우선 서명하고 네트워크에 올림.
  + 향후 데이터가 필요할 경우 데이터에 접근, 다운로드, 계산

+ 계산 후 사용자는 계산 결과와 계산에 대한 동형서명 집합을 얻을 수 있음.
+ 데이터 제공자임을 블록체인을 통해 보증할 수 있음.

### VI. CONCLUSION
+ ID-based linearly homomorphic signature 개념 소개
+ new ID-based linearly homomorphic signature 개발
  + public-key certificates 의 단점을 극복
  + random oracle model에서 adaptively chosen message and ID 공격에 안전함.
  + e-사업, 클라우드 컴퓨팅, 블록체인 등 분산된 곳에서도 사용 가능.


## Point to note

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
