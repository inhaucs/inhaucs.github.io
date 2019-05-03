---
title: Session 2. Simple Password-Hardened Encryption Services
date: 2019-05-03 00:00:00 Z
description: Simple Password-Hardened Encryption Services
card_title: Session 2
card_teaser: Simple Password-Hardened Encryption Services
card_position: 2
icon: fa-server
categories: [seminars,05-06-2019-morning-seminar,presentation]
tags: [USENIX, 2018, USENIX2018, Encryption, Password]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-may-06-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-05-06

## [Simple Password-Hardened Encryption Services](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-jh-may-06-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/lai)
+ Authors: Russell W. F. Lai and Christoph Egger (Friedrich-Alexander University Erlangen-Nuremberg); Manuel Reinert (Saarland University); Sherman S. M. Chow (Chinese University of Hong Kong); Matteo Maffei (Vienna University of Technology); Dominique Schröder( Friedrich-Alexander University Erlangen-Nuremberg)
+ Conference name: USENIX Security 2018
+ Published date: 2018-08-17
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-lai.pdf)


### Abstract
Passwords and access control remain the popular choice for protecting sensitive data stored online, despite their well-known vulnerability to brute-force attacks. 
A natural solution is to use encryption. Although standard practices of using encryption somewhat alleviate the problem, decryption is often needed for utility, and keeping the decryption key within reach is obviously dangerous. 
To address this seemingly unavoidable problem in data security, we propose password-hardened encryption (PHE). 
With the help of an external crypto server, a service provider can recover the user data encrypted by PHE only when an end user supplied a correct password. 
PHE inherits the security features of password-hardening (Usenix Security ’15), adding protection for the user data. 
In particular, the crypto server does not learn any information about any user data. 
More importantly, both the crypto server and the service provider can rotate their secret keys, a proactive security mechanism mandated by the Payment Card Industry Data Security Standard (PCI DSS). 
We build an extremely simple password-hardened encryption scheme. Compared with the state-of-the-art password-hardening scheme (Usenix Security ’17), our scheme only uses minimal number-theoretic operations and is, therefore, 30% - 50% more efficient. 
In fact, our extensive experimental evaluation demonstrates that our scheme can handle more than 525 encryption and (successful) decryption requests per second per core, which shows that it is lightweight and readily deployable in large-scale systems. 
Regarding security, our scheme also achieves a stronger soundness property, which puts less trust on the good behavior of the crypto server.


## Summary (Korean)


## Details
### Contents of the paper

### Points to note
+

## Discussion
+

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
