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
+ 

## Related Works
+ 비교 대상
  + Wang-kNN[[WCN+14]]
    + k-NN 사용
    + 100 개의 웹사이트들에 대해 90-95% 공격 달성
  + CUMUL[[PLZ+16]]
    + Radial Basis Function (RBF) kernel을 사용한 SVM 사용
    + 패킷 길이의 누적합 사용(나가는 패킷 - 들어오는 패킷)과 패킷의 개수 사용
    + 100 개의 웹사이트들에 대해 90-93 % 공격 달성
  + k-Fingerprinting(k-FP)[[HD16]]
    + Random Forests 사용
    + 100 개의 웹사이트들에 대해 90-93 % 공격 달성

[WCN+14]: <https://www.usenix.org/conference/usenixsecurity14/technical-sessions/presentation/wang_tao> "T. Wang, X. Cai, R. Nithyanand, R. Johnson, and I. Goldberg, “Effective Attacks and Provable Defenses for Website Fingerprinting,” in USENIX Security Symposium. USENIX Association, 2014, pp. 143–157."
[PLZ+16]: <https://nymity.ch/tor-dns/pdf/Panchenko2016a.pdf> "A. Panchenko, F. Lanze, A. Zinnen, M. Henze, J. Pennekamp, K.Wehrle, and T. Engel, “Website fingerprinting at internet scale,” in Network & Distributed System Security Symposium (NDSS). IEEE Computer Society, 2016, pp. 1–15."
[HD16]: <https://www.usenix.org/conference/usenixsecurity16/technical-sessions/presentation/hayes> "J. Hayes and G. Danezis, “k-fingerprinting: a Robust Scalable Website Fingerprinting Technique,” in USENIX Security Symposium. USENIX Association, 2016, pp. 1–17."

## Threat Model
+ 이전 WF 관련 연구들에서 고려되던 공격자 모델 사용
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-fig-wf_scenario.png" legend="Overview of the proposed method." width="50%" %}
  + a passive and local network-level adversary
  + Passive adversary: Tor network을 통해 전달되는 암호화된 트래픽을 확인할 수 있으며, 트래픽 수정, 삽입, 드랍 불가
  + Local adversary: 네트워크의 제한된 부분만 볼 수 있음
  <!-- + ISP-level의 공격자 가정: 복호화가 가능한 level -->
+ WF 연구들에서는 closed world assumption이 일반적임 -> 유저가 공격자가 학습 가능한 페이지들만 방문한다고 가정
  + 하지만 실제 상황과 부합하지 않으므로 본 연구에서는 open world assumption과 closed world assumption을 함께 고려

## Data Collection
+ 암호화된 페이로드는 사용할 수 없기 때문에, 메타 데이터만을 저장
  + 시간 정보(timing information), 방향(direction), TCP 패킷 크기
+ 데이터셋
  + Alexa Top Sites에 있는 웹페이지들을 대상으로 트래픽 수집
  + 종류
    + Closed world: 1,200 개의 웹사이트로부터, 각각 3,000 개의 네트워크 트레이스 -> 타임아웃이나 프레임웍(e.g., 셀레니움) 크래쉬로 인한 항목 제거 -> 정제했다
    + Revisit over time: 첫 데이터 획득 후 3일, 10일, 4주, 6주, 그리고 8주 후, 상위 200개 웹페이지에 대해 각각 500 개의 트레이스 획득
    + Open world: 400,000 개의 트레이스 획득 + Closed world 의 400,000 개 -> 800,000 개 트레이스
      + 테스트 목적으로만 사용했다고 하는데, 기존의 WF 논문들이 Closed world assumption을 기준으로 연구되었기 때문에, 테스트라도 했다는 데에 의의를 두는 것 같음


## Evaluation
+ 최신 WF 방법들을 우리가 수집한 데이터셋에 대해 다시 평가(Related work의 [WCN+14], [PLZ+16], [HD16])
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-fig-new_data.png" legend="Re-evaluation of traditional WF attacks on new data." width="50%" %}
  + CW100: 100 개 웹사이트에 대한 Closed world dataset이며 각 웹페이지마다 100 개의 트레이스
  + 새로 수집된 데이터셋에서 실험했을 때 더 높은 정확도
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-fig-web_traces.png" legend="Impact on the classification accuracy for a growing number of website traces." width="50%" %}
  + Trace 수가 증가함에 따라 정확도가 높아짐

## Deep Learning for Website Fingerprinting
+ WF에 세 가지 DNN 적용
  + SDAE, CNN, LSTM
+ Deep Learning 적용 순서
  + Problem definition
    + WF를 분류 문제로 설정
  + Hyperparameter tuning and model selection
  + Closed world evaluation
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-tbl-closed_world.png" legend="Acc, loss and runtime of the DL models." width="50%" %}
  + Concept drift evaluation
    + 웹페이지의 컨텐츠들은 시간에 따라 변화하기 때문에, 며칠 후의 트래픽을 사용해 테스트를 하면 정확도가 현저히 떨어짐
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-fig-time_gap.png" legend="DL vs. CUMUL over time." width="50%" %}
    + 이 정도 성능 하락은 봐줄만한 것이라 얘기하고 있으며, CUMUL보다 Deep Learning을 적용했을 때 그래도 더 높음
  + Open world evaluation
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-06-27-fig-open_world.png" legend="DL vs. CUMUL in the open world." width="50%" %}
    + Open world assumption 에서도 closed world assumption과 같이 Deep Learning 기반의 공격이 더 잘 수행됨을 보임


### Points to note
+ 패킷 내용이 아닌, 메타 데이터만으로 Webpage fingerprinting
+ WF 공격에 Deep Learning을 적용하는 체계적인 방법 제시



## Discussion


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
