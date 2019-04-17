---
title: "Session 5. ProcHarvester: Fully Automated Analysis of Procfs Side-Channel Leaks on Android"
date: 2019-04-17 00:00:00 Z
description: (blank)
card_title: Session 5
card_teaser: "Session 5. ProcHarvester: Fully Automated Analysis of Procfs Side-Channel Leaks on Android"
card_position: 5
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
tags: [ASIACCS, 2018, ASIACCS2018, Android, automatic analysis, procfs, side-channel analysis]
sidebar: morning-seminar
layout: default
slug: ms-presentation-th-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Tae-Hyun Kim (김태현)
+ 2019-04-18

## Information of the paper
+ Authors: Raphael Spreitzer, Felix Kirchengast, Daniel Gruss, and Stefan Mangard(Graz University of Technology)
+ Conference name: Proceedings of the 2018 on Asia Conference on Computer and Communications
+ Published date: 2018-06-08
+ [Paper Link](https://pure.tugraz.at/ws/portalfiles/portal/17305447/AsiaCCS2018.pdf)

## Abstract
The procfs has been identified as a viable source of side-channel information leaks on mobile devices. Starting with Android M (Android 6), access to the procfs has been continuously restricted in order to cope with these attacks. Yet, more recent papers demonstrated that even if access to process-specific information is restricted within the procfs, global statistics can still be exploited. However, with state-of-the-art techniques, the search for procfs information leaks requires a significant amount of manual work. This makes an exhaustive analysis of existing and newly introduced procfs resources in terms of information leaks impractical.
We introduce ProcHarvester, a systematic and fully automated technique to assess procfs information leaks. ProcHarvester automatically triggers events of interest and later on applies machine learning techniques to identify procfs information leaks.We demonstrate the power of ProcHarvester by identifying information leaks to infer app starts from a set of 100 apps with an accuracy of 96% on Android N (Android 7). Thereby, we outperform the most accurate app inference attack by about 10 percentage points. We also demonstrate the ease of applicability of ProcHarvester by showing how to profile other events such as website launches as well as keyboard gestures, and we identify the first procfs side channels on Android O (Android 8). ProcHarvester advances investigations of procfs information leaks to the next level and will hopefully help to reduce the attack surface of side-channel attacks.


## Summary (Korean)
안드로이드에서 부채널 공격에 이용 가능한 procfs 정보의 유출을 자동으로 찾을 수 있고, 앱의 실행, 웹사이트 방문, 키보드 제스처와 같은 이벤트에 대한 정보의 유출을 감지할 수 있다. 이를 이용해 OS 설계자와 OS 개발자가 이후 좀 더 안전하게 OS를 개발해 주길 기대한다.

## Details
#### ProcHarvester는 네가지 단계로 구성됨
  + exploration phase 
  + profiling phase 
  + analysis phase 
  + attack phase 
  
#### ProcHarvester의 작업흐름은 아래 네가지가 있다.
  + Trigger event: Desktop에서 ADB connection을 통해 이벤트를 실행. ADB를 통해 이벤트를 실행하는 것 외에도 MonkeyRunner와 같이 안드로이드 앱 자체에서 프로그래밍 방식으로 이벤트를 실행할 수 있다. 그리고 이벤트는 사람이 직접 실행시킬수 있다. 
  + Log: 안드로이드 앱은 exploration phase에서 procfs resource로부터의 정보 유출을 식별할 수 있다. 이벤트 실행의 실제 접근 방식과 관계없이, 안드로이드 앱은 지속적으로 profiling phase에서 procfs resource를 모리터링하고 기록한다.
  + Fetch Data: 특정 이벤트가 실행되면 분석을 위해 로그파일을 Desktop으로 가져온다.
  + Analysis: Analysis phase에서 실행된 이벤트를 추론할 수 있는 정보 유출을 식별하기 위해 가능한 상관관계에 대해 분석한다. 즉, attack phase에서 실행된 이벤트를 추론할 수 있고, 부채널 공격에서 이용될 수 있는 리소스의 리스트다. 
  
#### procfs를 프로파일링하는 방법

  

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
