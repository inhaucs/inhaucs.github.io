---
title: Session 1. The Rewards and Costs of Stronger Passwords in a University Linking Password Lifetime to Strength
date: 2019-04-16 00:00:00 Z
description: test about how to post into this site. 
card_title: Session 1
card_teaser: The Rewards and Costs of Stronger Passwords in a University Linking Password Lifetime to Strength
card_position: 2
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

## Details


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
