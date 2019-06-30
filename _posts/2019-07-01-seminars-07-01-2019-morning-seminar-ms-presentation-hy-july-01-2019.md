---
title: Session 1. HEDGE: Efficient Traffic Classification of Encrypted and Compressed Packets
date: 2019-07-01 00:00:00 Z
description: HEDGE: Efficient Traffic Classification of Encrypted and Compressed Packets
card_title: Session 1
card_teaser: HEDGE: Efficient Traffic Classification of Encrypted and Compressed Packets
card_position: 1
icon: fa-server
categories: [seminars,07-01-2019-morning-seminar,presentation]
tags: [TIFS, 2019, TIFS2019, Encryption, High entropy sources, Compression, Classification, Traffic analysis]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-july-01-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-07-01

## [HEDGE: Efficient Traffic Classification of Encrypted and Compressed Packets](https://inhaucs.github.io/seminars/07-01-2019-morning-seminar/presentation/ms-presentation-hy-july-01-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8691576)
+ Authors: Fran Casino; Constantinos Patsakis (University of Piraeus); Kim-Kwang Raymond Choo (University of Texas at San Antonio)
+ **Journal** name: IEEE Transactions on Information Forensics and Security (Volume 14, Issue 11)
+ Published date: 2019-04-15
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8691576)


### Abstract
As the size and source of network traffic increase, so does the challenge of monitoring and analyzing network traffic. Therefore, sampling algorithms are often used to alleviate these scalability issues. However, the use of high entropy data streams, through the use of either encryption or compression, further compounds the challenge as current state-of-the-art algorithms cannot accurately and efficiently differentiate between encrypted and compressed packets. In this paper, we propose a novel traffic classification method named High Entropy DistinGuishEr (HEDGE) to distinguish between compressed and encrypted traffic. HEDGE is based on the evaluation of the randomness of the data streams and can be applied to individual packets without the need to have access to the entire stream. The findings from the evaluation show that our approach outperforms current state of the art. We also make available our statistically sound dataset, based on known benchmarks, to the wider research community.


## Summary (Korean)
+ IoT & Mobile 기기들이 늘어남에 따라 네트워크 트래픽도 급격히 증가 -> 보안 및 프라이버시 문제 발생
+ 최근의 네트워크 데이터들은 일반적으로 암호화됨
  + 트래픽이 암호화되어 있더라도 분석을 통해 사용자 행위를 식별하는 연구들이 있음 ([[CMS+16]], [[TSC+18]])
    + Hgih entropy stream 을 잘 분석하지 못 하다는 한계 존재
+ 보통은 데이터 보호를 위해 암호화를 사용함
  + 그러나 IoT 기기들은 연산 능력의 부족으로 암호화를 잘 수행하지 못 함
    + ***기존의 기술들은 암호화(Encryption)와 압축(Compression)을 잘 구별하지 못하므로***, 암호화 대신 압축을 많이 사용함
+ 그래서 HEDGE: High Entropy DistinGuishEr 개발
  + 기존의 접근과 달리 모든 네트워크 트래픽을 분석하지 않음
  + 실시간 탐지를 위해 임의의 부분적인 트래픽 사용 (Random Subset)
+ 결과 요약
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-comp_summ.png" legend="A comparative summary." width="50%" %}
  + 초록색과 노란 선의 결과는 우리와 달리 추가적인 트래픽 정보를 사용해 분석한 결과임

[CMS+16]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7265055> "M. Conti, L. V. Mancini, R. Spolaor, and N. V. Verde, “Analyzing android encrypted network traffic to identify user actions,” IEEE Trans. Inf. Forensics Security, vol. 11, no. 1, pp. 114–125, Jan. 2016."
[TSC+18]: <https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8006282> "V. F. Taylor, R. Spolaor, M. Conti, and I. Martinovic, “Robust smartphone app identification via encrypted network traffic analysis,” IEEE Trans. Inf. Forensics Security, vol. 13, no. 1, pp. 63–78, Jan. 2018."


## Proposed Approach
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-overview.png" legend="An overview of the proposed approach." width="50%" %}
+ 교환되는 메시지 : 평문, 암호문, 압축문
+ Eve: 메시지 인터셉트 가능
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-step_by_step.png" legend="Step by step of our methodology." width="50%" %}
+ Randomness Tests 에는 Chi square test (2) 와 NIST SP 800-22 (1) 세 가지를 사용
+ 구분하려는 암호화 알고리즘은 AES (128, 192, 256) & Camelia (128, 192, 256) 이며, 압축 알고리즘은 ZIP, RAR, BZIP2, GZIP


## Experiments
+ 상기 Randomness test 들은 파일 크기에 영향을 받으므로, 실험에서 파일 크기도 고려함
+ Dataset
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-dataset.png" legend="Datasets." width="50%" %}
  + 그림, 비디오, 바이너리, 오디오, 텍스트, PDF 에서 같은 수의 파일 사용
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-accuracy.png" legend="Accuracy detection." width="50%" %}
  + Gain Factor? : 회수율(이득률)이라고 하는데, 설명은 없고 적용한다고 되어있음. 실험 결과를 보면 Threshold가 얼마나 엄격하게 적용되는지를 결정하는 인자로 생각됨
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-01-fig-outcomes.png" legend="Outcomes." width="50%" %}


### Points to note
+ 기계 학습을 사용하지 않고 높은 성능으로 암호화 패킷과 압축된 패킷을 구분하는 방법 제시
+ 구현 코드 제공 : https://github.com/francasino/traffic_analysis



## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
