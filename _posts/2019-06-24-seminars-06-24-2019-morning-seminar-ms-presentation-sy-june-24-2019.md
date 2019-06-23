---
title: Session 1. Password Authentication Using One-Time Key-Based Signature and Homomorphic Encryption
date: 2019-06-24 00:00:00 Z
description: Password Authentication Using One-Time Key-Based Signature and Homomorphic Encryption
card_title: Session 1
card_teaser: Password Authentication Using One-Time Key-Based Signature and Homomorphic Encryption
card_position: 1
icon: fa-server
categories: [seminars,06-24-2019-morning-seminar,presentation]
tags: [BWCCA, 2016, BWCCA2016, Password, Password Authentication, Authentication, OTP, One Time Password, HE, Homomorphic Encryption]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-june-24-2019
permalink: /:categories/:slug.html
---

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-06-24

## [Password Authentication Using One-Time Key-Based Signature and Homomorphic Encryption](https://inhaucs.github.io/seminars/06-24-2019-morning-seminar/presentation/ms-presentation-sy-june-24-2019.html)

### Information of the paper [(Link)](https://link.springer.com/chapter/10.1007/978-3-319-49106-6_45)
+ Authors: Jong-Hyuk Im; Mun-Kyu Lee (Inha University)
+ **Conference** name: International Conference on Broadband and Wireless Computing, Communication and Applications
+ Published date: 2016-10-22
+ [Paper Link](https://link.springer.com/chapter/10.1007/978-3-319-49106-6_45)

### Abstract
User authentication is a process for a system to verify the identity of a claimed user and to give access permission. Although there are many other authentication methods such as biometrics and physical tokens, passwords are still being used in many applications due to easy deployment. To enhance the security against possible attacks such as an off-line dictionary attack, passwords are usually stored in a hashed form using a random nonce called a salt. However, this does not completely solve the security issue. In this paper, we propose a new password-based authentication method using homomorphic encryption where a password is stored in a remote server in an encrypted form and an input password is compared with the stored one on the encrypted domain. For this purpose, we also propose a new cryptographic primitive called one-time private key-based digital signature.

### Summary (Korean)

### Background
- 패스워드 기반 인증(password-based authentication)은 개발하기 쉽기 때문에 여전히 많이 사용되고 있음.
- 패스워드는 사용자 인증을 위한 문자열이고, 등록과 인증은 다음과 같음.
  - 등록 절차에서는, ...
  - 인증 절차에서는, ...

### Attacks, Existing solutions and Limitations
- 일반적인 인증 시스템에서는 패스워드를 관리하는 파일에 패스워드를 그대로 저장하지 않고, cryptographic hash function을 이용해 변환된 결과를 저장함. 시스템에서는 등록/인증 시, 패스워드를 비교하는 것이 아니라 변환된 결과들을 비교하는 것으로 인증 수행. 이렇게함으로써, 패스워드를 관리하는 파일이 탈취당하더라도 패스워드의 원래 문자열을 알아내기는 매우 어렵게 만드는 보안 조치.
- 한편, 사용자가 지정하는 패스워드들의 분포(distribution)는 통계적으로 균일하지 않기 때문에, dictionary attack을 고려할 수 있음.
- Dictionary attack은 다음과 같이 크게 두가지로 분류.
  1. off-line dictionary attack ;
  2. on-line dictionary attack ; 
- 패스워드에 hash function을 적용한다고 해도, hash function이 1대1 대응에 가깝다면, 여전히 변환된 패스워드들의 분포도 균일하지 않아서, dictionary attack을 고려할 수 있음. (Off-line dictionary attack)
- Off-line dictionary attack을 막기 위해, ... => 하지만, ... (On-line dictionary attack)
- On-line dictionary attack을 막기 위해, ... => 하지만, ...

### Proposed method
- 동형암호를 이용하여 One-Time Key-Based Signature를 구현

### Proposed cryptographic primitive
- One-Time Key-Based Signature

### Points to note
- One-Time Key-Based Signature의 동작 원리
- One-Time Key-Based Signature를 구현하기 위해 동형암호가 적용된 이유

### Discussion
- One-Time Key-Based Signature에 대한 future work

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
