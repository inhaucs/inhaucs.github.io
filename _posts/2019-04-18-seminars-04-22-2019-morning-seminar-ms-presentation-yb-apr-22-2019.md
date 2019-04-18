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
ID-based 암호체계가 certificate-based 암호체계에서의 공개키 관리보다 편리하다. 따라서, 기존에 나와있는 공개키 인증서 사용의 단점을 극복하고, adaptively chosen message and ID 공격으로부터 안전한 ID-based Linearly Homomorphic Signature Scheme을 개발한다. 또한, 블록체인에서 이를 어떻게 적용할 수 있는지 시뮬레이션 한다.

## Details

### I. Introduction

### II. PRELIMINARIES
#### A. BILINEAR GROUPS (논문 참조)
#### B. BLS SHORT SIGNATURE SCHEME
##### BLS : Boneh, Lynn, and Shacham. 짧은 서명 스킴 
#### C. ID-BASED SIGNATURE SCHEME
#### D. ID-BASED LINEARLY SIGNATURE SCHEME

### III. THE PROPOSED SCHEME

### IV. PROPOSED SCHEME ANALYSIS
##### Theorem 1
##### Proof


### V. APPLICATION IN DATA ANALYSIS AND BLOCKCHAIN
### VI. CONCLUSION


## Point to note

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
