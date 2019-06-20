---
title: Session 2. Pairing-Friendly Elliptic Curves of Prime Order
date: 2019-06-20 00:00:00 Z
description: Pairing-Friendly Elliptic Curves of Prime Order
card_title: Session 2
card_teaser: Pairing-Friendly Elliptic Curves of Prime Order
card_position: 2
icon: fa-server
categories: [seminars,06-20-2019-morning-seminar,presentation]
tags: [Pairings, Barreto-Naehrig curves, ate pairing, MCL, BLS]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-june-20-2019
permalink: /:categories/:slug.html
---


{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-06-20

## [Pairing-Friendly Elliptic Curves of Prime Order](https://inhaucs.github.io/seminars/06-20-2019-morning-seminar/presentation/ms-presentation-sy-june-20-2019.html)

### Information of the paper [(Link)](https://dl.acm.org/citation.cfm?id=2180571)
+ Authors: Paulo S. L. M. Barreto1 (Escola Polit´ecnica, Universidade de S˜ao Paulo),  Michael Naehrig (Lehrstuhl f¨ur Theoretische Informationstechnik, Rheinisch-Westf¨alische Technische Hochschule Aachen.)
+ Published date: 2005-08-11
+ [Paper Link](https://eprint.iacr.org/2005/133.pdf)


### Abstract
Previously known techniques to construct pairing-friendly curves of prime or near-prime order are restricted to embedding degree k <= 6. More general methods produce curves over Fp where the bit length of p is often twice as large as that of the order r of the subgroup with embedding degree k; the best published results achieve ρ ≡ log(p)/ log(r) ∼ 5/4. In this paper we make the first step towards
surpassing these limitations by describing a method to construct elliptic curves of prime order and embedding degree k = 12. The new curves lead to very efficient implementation: non-pairing cryptosystem operations only need Fp and Fp2 arithmetic, and pairing values can be compressed to one sixth of their length in a way compatible with point reduction techniques. We also discuss the role of large CM discriminants D to minimize ρ; in particular, for embedding degree k = 2q where q is prime we show that the ability to handle log(D)/ log(r) ∼ (q − 3)/(q − 1) enables building curves with ρ ∼ q/(q − 1).

### Weil pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062001.PNG" legend="Weil pairing miller algorithm" %}
### Tate pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062002.PNG" legend="Tate pairing miller algorithm" %}

+ All the fast algorithms to compute the Weil and Tate pairing on elliptic curves are based on Miller's algorithm.
### [Optimal pairing miller algorithm](https://ieeexplore.ieee.org/document/5361495)
{% include articles/figure.html url="/assets/img/byoul/2019/2019062003.PNG" legend="Optimal pairing miller algorithm" %}

### bn256 Optimal ate pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062004.PNG" legend="bn256 Optimal ate pairing miller algorithm" %}

### bn256 pairing code
[Basic bn256 crypto code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)
[go-ethereum bn256 code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)

#### bn256 pairing code
{% include articles/figure.html url="/assets/img/byoul/2019/2019062005.PNG" legend="bn256 optimalate pairing code" %}

#### miller code
{% include articles/figure.html url="/assets/img/byoul/2019/2019062006.PNG" legend="miller code" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062007.PNG" legend="miller code(cont.)" %}

#### finalexponentation code
{% include articles/figure.html url="/assets/img/byoul/2019/2019062008.PNG" legend="finalexponentation code" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062008.PNG" legend="finalexponentation code(cont.)" %}

### Points to note


## Discussion



{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
