---
title: "Session 2. ProcHarvester: Fully Automated Analysis of Procfs Side-Channel Leaks on Android"
date: 2019-04-18 00:00:00 Z
description: (blank)
card_title: Session 2
card_teaser: "Session 2. ProcHarvester: Fully Automated Analysis of Procfs Side-Channel Leaks on Android"
card_position: 2
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [ASIACCS, 2018, ASIACCS2018, Android, automatic analysis, procfs, side-channel analysis]
sidebar: morning-seminar
layout: default
slug: ms-presentation-th-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Tae-Hyun Kim (김태현)
+ 2019-04-22

## Information of the paper
+ Authors: Raphael Spreitzer, Felix Kirchengast, Daniel Gruss, and Stefan Mangard(Graz University of Technology)
+ Conference name: Proceedings of the 2018 on Asia Conference on Computer and Communications
+ Published date: 2018-06-08
+ [Paper Link](https://pure.tugraz.at/ws/portalfiles/portal/17305447/AsiaCCS2018.pdf)

## Abstract
The procfs has been identified as a viable source of side-channel information leaks on mobile devices. Starting with Android M (Android 6), access to the procfs has been continuously restricted in order to cope with these attacks. Yet, more recent papers demonstrated that even if access to process-specific information is restricted within the procfs, global statistics can still be exploited. However, with state-of-the-art techniques, the search for procfs information leaks requires a significant amount of manual work. This makes an exhaustive analysis of existing and newly introduced procfs resources in terms of information leaks impractical.
We introduce ProcHarvester, a systematic and fully automated technique to assess procfs information leaks. ProcHarvester automatically triggers events of interest and later on applies machine learning techniques to identify procfs information leaks.We demonstrate the power of ProcHarvester by identifying information leaks to infer app starts from a set of 100 apps with an accuracy of 96% on Android N (Android 7). Thereby, we outperform the most accurate app inference attack by about 10 percentage points. We also demonstrate the ease of applicability of ProcHarvester by showing how to profile other events such as website launches as well as keyboard gestures, and we identify the first procfs side channels on Android O (Android 8). ProcHarvester advances investigations of procfs information leaks to the next level and will hopefully help to reduce the attack surface of side-channel attacks.


## Summary (Korean)
안드로이드에서 procfs information leaks를 자동으로 찾아서 앱의 실행, 웹사이트 방문, 키보드 제스처와 같은 이벤트의 발생을 알아낼 수 있다. 이를 이용해 OS 설계자와 OS 개발자가 이후 좀 더 안전하게 OS를 개발해 주길 기대한다.

## Details
  + Android에서 앱 설치 중에 user ID(uid)가 할당되고 process ID(pid)는 실행 된 프로세스를 식별하는데 이러한 리소스는 각어플리케이션의대한 정보를 제공한다. 또한, procfs는 시스템에서 처리된 interrupt에 대한 통계 정보와 같이 무해하다고 간주되는 정보를 제공하기도 한다.

#### procfs Rectiction
  + Android 4.3부터 이전 정책보다 더 세분화해서 앱에 대한 액세스를 제한한다.
  + Android 6부터 third-party 앱들은 untrusted_app으로 label되는데, 해당 앱들은 /proc/에만 액세스 할 수 있도록 제한된다.
  + Android 7부터 process들은 자신의 pid가 아닌 경우의 /proc/<pid>/*에 접근 할 수 없다.
  + Android 8부터 procfs에 대한 제한이 더 많아졌다.(/proc/interrupts에 더이상 접근이 불가능하다.)

#### ProcHarvester는 네가지 단계로 구성됨
  + exploration phase 
  + profiling phase 
  + analysis phase 
  + attack phase 
  
#### ProcHarvester의 작업흐름은 아래 네가지가 있다.
  + Trigger event: Desktop에서 ADB connection을 통해 이벤트를 실행. ADB를 통해 이벤트를 실행하는 것 외에도 MonkeyRunner와 같이 안드로이드 앱 자체에서 프로그래밍 방식으로 이벤트를 실행할 수 있다. 그리고 이벤트는 사람이 직접 실행시킬수 있다. 
  + Log: 안드로이드 앱은 procfs resource로부터 정보의 발생을 알 수 있다(exploration phase). 이벤트 실행의 실제 접근 방식과 관계없이, 안드로이드 앱은 지속적으로 procfs resource를 모리터링하고 기록한다(profiling phase).
  + Fetch Data: 특정 이벤트가 실행되면 분석을 위해 로그파일을 Desktop으로 가져온다.
  + Analysis: 실행된 이벤트를 추론하기 위해 기록된 정보간의 가능한 상관관계에 대해 분석한다(analysis phase). 즉, 실행된 이벤트를 추론하는 부채널 공격에 이용 될 수 있는 resource의 리스트를 뽑아낸다(attack phase). 


## Discussion
+ Editor: 손예별
+ 이벤트 자동으로 실행 -> scikit-learn, dynamic-time-wraping(DTW) 등의 툴을 이용해 이벤트 분석 -> 앱 이용시 비슷한 결과를 내는 것들을 모아 앱의 finger print를 만듦.
+ Finger Print를 가지고, 사용자의 앱 리소스를 분석하여 사용자가 무슨 앱을 쓰는지 확인 가능 (사용자의 이용 정보를 획득)
+ 자동으로 분석하는 툴 들 중에서는 정확도가 높음.
  + 수동으로 하는 분석 보다는 낮을 수 있음.
  + Android 8에서 최초로 분석 진행
+ 폰을 루팅을 해도 /proc/ 폴더 외에는 접근이 불가능하게 개발되었다는 점을 고려하면, 루팅 후 /proc/이외의 폴더에 접근하는 공격기법을 만들면 논문이 될 수 있을 것 같음. 


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
