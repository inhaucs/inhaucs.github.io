---
title: "Session 3. Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
date: 2019-04-17 00:00:00 Z
description: "Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
card_title: Session 3
card_teaser: "Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
card_position: 3
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
tags: [RSA, 2019, RSA2019, CT-RSA, CT-RSA2019, functional encryption, FE, function-hiding, orthogonality]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-04-18

## Information of the paper
+ Authors: Manuel Barbosa(INESC TEC and FCUP, Portugal), Dario Catalano(Universit`a di Catania, Italy), Azam Soleimanian(Kharazmi University of Tehran, Iran and École Normale Supérieure, Paris, France), and Bogdan Warinschi(University of Bristol, Bristol, UK)
+ Conference name: The Cryptographers' Track at the RSA Conference 2019
+ Published date: 2019-03-04
+ [Paper Link](https://doi.org/10.1007/978-3-030-12612-4_7)

## Abstract
We construct functional encryption (FE) schemes for the orthogonality (OFE) relation where each ciphertext encrypts some vector ***x*** and each decryption key, associated to some vector ***y***, allows to determine if ***x*** is orthogonal to ***y*** or not. Motivated by compelling applications, we aim at schemes which are function hidding, i.e. ***y*** is not leaked.
Our main contribution are two such schemes, both rooted in existing constructions of FE for inner products (IPFE), i.e., where decryption keys reveal the inner product of ***x*** and ***y***. The first construction builds upon the very efficient IPFE by Kim et al. (SCN 2018) but just like the original scheme its security holds in the generic group model (GGM). The second scheme builds on recent developments in the construction of efficient IPFE schemes in the standard model and extends the work of Wee (TCC 2017) in leveraging these results for the construction of FE for Boolean functions. Conceptually, both our constructions can be seen as further evidence that shutting down leakage from inner product values to only a single bit for the orthogonality relation can be done with little overhead, not only in the GGM, but also in the standard model.
We discuss potential applications of our constructions to secure databases and provide efficiency benchmarks. Our implementation shows that the first scheme is extremely fast and ready to be deployed in practical applications.

## Summary (Korean)
이 논문은 기존의 내적 기반의 암호(Inner-Product Functional Encryption, IPFE) 스킴들을 근간으로 확장한 연구이다. 이 연구에서는 내적(Inner-Product)의 값이 아닌 직교성(Orthogonality) 여부를 결과로 얻는 스킴(functional encryption for orthogonality relation, OFE)들을 설계하였고 실험의 결과를 제시한다. 크게 두가지 스킴을 설계하였는데, 하나는 Kim __et al__. 이 SCN 2018에서 제안한 함수은닉을 지원하는 내적 암호(Function Hiding IPFE, FH-IPFE)를 black-box 로써 직교성을 구하는 스킴으로 구성하는 방법이고, 다른 하나는, 직전 방법과 같이 제네릭 그룹 모델(Generic Group Model, GGM)을 활용하는 것이 아니라 standard model을 사용하는 방법이다. 연구의 결과에 따르면, 첫번째 스킴은 실용적인 수준의 성능을 가진다.

## Details
### Contents of the paper
#### Research questions
+ **(RQ1)** 내적 값으로 인한 정보 누수(논문의 표현으로는 the excessive leakage)를 막기 위해 IPFE를 black-box 로 활용하여 OFE를 설계할 수 있는가?
+ **(RQ2)** OFE를 설계하는 데에 Lin [ref] 와 Wee [ref] 의 방법들 조합하여 적용할 수 있는가?

#### RQ1: 내적 값으로 인한 정보 누수(논문의 표현으로는 the excessive leakage)를 막기 위해 IPFE를 black-box 로 활용하여 OFE를 설계할 수 있는가?

#### RQ2: OFE를 설계하는 데에 Lin [ref] 와 Wee [ref] 의 방법들 조합하여 적용할 수 있는가?

#### Conclusion
작성중

### Points to note
작성중

[ref]: <url> "description"

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
