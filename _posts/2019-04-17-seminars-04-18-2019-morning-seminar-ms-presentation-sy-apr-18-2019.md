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
이 논문은 기존의 내적 기반의 암호(Inner-Product Functional Encryption, IPFE) 스킴들을 근간으로 확장한 연구이다. 이 연구에서는 내적(Inner-Product)의 값이 아닌 직교성(Orthogonality) 여부를 결과로 얻는 스킴(functional encryption for orthogonality relation, OFE)들을 설계하였고 실험의 결과를 제시한다. 크게 두가지 스킴을 설계하였는데, 하나는 Kim __et al__. 이 SCN 2018에서 제안한 함수은닉을 지원하는 내적 암호(Function Hiding IPFE, FH-IPFE)를 black-box로써 직교성을 구하는 스킴으로 구성하는 방법이고, 다른 하나는, 직전 방법과 같이 제네릭 그룹 모델(Generic Group Model, GGM)을 활용하는 것이 아니라 standard model을 사용하는 방법이다. 연구의 결과에 따르면, 첫번째 스킴은 실용적인 수준의 성능을 가진다.

## Details
### Notice for this seminar
+ RQ2와 Implementation and Performance Evaluation에 대한 내용을 마치지 못했습니다. 다음 세미나 앞시간을 활용하도록 양해를 구하고자 합니다.

### Contents of the paper
#### Research questions
+ **(RQ1)** 내적 값으로 인한 정보 누수(논문의 표현으로는 the excessive leakage)를 막기 위해 IPFE를 black-box로 활용하여 OFE를 설계할 수 있는가?
+ **(RQ2)** OFE를 설계하는 데에 Lin [Lin17] 와 Wee [Wee17] 의 방법들 조합하여 적용할 수 있는가?

#### RQ1: 내적 값으로 인한 정보 누수(논문의 표현으로는 the excessive leakage)를 막기 위해 IPFE를 black-box로 활용하여 OFE를 설계할 수 있는가?
이 질문에 대한 연구 시작점은 Kim __et al__ 이.[KLM+16] 에서 제안한 FH-IPFE이다. FH-IPFE를 black-box로써 활용하여 FH-OFE를 다음과 같이 구성한다.
{% include articles/figure.html url="/assets/img/seongyun/2019/04-18-2019-ms-session3-fig1.png" legend="a contruction in the generic group model" %}
기존에 알고 있던 FH-IPFE와 두드러지게 달라진 점은 sk, ct의 형태라고 할수 있다. FH-IPFE의 sk=(K1, K2)와 ct=(C1,C2)에서 첫번째 원소가 각각 없어졌기 때문에, 크기는 n+1이 아니라 n이다. 또, 복호화 단계에서 내적 값을 얻기 위해 이산 로그 문제를 해결하는 것이 아니라, 계산의 결과가 GT 상에서 1인 결과라면 직교라고 판단하고, 이외의 값인 경우 직교가 아니라고 판단한다. 이 스킴에 대한 Security 증명은 FH-IPE와 거의 비슷하다. 

#### RQ2: OFE를 설계하는 데에 Lin [Lin17] 와 Wee [Wee17] 의 방법들을 조합하여 적용할 수 있는가?
(Lin [Lin17] 와 Wee [Wee17]의 방법 각각 소개.)
(이 논문의 조합 방법 소개.)
(Correctness 와 Security proof 설명.)

#### Implementation and Performance Evaluation
(구현 환경과 관련 정보들 수집하여 쓰기.)
(성능 평가와 성능 측정 방법. 다른 방법과 비교.)

#### Applications
+ Privacy-preserving subset relation
  + Sorting algorithm
  + Searchable Encryption
+ Range Queries
+ Access Control

### Points to note
+ Kim __et al__ 의.논문[KLM+16]에서 제안한 FH-IPFE을 활용해서 실용적인 FH-OFE를 구성했다. 물론, 이 첫번째 FH-OFE는 FH-IPFE와 같이, its security holds in the GGM 이다. 첫번째 FH-OFE의 장점은 간단히 구성가능하고 실용적인 성능을 가진다는 것이다.
+ 두번째 FH-OFE의 security는 GGM이 아니라 standard model에 hold 한다. security 의 hold 는 바꾸었지만, 성능은 매우 떨어졌다. 
+ 내적 값(inner product values)을 드러내는 것보다 직교 관계(orthogonality relation)에 있는지 여부만 0 또는 1 (sigle bit)만 드러냄으로써 발생가능한 정보 누수를 차단할수 있고, 이것이 GGM 뿐만 아니라 standard model 에 대해서도 overhead가 거의 없이 가능하다는 것을 보였다.

[Lin17]: <https://doi.org/10.1007/978-3-319-63688-7_20> "Lin, H.: Indistinguishability obfuscation from SXDH on 5-linear maps and locality-5 prgs. Advances in Cryptology - CRYPTO 2017. Proceedings, Part I, pp. 599–629 (2017)"
[Wee17]: <https://doi.org/10.1007/978-3-319-70500-2_8> "Wee, H.: Attribute-hiding predicate encryption in bilinear groups, revisited. Theory of Cryptography - TCC 2017. Proceedings, Part I, pp. 206–233 (2017)"
[KLM+16]: <https://eprint.iacr.org/2016/440.pdf> "Kim, S., Lewi, K., Mandal, A., Montgomery, H.W., Roy, A.,Wu, D.J.: Function-hiding inner product encryption is practical. IACR Cryptology ePrint Archive 2016, 440 (2016)"

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
