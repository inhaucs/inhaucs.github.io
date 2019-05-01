---
title: Session 2. Analysis of Privacy Protections in Fitness Tracking Social Networks -or- You can run, but can you hide?
date: 2019-05-01 00:00:00 Z
description: Analysis of Privacy Protections in Fitness Tracking Social Networks -or- You can run, but can you hide?
card_title: Session 2
card_teaser: Analysis of Privacy Protections in Fitness Tracking Social Networks -or- You can run, but can you hide?
card_position: 2
icon: fa-server
categories: [seminars,04-29-2019-morning-seminar,presentation]
tags: [USENIX, 2018, USENIX2018, Privacy, Hacking, Mobile]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-apr-29-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-04-29

## [Analysis of Privacy Protections in Fitness Tracking Social Networks -or- You can run, but can you hide?](https://inhaucs.github.io/seminars/04-29-2019-morning-seminar/presentation/ms-presentation-jh-apr-29-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/hassan)
+ Authors: Wajih Ul Hassan, Saad Hussain, and Adam Bates (University Of Illinois Urbana-Champaign)
+ Conference name: 27th USENIX Security Symposium
+ Published date: 2018-08-16
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-hassan_0.pdf)


### Abstract
Mobile fitness tracking apps allow users to track their workouts and share them with friends through online social networks. 
Although the sharing of personal data is an inherent risk in all social networks, the dangers presented by sharing personal workouts comprised of geospatial and health data may prove especially grave. 
While fitness apps offer a variety of privacy features, at present it is unclear if these countermeasures are sufficient to thwart a determined attacker, nor is it clear how many of these services’ users are at risk.

In this work, we perform a systematic analysis of privacy behaviors and threats in fitness tracking social networks. 
Collecting a month-long snapshot of public posts of a popular fitness tracking service (21 million posts, 3 million users), 
we observe that 16.5% of users make use of Endpoint Privacy Zones (EPZs), 
which conceal fitness activity near user-designated sensitive locations (e.g., home, office). 
We go on to develop an attack against EPZs that infers users’ protected locations from the remaining available information in public posts, 
discovering that 95.1% of moderately active users are at risk of having their protected locations extracted by an attacker. 
Finally, we consider the efficacy of state-of-the-art privacy mechanisms through adapting geo-indistinguishability techniques as well as developing a novel EPZ fuzzing technique. 
The affected companies have been notified of the discovered vulnerabilities and at the time of publication have incorporated our proposed countermeasures into their production systems.


## Summary (Korean)
Fitness tracking service에서의 개인 정보 보호 기능에 대해 실제로 공격한 논문으로, 
운동 시에 자신의 위치를 추적하는 self-tracking 기능에 대한 공격을 통해 사용자의 민감한 지역 (예: 집, 회사 등)을 추측하는 공격이 가능해짐을 보였음.
나아가, 이를 방지하는 기법을 제안하였으며, 그 결과 공격 성공률을 절반 이하로 떨어뜨리는 효과를 보이기도 하였음.
현재, 이 연구진의 제안으로 취약점은 해당 회사의 제품에서 해결된 상태임.


## Details
### Contents of the paper
#### Introduction

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-29-fig-1.PNG" legend=" Example 1" %}

+ 사람들은 대개 민감한 지역 (집, 사무실 등)에서 달리기를 시작한다.
+ 공개되는 이동 경로는 개인정보 보호 문제가 있다. 

  + 자전거 관련된 Fitness 앱을 이용하여 자전거 타는 사람을 추적하여 값 비싼 자전거를 훔치기도 하였다. (기사)
  + 논문서 주로 언급되는 앱은 Strava (run activity) 이며, 이러한 서비스들은 개인정보 보호를 위한 정책들을 펼치고 있음

    + Strava의 300만명의 사용자에 대한 2100만개의 게시물을 한 달간 스냅샷을 통해 수집하였음
    + 이 사용자 중 16.5%가 EPZ (Endpoint Privacy Zone)을 사용함.

      + 민감한 지역을 숨기는 역할을 수행함
      + Zone (고정 크기의 원) 내에서 시작하거나 끝나는 운동 위치를 숨겨주는 역할을 함
      
{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-29-fig-2.PNG" legend=" Example 2" %}

+ 본 논문에서는 EPZ에 대한 공격을 개발하여, 공격자가 자신의 보호된 위치를 추출할 위험이 보통 사용자의 95.1%임을 발견했음.
+ 이러한 공격을 방지하기 위한 새로운 EPZ 퍼징 기술을 개발함으로써 개인 정보 보호 효용성을 늘렸음
  
  + Strava는 이를 현재 수정한 상태임

#### Attack & Conclusion
+ 포인트가 세 개면 원을 그리는 것은 어렵지 않음

  + 실제로는 쉬운일이 아님
  
    + (Multiple endpoints) 여러 개의 EPZ가 예측될 수 있으나, 하나만 정확함
    + GPS의 오차에 의해, endpoint가 EPZ의 경계에 정확히 놓이지 않을 수 있음
    
+ You can run, but can you hide?

  + 공격 과정

    1. Collected activity dataset from strava.com
    2. Designed robust algorithm to search EPZ circles.

       1. 먼저, 보호되지 않는 활동들에 대해 알고리즘을 검증함
       2. 이후에, 보호된 활동들에 대해 공격을 수행함
    3. Designed mitigation strategies

  + Dataset

    + strava.com에서 다음 정보를 수집함
      + GPS coordinates
      + activity type
      + duration
      + distance
      + athlete ID
      + etc.
  + 알고리즘 (EPZ search)

    + Least Square Circle Fit (LSF) algorithm
      + 정확히 공격 요구에 맞지는 않음 (모든 endpoint를 고려한다는 것이나 느리다는 것 등)
    + 이 논문의 알고리즘 자체는 첨부하지 않음

  + 구성한 알고리즘을 통해 공격하는 것을 검증하는 과정이 있음
    1. 보호되지 않은 활동들로부터 생성된 EPZ를 실제 활동들과 정확히 일치하는 지 비교
       + 97%를 식별함 (210만개 활동)
    2. 상기 예측 방식으로 보호된 활동들로부터 EPZ를 찾음
       + 1개의 EPZ만을 이용할 때에는 84%를 식별하였고, (0.4M)
       + 3개 이상의 EPZ를 이용한 경우에는 95%를 식별하였음. (0.3M)


  + Countermeasures?
    + Radius size를 수정
    + EPZ Intersection Point를 Fuzz함
    + Spatial Cloaking?
      + 원의 중심을 옮기는 형태의 방어법 -> 완벽한 방어법은 아님 (어느 정도 정보 유출은 존재함)
      + 선형 인터폴레이션 공격이 가능하긴 하기 때문

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-29-fig-3.PNG" legend=" Countermeasures " %}      

  + 결과적으로 공격 성공률은 다음과 같이 줄어들었음 (대략 절반)


### Points to note
+ 공개적으로 SNS 크롤링을 통해 획득할 수 있는 데이터로부터 실험을 하였음, 추후 이러한 연구를 하는데 논문 구조를 참조할 수 있을 것으로 보임
+ 실제 제품을 공격한 것인데, 사용자의 민감한 개인 정보가 포함되어있어 윤리적 이슈를 주구장창 설명함.
  + 그러나, IRB 승인을 받지 않았는데, 이럴 때 어떤식으로 서술해야하는지 추후 참조할 수 있을 것으로 보임 (9장)


## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
