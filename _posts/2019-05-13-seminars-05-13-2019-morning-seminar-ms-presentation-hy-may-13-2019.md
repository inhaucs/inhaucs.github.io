---
title: Session 4. Detection of Malicious Code Variants Based on Deep Learning
date: 2019-05-13 00:00:00 Z
description: Detection of Malicious Code Variants Based on Deep Learning
card_title: Session 4
card_teaser: Detection of Malicious Code Variants Based on Deep Learning
card_position: 4
icon: fa-server
categories: [seminars,05-13-2019-morning-seminar,presentation]
tags: [TII, 2018, TII2018, Malware variants, grayscale image, deep learning, convolution neural network, bat algorithm]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-may-13-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-05-13

## [Detection of Malicious Code Variants Based on Deep Learning](https://inhaucs.github.io/seminars/05-13-2019-morning-seminar/presentation/ms-presentation-hy-may-13-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8330042)
+ Authors: Zhihua Cui; Xingjuan Cai; Jinjun Chen (TaiYuan University of Science and Technology); Fei Xue (Beijing Wuzi University); Yang Cao (Beijing Unibersity of Technology); Gai-ge Wang (Ocean University)
+ **Journal** name: IEEE Transactions on Industrial Informatics
+ Published date: 2018-04-03
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8330042)


### Abstract
With the development of the Internet, malicious code attacks have increased exponentially, with malicious code variants ranking as a key threat to Internet security. The ability to detect variants of malicious code is critical for protection against security breaches, data theft, and other dangers. Current methods for recognizing malicious code have demonstrated poor detection accuracy and low detection speeds. This paper proposed a novel method that used deep learning to improve the detection of malware variants. In prior research, deep learning demonstrated excellent performance in image recognition. To implement our proposed detection method, we converted the malicious code into grayscale images. Then, the images were identified and classified using a convolutional neural network (CNN) that could extract the features of the malware images automatically. In addition, we utilized a bat algorithm to address the data imbalance among different malware families. To test our approach, we conducted a series of experiments on malware image data from Vision Research Lab. The experimental results demonstrated that our model achieved good accuracy and speed as compared with other malware detection models.


## Summary (Korean)
+ Internet 발달과 함께 각종 malware들의 변종들이 등장
+ 현재의 탐지 방법들은 탐지율이 매우 낮고 심지어 느림
+ Deep learning을 사용해서 malware의 변종들을 탐지하는 방법을 제안
  + Malware 코드를 **grayscale** 이미지로 변환
  + 변환된 image에 대해서 **Convolution Neural Network (CNN)** 적용
  + 다른 malware familie 사이의 불균형을 다루기 위해 **bat algorithm** 사용
+ Vision Research Lab.의 malware 이미지 데이터에 대해 실험했고(Santa Barbara, [[NLJ+11]]), 좋은 정확도와 속도를 보임

[NLJ+11]: <http://delivery.acm.org/10.1145/2020000/2016908/a4-nataraj.pdf?ip=165.246.44.143&id=2016908&acc=ACTIVE%20SERVICE&key=36491E83F85BB6C1%2E36491E83F85BB6C1%2E1702E7686A5145AB%2E4D4702B0C3E38B35&__acm__=1557306835_9d024be09ef7961180484ff3c8575c2a> "Nataraj, Lakshmanan, et al. "Malware images: visualization and automatic classification." Proceedings of the 8th international symposium on visualization for cyber security. ACM, 2011."


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
    + Antivirus scanners가 detection rate이 작은 이유는 signature matching based이기 때문
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-05-06-fig-detection_rates.png" legend="Detection Rates" %}


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