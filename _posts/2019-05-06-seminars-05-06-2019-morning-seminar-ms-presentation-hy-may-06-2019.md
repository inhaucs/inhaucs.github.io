---
title: Session 4. Significant Permission Identification for Machine-Learning-Based Android Malware Detection
date: 2019-05-06 00:00:00 Z
description: Significant Permission Identification for Machine-Learning-Based Android Malware Detection
card_title: Session 4
card_teaser: Significant Permission Identification for Machine-Learning-Based Android Malware Detection
card_position: 4
icon: fa-server
categories: [seminars,05-06-2019-morning-seminar,presentation]
tags: [TII, 2018, TII2018, Access control, computer security, machine learning, mobile applications, mobile computing]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-may-06-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-05-06

## [Significant Permission Identification for Machine-Learning-Based Android Malware Detection](https://inhaucs.github.io/seminars/05-06-2019-morning-seminar/presentation/ms-presentation-hy-may-06-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8255798)
+ Authors: Jin Li (Guangzhou University); Lichao Sun (University of
Illinois at Chicago); Qiben Yan; Zhiqiang Li; Witawas Srisa-an (University of Nebraska–Lincoln); Heng Ye (Beijing Jiaotong University)
+ Conference name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-01-12
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8255798)


### Abstract
The alarming growth rate of malicious apps has become a serious issue that sets back the prosperous mobile ecosystem. A recent report indicates that a new malicious app for Android is introduced every 10 s. To combat this serious malware campaign, we need a scalable malware detection approach that can effectively and efficiently identify malware apps. Numerous malware detection tools have been developed, including system-level and network-level approaches. However, scaling the detection for a large bundle of apps remains a challenging task. In this paper, we introduce Significant Permission IDentification (SigPID), a malware detection system based on permission usage analysis to cope with the rapid increase in the number of Android malware. Instead of extracting and analyzing all Android permissions, we develop three levels of pruning by mining the permission data to identify the most significant permissions that can be effective in distinguishing between benign and malicious apps. SigPID then utilizes machine-learning-based classification methods to classify different families of malware and benign apps. Our evaluation finds that only 22 permissions are significant. We then compare the performance of our approach, using only 22 permissions, against a baseline approach that analyzes all permissions. The results indicate that when a support vector machine is used as the classifier, we can achieve over 90% of precision, recall, accuracy, and F-measure, which are about the same as those produced by the baseline approach while incurring the analysis times that are 4–32 times less than those of using all permissions. Compared against other state-of-the-art approaches, SigPID is more effective by detecting 93.62% of malware in the dataset and 91.4% unknown/new malware samples.


## Summary (Korean)
+ Android에서 새로운 Malware들이 10초에 하나 꼴로 추가되고 있음
+ 기존의 system-level, network-level 의 malware detection tool들이 있으나 여전히 문제
+ 이에, Significant Permission IDentification (SigPID) 제안
  + 권한 분석에 기반한 Malware detection system
  + Android의 모든 권한을 분석하는 것이 아닌 일반 앱과 Malware를 구분하는 가장 심대한 권한을 가지치기하는 세 가지 레벨을 개발
  + 기계 학습 기반 분류 방법 사용
  + 결과적으로 22 개의 권한이 중요 권한임을 찾음
  + 실험 : baseline approach(모든 권한에 대해 분석) vs. 상기 22개의 권한에 대한 분석
    + 결과적으로 SVM을 분류기로 사용했을 때, baseline approach 와 비교하여 비슷한 결과를 얻었으며, 90%가 넘는 precision, recall, accuracy, F-measure를 보였고, 4-32배 빠름
    + State-of-art approach와 비교해도 SigPID는 93.62%의 malware를 탐지함으로써 더 나은 성능을 보였고, 알려지지 않거나/새로운 Malware에 대해서도 91.4% 탐지
  + Contribution
    + Malware를 탐지하기 위한 권한의 서브셋을 찾는 SigPID 개발 -> 필요한 권한을 84% 줄임(16% 사용)
    + 제안하는 방법 평가 -> 90% in precision, recall, accuracy, and F-measure
    + 포괄성 증명 -> 주로 사용되는 67개의 지도 학습 알고리즘에 적용 (5494 malware & 310926 benign)
      + 55개의 알고리즘에서 F-measure 85% 이상, 평균 수행 시간이 baseline approach에 비해 85.6% 감소


## Motivation
+ Android 시장은 매우 큰데, iOS와는 다르게 third-party나 file-sharing을 통한 어플리케이션 설치를 허용하고 있음 -> Malware가 다운로드될 수 있는 경로
+ Mobile malware의 97%가 Android를 타겟으로 함
+ 이러한 Malware의 타입은 50개 이상 있고, 이 때문에 모두 탐지하기가 힘듦
+ 이전 기술들이 있고 한계가 있음
  + RISKRANKER : 정적 분석 기반 -> False positive 많음
  + TAINTDROID : 동적 분석 기반 -> Malware 탐지 회피 기술
  + DREBIN : 정적 분석 + 기계 학습 -> High Cost


## Introducing SigPID
+ Goal : Malware 분석을 위해 필요한 최소한의 권한 찾기
+ a) Multi-Level Data Pruning(MLDP)을 사용하여 Malware 탐지에 영향이 별로 없는 권한 제거, 이는 세 컴포넌트를 포함
  + Permission Ranking with Negative Rate (PRNR)
  + Support-based Permission Ranking (SPR)
  + Permission Mining with Association Rules (PMAR)
