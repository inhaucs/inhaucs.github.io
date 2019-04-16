---
title: Session 1. The Rewards and Costs of Stronger Passwords in a University Linking Password Lifetime to Strength
date: 2019-04-16 00:00:00 Z
description: test about how to post into this site. 
card_title: Session 1
card_teaser: The Rewards and Costs of Stronger Passwords in a University Linking Password Lifetime to Strength
card_position: 1
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-04-18

## Information of the paper
+ Authors: Ingolf Becker, Simon Parkin, and M. Angela Sasse, University College London
+ Conference name: 27th USENIX Security Symposium (USENIX Security 18)
+ Published date: 2018-08-15
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-becker.pdf)

## Abstract
We present an opportunistic study of the impact of a new password policy in a university with 100,000 staff and students. The goal of the IT staff who conceived the policy was to encourage stronger passwords by varying password lifetime according to password strength. Strength was measured through Shannon entropy (acknowledged to be a poor measure of password strength by the academic community, but still widely used in practice). When users change their password, a password meter informs them of the lifetime of their new password, which may vary from 100 days (50 bits of entropy) to 350 days (120 bits of entropy).
We analysed data of nearly 200,000 password changes and 115,000 resets of passwords that were forgotten/expired over a period of 14 months. The new policy took over 100 days to gain traction, but after that, average entropy rose steadily. After another 12 months, the average password lifetime increased from 146 days (63 bits) to 170 days (70 bits).
We also found that passwords with more than 300 days of lifetime are 4 times as likely to be reset as passwords of 100 days of lifetime. Users who reset their password more than once per year (27% of users) choose passwords with over 10 days fewer lifetime, and while they also respond to the policy, maintain this deficit.
We conclude that linking password lifetime to strength at the point of password creation is a viable strategy for encouraging users to choose stronger passwords (at least when measured by Shannon entropy).

## Summary (Korean)
"Stronger password longer lifetime"이라는 주제로 대학에서 Password 수명이 강도에 미치는 영향을 대규모 실험을 통해 확인한 논문이다. 본 논문에서는 16개월 이상 실제 100,000명의 실제 사용자 (대학 관계자)에 대한 실험을 수행하였으며, 로그 데이터를 분석하였다. 

기존의 연구들은 대부분 오래된 암호일수록 손상 위험이 높다라는 관점을 갖고 있었으나, 이 논문의 결과를 통해 이는 완전히 잘못되었다는 사실을 실험적으로 확인할 수 있었다(2010, 2015년에도 이론적으로 확인한 바 있음). 

본 논문에서는 암호 강도에 따라 만료일을 다르게 설정하는 방법으로 실험을 수행하였으나, 온라인 공격(10^6 추측 공격)에 대해서 충분히 안전한 수준의 암호나, 이보다 훨씬 어렵지만 오프라인 공격(10^14 추측 공격)에 대해서 안전성을 보장할 수 없는 수준의 암호가 1년에 1회 이상 변경(또는 초기화)됨을 확인하였다. 즉, 적절한 수준의 (샤넌 엔트로피 50 bits) 안전성을 가진 암호는 암호 강도에 따라 만료일을 다르게 하는 것이 크게 의미없다는 사실을 확인하였다.

이 논문의 실험은 실제 환경에서의 실제 서비스(대학 IT 서비스)에 적용하여 진행하였으며, 90여명의 유저 피드백을 논문에 정리하여 포함시켰으므로, 추후 이러한 실험 중심의 논문을 작성할 때 참조할 수 있을 것으로 보인다.

## Details
(Document for presentation)

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
