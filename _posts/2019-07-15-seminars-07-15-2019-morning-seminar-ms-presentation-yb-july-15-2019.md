---
title: Session 1. Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
date: 2019-07-15 00:00:00 Z
description: Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
card_title: Session 1
card_teaser: Redactable Blockchain – or – Rewriting History in Bitcoin and Friends
card_position: 1
icon: fa-server
categories: [seminars,07-15-2019-morning-seminar,presentation]
tags: [EUROSNP, 2017, EUROSNP2017, Blockchain, Bitcoin, Redactable Blockchain, Chameleon hash]
sidebar: morning-seminar
layout: default
slug: ms-presentation-yb-july-15-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Ye-Byoul Son (손예별)
+ 2019-07-15

## [Redactable Blockchain – or – Rewriting History in Bitcoin and Friends](https://inhaucs.github.io/seminars/07-15-2019-morning-seminar/presentation/ms-presentation-yb-july-15-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/7961975)
+ Authors: Giuseppe Ateniese, Bernardo Magri, Daniele Venturi, Ewerton R. Andrade 
(Stevens Institute of Technology(USA), Friedrich-Alexander University(Germany), Sapienza University of Rome(Italy), University of S˜ao Paulo(Brazil))
+ Journal name: IEEE European Symposium on Security and Privacy
+ Published date: 2017-04-26
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7961975)
+ [Full version Link](https://eprint.iacr.org/2016/757.pdf)

### Abstract
We put forward a new framework that makes it possible to re-write or compress the content of any number of blocks in decentralized services exploiting the blockchain technology. As we argue, there are several reasons to prefer an editable blockchain, spanning from the necessity to remove inappropriate content and the possibility to support applications requiring re-writable storage, to “the right to be forgotten.” 
Our approach generically leverages so-called chameleon hash functions (Krawczyk and Rabin, NDSS ’00), which allow determining hash collisions efficiently, given a secret trapdoor information. We detail how to integrate a chameleon hash function in virtually any blockchain-based technology, for both cases where the power of redacting the blockchain content is in the hands of a single trusted entity and where such a capability is distributed among several distrustful parties (as is the case with Bitcoin). 
We also report on a proof-of-concept implementation of a redactable blockchain, building on top of Nakamoto’s Bitcoin core. The prototype only requires minimal changes to the way current client software interprets the information stored in the blockchain and to the current blockchain, block, or transaction structures. Moreover, our experiments show that the overhead imposed by a redactable blockchain is small compared to the case of an immutable one.

 
## Summary (Korean)
+ 존재하는 비트코인과 같은 블록체인들은 블록에 한번 기록되면 수정할 수 없다는 특징이 있음. 
+ 그러나 이런 점은 실제 세계에서는 적합하지 않은 경우가 많음. 따라서, 블록 수정이 필요함.
+ 카멜레온 해시를 이용한 블록 수정, 삭제, 삽입, 압축이 가능한 블록체인 프레임워크 개발.


## Details
### Blockchain Basics

### Chameleon hash
### SABRE Relay Network

### Experiments


### DISCUSSIONS


### Points to note


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