+ b) MLDP로 필터링된 권한들을 지도 학습 분류 방법에 입력으로 사용하여 Malware 탐지

  ##### Multi-Level Data Pruning(MLDP)
  + Permission Ranking with Negative Rate (PRNR)
    + Benign과 Malware를 구별하는 권한들을 식별하고, 비슷하게 사용되는 권한 제거(pruning)
    + 이를 위해 PPNR을 사용할건데, 먼저 Malware와 Benign 어플리케이션들에서 사용되는 권한들을 매트릭스 M & B로 표현
      + Sample 수가 다르면 Skewed model이 될 수 있으므로(5494 malware vs. 310,926 benign), scaling 해주는 식 포함 (1)
      + 식 (2)를 사용하여 권한들의 사용 빈도를 계산, [-1, 1]의 값이 나오며 -1은 benign에서만 사용하는 권한, 1은 malware에서만 사용하는 권한을 의미, 0인 경우 malware 탐지에 별 효과가 없음을 의미
      + R(P) 값이 1, -1인 값이 중요하므로, 오름차순과 내림차순의 two ranked lists 생성
      + Two lists의 top tier 권한을 시스템에 넣어 TPR, FPR, precision, recall, F-measure를 측정, 이 값이 안정될 때까지 반복
        + 이를 통해, 전체 sample에서 135개의 권한을 사용하는데 이를 비슷한 정확도를 가지는 95개로 줄임
  + Support-based Permission Ranking (SPR)
    + 상기 PRNR 방법은 benign과 malware 각각에서 사용되는 ranking이기 때문에, 실질적인 support를 고려(특정 권한은 benign에서만 사용된다든지)
    + 사용되는 권한을 25개로 줄임
  + Permission Mining with Association Rules (PMAR)
    + 특정 권한들의 경우 항상 같이 등장함(e.g., WRITE_SMS AND READ_SMS) -> 하나만 사용해도 됨
    + 결과적으로 22개의 권한으로 줄임

  ##### Machine-Learning-Based Malware Detection Using Significant Permissions
  + SVM을 먼저 사용하여 비교했고, 주로 알려진 67개의 기계 학습 알고리즘을 사용, 135개의 전체 권한(baseline)과 비교 결과는 차후 기술


## Evaluation
+ Dataset
  + Google play store benign apps 310,926개 [[ASH+14]], 여러 소스로부터 2650, 5494, 54694 Malware [[WWF+14]]
+ Evaluating Effectiveness of MLDP
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-05-06-fig-detection_results.png" legend="Detection Results" %}
  + Malware는 잘 찾으나 FPR이 상대적으로 높음
  + Mutual Information이라는 다른 권한 리스트와 비교한 내용이 Table 2에 있음
+ Evaluating Generality of MLDP
  + Figure 5에서 top five 기계 학습 알고리즘에 대해서 테스트 결과를 보임
  {% include articles/figure.html url="/assets/img/heeyong/2019/2019-05-06-fig-optimal_ml_algorithm.png" legend="Optimal Machine Learning Algorithm" %}
  + SigPID(Proposed)와 Google에서 제안한 방법에 대해서 가장 좋은 기계 학습 방법에 대한 소개
  + Table 4에서 Top five 기계 학습 알고리즘에 대한 수행 시간을 보임, 예상되다시피 권한의 수가 적을수록 빠름을 보임
  + Table 5에서는 다른 소스에서 얻어진 Malware들에 대해서 Precision, Recall, FPR, FM, ACC 비교
+ Comparison With Other Approaches
  + Other Approaches
    + DREBIN [[ASH+14]] : 정적 분석 접근법 사용, SVM 사용, 재구현하지는 않고 논문에 있는 정보 사용
    + PERMISSION-INDUCED RISK MALWARE DETECTION [[WWF+14]] : Mutual information이라는 권한 랭킹 사용, 위험한 권한 상위 40개를 사용, 이건 재구현 함
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-05-06-fig-detection_rates.png" legend="Detection Rates" %}
    + Antivirus scanners가 detection rate이 작은 이유는 signature matching based이기 때문


### Points to note
+ 권한 랭킹과 가지치기를 통해 적은 수의 권한들로 높은 수준의 malware 탐지율을 보임
+ 비록 최신 연구 내용과 비교하여 더 높은 탐지율은 아니지만, 이와 비슷한 수준이며 feature로 사용되는 권한의 수가 적기 때문에, malware가 빠르게 늘어나는 Android 플랫폼의 특성상 빠르게 탐지해야하는 요구 조건을 만족시킴



## Discussion

[ASH+14]: <https://www.researchgate.net/profile/Hugo_Gascon/publication/264785935_DREBIN_Effective_and_Explainable_Detection_of_Android_Malware_in_Your_Pocket/links/53efd0020cf26b9b7dcdf395.pdf> "D. Arp, M. Spreitzenbarth, M. H¨ubner, H. Gascon, K. Rieck, and C. Siemens, “DREBIN: Effective and explainable detection of android malware in your pocket,” presented at Annu. Symp. Netw. Distrib. Syst. Security, 2014."
[WWF+14]: <https://ieeexplore.ieee.org/abstract/document/6891250> "W. Wang, X. Wang, D. Feng, J. Liu, Z. Han, and X. Zhang, “Exploring permission-induced risk in android applications for malicious application detection,” IEEE Trans. Inf. Forensics Security, vol. 9, no. 11, pp. 1869–1882, Nov. 2014."


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
