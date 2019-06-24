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
 이 논문에서는 원격 서버와 패스워드 기반 인증을 수행할 때, Dictionary-attack에 안전한 패스워드 기반 인증 방법을 제안한다. 구체적으로는, 이 논문에서 제안한 cryptographic primitive인 One-Time Key-Based Signature를 동형암호(Homomorphic encryption)를 이용하여 구현한다.

### Background
- 패스워드 기반 인증(password-based authentication)은 개발하기 쉽기 때문에 여전히 많이 사용되고 있다.
- 패스워드는 사용자 인증을 위한 문자열을 일컫고, 패스워드 기반 인증의 등록과 인증 절차는 다음과 같다.
  - 등록 절차에서, 시스템은 각 사용자의 (사용자 ID, 패스워드) 쌍을 저장한다.
  - 인증 절차에서, 시스템은 사용자의 암호를 묻고 저장된 패스워드와 입력된 패스워드를 비교하여 사용자에게 접근(access)을 허용할지 판단한다.

### Attacks, Existing solutions and Limitations
- 일반적인 인증 시스템에서는 패스워드를 관리하는 파일에 패스워드를 그대로 저장하지 않고, cryptographic hash function을 이용해 변환된 결과를 저장한다. 시스템에서는 등록/인증 시, 패스워드를 비교하는 것이 아니라 변환된 결과들을 비교하는 것으로 인증을 수행한다. 이렇게함으로써, 패스워드를 관리하는 파일이 탈취당하더라도 패스워드의 원래 문자열을 알아내기는 매우 어렵게 만드는 보안 조치이다.
- 한편, 사용자가 지정하는 패스워드들의 분포(distribution)는 통계적으로 균일하지 않기 때문에, dictionary attack을 고려할 수 있다. Dictionary attack은 다음과 같이 크게 두가지로 분류한다.
  1. off-line dictionary attack ; 공격자는 자주 사용되는 패스워드들에 대해 미리 hash function을 계산하여 패스워드와 hash된 패스워드 간의 dictionary를 준비한다. 공격자가 시스템으로부터 패스워드를 관리하는 파일을 탈취한 후, 탈취한 파일의 hash를 value로 가지는 key를 dictionary에서 검색하는 것으로 패스워드 문자열 복구를 시도한다. 
  2. on-line dictionary attack ; 공격자는 공격 대상인 hash된 패스워드를 획득한 후에, dictionary를 준비한다. 이 시점에서는 hash에 적용된 salt가 공격자에게도 available하기에, 획득한 salt를 적용하여 hash된 패스워드와 자주 사용되는 패스워드들 간의 dictionary를 생성한다. 
- 패스워드로 가능한 문자열 전체 모집단 P라고 하고 P의 분포를 D(P)라고 하자,
  임의의 패스워드 p\inP에 대해 hash function h을 적용한 결과를 h(p)라고 하고 hash function h의 결과의 모집단을 H라고 하자.
  사용자가 지정하는 패스워드들의 분포. 즉, D(P)는 균일하지 않다. 그런데 만약 hash function이 일대일 대응에 가깝다면, D(H)의 분포는 D(P)와 동일하기 때문에, hash function을 적용한 패스워드에 대해서도 dictionary attack을 고려할 수 있다. (Off-line dictionary attack)
- Off-line dictionary attack을 막기 위해, hash에 random한 salt를 추가한다. => 하지만, salt가 고정된 후에 dictionary를 생성하면 salt가 useless하다. (On-line dictionary attack)

### Proposed method
- 동형암호를 이용하여 One-Time Key-Based Signature를 구현하여서 dictionary attack에 안전한 패스워드 인증 방법을 제안한다.
- 동형암호로 One-Time Key-Based Signature를 구현하였을때 패스워드 인코딩 방법(논문의 fig 2, fig 3)

### Proposed cryptographic primitive
- Proposed method의 registration phase에서 signature를 생성한 후에, "Remove Sk(sig)"를 수행하는, 즉, private key를 삭제하는 방식.
- private key를 삭제하는 것은 device가 더이상 signature를 생성할 수 없도록 하지만, public key가 삭제되지 않는한 signature verification은 가능하다. (One-Time Key) 
=> dictionary attack은 hash function의 결과와 패스워드의 원본 문자열의 매핑을 가지고 하는 공격이다. 하지만, 이 논문에서 제안한 방법은 hash function과 같이 일대일 대응이 아니라 (on-line에서는 salt가 고정되므로 그 이후로는 일대일 대응이라고 볼수 있음) 서명 검증만을 수행할 수 있는 암호문 쌍이 유지된다. 이 암호문은 key가 없으면 복호화를 할수 없고 암호문의 분포가 균일하게 되어서, 암호문을 만들수 있는 방법이 없으므로 dictionary attack이 불가능하다.

### Points to note
- One-Time Key-Based Signature의 동작 원리
- One-Time Key-Based Signature를 구현하기 위해 동형암호가 적용된 이유
- 동형암호로 One-Time Key-Based Signature를 구현하였을때 패스워드 인코딩 방법

### Discussion
- One-Time Key-Based Signature에 대한 future work

{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
