---
title: 1st UCSLab Morning Seminar
date: 2019-04-15 00:00:00 Z
description: Notificaion of 1st UCSLab Morning Seminar (on 2019-04-18) 
card_title: 1st Morning Seminar
card_teaser: with 5 presentations on 2019-04-18.
card_position: 1
icon: fa-bullhorn
categories: [seminars,04-18-2019-morning-seminar,notification]
sidebar: morning-seminar
layout: default
slug: ms-notification-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Date
2019-04-18

## Presenters
+ Jong-Hyuk Im (임종혁)
+ Hee-Yong Kwon (권희용)
+ Tae-Hyun Kim (김태현)
+ Sung-Yun Jeon (전성윤)
+ Ye-Byoul Son (손예별)

## Presentations

### Session 1: [The Rewards and Costs of Stronger Passwords in a University: Linking Password Lifetime to Strength](https://inhaucs.github.io/seminars/04-18-2019-morning-seminar/presentation/ms-presentation-jh-apr-18-2019.html)

+ Jong-Hyuk Im (임종혁)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/becker)
+ Authors: Ingolf Becker, Simon Parkin, and M. Angela Sasse, University College London
+ Conference name: 27th USENIX Security Symposium (USENIX Security 18)
+ Published date: 2018-08-15
+ [Paper file](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-becker.pdf)

#### Abstract
We present an opportunistic study of the impact of a new password policy in a university with 100,000 staff and students. The goal of the IT staff who conceived the policy was to encourage stronger passwords by varying password lifetime according to password strength. Strength was measured through Shannon entropy (acknowledged to be a poor measure of password strength by the academic community, but still widely used in practice). When users change their password, a password meter informs them of the lifetime of their new password, which may vary from 100 days (50 bits of entropy) to 350 days (120 bits of entropy).
We analysed data of nearly 200,000 password changes and 115,000 resets of passwords that were forgotten/expired over a period of 14 months. The new policy took over 100 days to gain traction, but after that, average entropy rose steadily. After another 12 months, the average password lifetime increased from 146 days (63 bits) to 170 days (70 bits).
We also found that passwords with more than 300 days of lifetime are 4 times as likely to be reset as passwords of 100 days of lifetime. Users who reset their password more than once per year (27% of users) choose passwords with over 10 days fewer lifetime, and while they also respond to the policy, maintain this deficit.
We conclude that linking password lifetime to strength at the point of password creation is a viable strategy for encouraging users to choose stronger passwords (at least when measured by Shannon entropy).


### Session 2: [Paper-2 title](url)

+ Gil-Dong (길동)

#### Information of the paper [(Link)](url)
+ Authors: 저자들이 옵니다.
+ Conference name: 저널인 경우에는 Journal name
+ Published date: 컨퍼런스의 경우에는 발표 일자 또는 프로시딩 공개 일자
+ [Paper Link](https://ucs.inha.ac.kr)

#### Abstract
초록이 여기에 옵니다.

## Supplementary Data
보조자료가 필요한 경우 또는 해당 회차 세미나완 관련된 무언가..?



{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
