---
title: Session 3. Weil pairing
date: 2019-06-19 00:00:00 Z
description: Weil pairing
card_title: Session 3
card_teaser: Weil pairing
card_position: 3
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
+ 2019-06-27

## [New software speed records for cryptographic pairings](https://inhaucs.github.io/seminars/06-20-2019-morning-seminar/presentation/ms-presentation-yb-june-20-2019.html)

### Information of the paper [(Link)](http://cryptojedi.org/papers/dclxvi-20100714.pdf)
+ Authors: Michael Naehrig (Microsoft Research), Ruben Niederhagen (National Taiwan University), Peter Schwabe(Technische Universiteit Eindhoven)
+ Published date: 2010-07-14
+ [Paper Link](http://cryptojedi.org/papers/dclxvi-20100714.pdf)


### Abstract
This paper presents new software speed records for the computation of cryptographic pairings. More specifically, we present details of an implementation which computes the optimal ate pairing on a 256- bit Barreto-Naehrig curve in only 4,379,912 cycles on one core of an Intel Core 2 Quad Q9550 processor. This speed is achieved by combining 1.) state-of-the-art high-level optimization techniques, 2.) a new representation of elements in the underlying finite fields which makes use of the special modulus arising from the Barreto-Naehrig curve construction, and 3.) implementing arithmetic in this representation using the double-precision floating-point SIMD instructions of the AMD64 architecture.


### Weil pairing miller algorithm
+ Weil pairing equation
{% include articles/figure.html url="/assets/img/byoul/2019/2019062601.png" legend="Weil pairing equation" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062602.png" legend="Weil pairing divisor" width="50%" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062603.png" legend="Weil pairing divisor addition" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062604.png" legend="Weil pairing divisor doubling" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062605.png" legend="Weil pairing f1value" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062606.png" legend="Weil pairing f1function" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062607.png" legend="Weil pairing f1Qfunction" width="50%"%}

+ Weil pairing pseudocode
{% include articles/figure.html url="/assets/img/byoul/2019/2019062001.png" legend="Weil pairing miller algorithm" %}

### Tate pairing miller algorithm

+ Tate pairing equation
{% include articles/figure.html url="/assets/img/byoul/2019/2019062608.png" legend="Tate pairing equation" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062609.png" legend="Tate pairing divisor" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062610.png" legend="Tate pairing additionr" width="50%"%}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062611.png" legend="Tate pairing doubling" width="50%"%}

+ Tate pairing pseudocode
{% include articles/figure.html url="/assets/img/byoul/2019/2019062002.png" legend="Tate pairing miller algorithm" %}


### [Optimal pairing miller algorithm](https://ieeexplore.ieee.org/document/5361495)
+ All the fast algorithms to compute the Weil and Tate pairing on elliptic curves are based on Miller's algorithm.
+ The ate pairing [15,17] and its variations [20,21,28] are simply optimized versions of the Tate pairing when restricted to the eigenspaces of Frobenius.

### bn256 Optimal ate pairing miller algorithm
{% include articles/figure.html url="/assets/img/byoul/2019/2019062004.png" legend="bn256 Optimal ate pairing miller algorithm" %}

### [Weil pairing code example](https://github.com/elliptic-shiho/ecpy/blob/master/ecpy/elliptic_curve/pairing.py)
{% include articles/figure.html url="/assets/img/byoul/2019/2019062612.png" legend="weil_pairing" %}
{% include articles/figure.html url="/assets/img/byoul/2019/2019062613.png" legend="weil_pairing_miller" %}

**20190627 발표**

{% include articles/figure.html url="/assets/img/byoul/2019/2019062614.png" legend="weil_pairing_line_coeff" %}

### bn256 pairing code
+ [Basic bn256 crypto code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)
+ [go-ethereum bn256 code](https://github.com/ethereum/go-ethereum/tree/master/crypto/bn256/cloudflare)
{% include articles/figure.html url="/assets/img/byoul/2019/2019062005.png" legend="bn256 pairing miller code" %}

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
