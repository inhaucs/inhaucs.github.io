---
title: Session 1. Barreto-Naehrig(BN)256 curve Pairing
date: 2019-06-19 00:00:00 Z
description: Barreto-Naehrig(BN)256 curve Pairing
card_title: Session 1
card_teaser: Barreto-Naehrig(BN)256 curve Pairing
card_position: 1
icon: fa-server
categories: [seminars,06-20-2019-morning-seminar,presentation, seminars,06-27-2019-morning-seminar]
tags: [Pairings, Barreto-Naehrig curves, ate pairing, AMD64 architecture, modular arithmetic, SIMD floating-point instructions]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-june-20-2019, ms-presentation-yb-june-27-2019
permalink: /:categories/:slug.html
---


{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-06-20

## [New software speed records for cryptographic pairings](https://inhaucs.github.io/seminars/06-20-2019-morning-seminar/presentation/ms-presentation-yb-june-20-2019.html)

### Information of the paper [(Link)](http://cryptojedi.org/papers/dclxvi-20100714.pdf)
+ Authors: Michael Naehrig (Microsoft Research), Ruben Niederhagen (National Taiwan University), Peter Schwabe(Technische Universiteit Eindhoven)
+ Published date: 2010-07-14
+ [Paper Link](http://cryptojedi.org/papers/dclxvi-20100714.pdf)


### Abstract
This paper presents new software speed records for the computation of cryptographic pairings. More specifically, we present details of an implementation which computes the optimal ate pairing on a 256- bit Barreto-Naehrig curve in only 4,379,912 cycles on one core of an Intel Core 2 Quad Q9550 processor. This speed is achieved by combining 1.) state-of-the-art high-level optimization techniques, 2.) a new representation of elements in the underlying finite fields which makes use of the special modulus arising from the Barreto-Naehrig curve construction, and 3.) implementing arithmetic in this representation using the double-precision floating-point SIMD instructions of the AMD64 architecture.


### Weil pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062001.png" legend="Weil pairing miller algorithm" %}
### Tate pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062002.png" legend="Tate pairing miller algorithm" %}

+ All the fast algorithms to compute the Weil and Tate pairing on elliptic curves are based on Miller's algorithm.
### [Optimal pairing miller algorithm](https://ieeexplore.ieee.org/document/5361495)


{% include articles/figure.html url="/assets/img/byoul/2019/2019062003.png" legend="Optimal pairing miller algorithm" %}

### bn256 Optimal ate pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062004.png" legend="bn256 Optimal ate pairing miller algorithm" %}

### bn256 pairing code
+ [Basic bn256 crypto code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)
+ [go-ethereum bn256 code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)


#### pairing code
{% include articles/figure.html url="/assets/img/byoul/2019/2019062006.png" legend="pairing code" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062007.png" legend="pairing code(cont.)" %}

#### finalexponentation code
{% include articles/figure.html url="/assets/img/byoul/2019/2019062008.png" legend="finalexponentation code" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062008.png" legend="finalexponentation code(cont.)" %}



### Points to note


## Discussion



{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
