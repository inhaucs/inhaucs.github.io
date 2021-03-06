---
title: Session 4. Iris Recognition After Death
date: 2019-04-25 00:00:00 Z
description: Iris Recognition After Death
card_title: Session 4
card_teaser: Iris Recognition After Death
card_position: 4
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [TIFS, 2019, Iris recognition, post-mortem biometrics, forensics]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-04-25

## [Iris Recognition After Death](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-hy-apr-25-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8537970)
+ Authors: Mateusz Trokielewicz (Research and Academic Computer Network NASK); Adam Czajka (University of Notre Dame); Piotr Maciejewicz (Medical University of Warsaw)
+ Journal name: IEEE Transactions on Information Forensics and Security
+ Published date: 2018-11-16
+ [Paper Link](https://ieeexplore.ieee.org/document/8537970)


### Abstract
This paper presents a comprehensive study of post-mortem human iris recognition carried out for 1200 near-infrared and 1787 visible-light samples collected from 37 deceased individuals kept in mortuary conditions. We used four independent iris recognition methods (three commercial and one academic) to analyze genuine and impostor comparison scores and check the dynamics of iris quality decay over a period of up to 814 h after death. This study shows that post-mortem iris recognition may be close-to-perfect approximately 5-7 h after death and occasionally is still viable even 21 days after death. These conclusions contradict the statements present in the past literature that the iris is unusable as a biometrics shortly after death, and show that the dynamics of post-mortem changes to the iris that are important for biometric identification are more moderate than previously hypothesized. This paper contains a thorough medical commentary that helps to understand which post-mortem metamorphoses of the eye may impact the performance of automatic iris recognition. An important finding is that false-match probability is higher when live iris images are compared with post-mortem samples than when only live samples are used in comparisons. This paper conforms to reproducible research and the database used in this study is made publicly available to facilitate research on post-mortem iris recognition. To the best of our knowledge, this paper offers the most comprehensive evaluation of post-mortem iris recognition and the largest database of post-mortem iris images.

## Summary (Korean)
+ Dataset: 37명의 사망자로부터 수집된 1200개의 근적외선 및 1787개의 가시광 홍채 표본
  + 이에 대해 사망자의 홍채 인식에 대한 포괄적인 연구 진행
+ Methods(Iris Recognition): 3개의 상업용, 1개의 연구용 인식 방법 사용
  + 사후 817(약 34일)시간까지의 홍채의 품질 저하에 대해 확인
+ 사후 약 5-7 시간까지 홍채 인식은 거의 완벽하고, 사후 21일 후에도 여전히 실행 가능함
+ 이전에 연구된 내용에 따르면 홍채가 사망 직후 생체 인식에 사용될 수 없는데, 이는 틀렸음을 보임
+ 본 연구에 사용된 데이터베이스 공개(http://zbum.ia.pw.edu.pl/EN, Research -> Databases -> 8.Warsaw-BioBase-Post-Mortem-Iris v2.0.)
+ 본 논문은 사후 홍채 인식과 가장 큰 데이터셋에 대해 연구


## Research Question
+ **(Q1)** 사후에도 자동 홍채 인식이 가능한가?
+ **(Q2)** 홍채 인식 성능 저하를 일으키는 요인은 무엇인가?
+ **(Q3)** 사후 홍채 인식에 가장 유용한 이미지는 무엇인가?
+ **(Q4)** 사후 홍채 표본과 비교할 때 에러의 주요인은 무엇인가?
+ **(Q5)** 사후 홍채 인식 성능에 영향을 미치는 요소는 무엇인가?
+ **(Q6)** 사후 홍채 이미지와 생체(live) 홍채 이미지에 대해 false-match로 인한 위험은 무엇인가?
  

## Details
+ Dataset details
  + 37명의 시신
    + 사후 시간 : 5-814시간
    + 연령 : 19-75세
    + 성별 : 5명의 여성과 32명의 남성
    + 사망 원인 : 18명은 심장질환, 7명은 교통 사고, 7명은 자살(교사), 1명은 살인, 2명은 음독사, 2명은 뇌내 출혈
    + 안구색 : 파랑색/녹색/연두색 29명, 연갈색/녹갈색 5명, 진갈색 3명
  + 1200개의 근적외선(near-infrared: NIR) 및 1787개의 가시광(visible-light: VIS) 이미지
    + Fig. 1에서 Image 획득 시간을 보임
  + 온도가 6도 정도인 영안실에서 진행 (기압 습도 등은 체크하지 않음)
  + 냉동실에 들어갔는지는 확인되지 않음
  + False-match를 확인하기 위해 74명의 피실험자로부터 홍채 이미지 추출
+ 4개의 홍채 인식 방법 사용
  + 사후 21일이 지난 시체도 가끔씩 인식되었고, 5-7시간의 홍채는 거의 완벽히 인식
  + 이 결과는 이전의 연구들에서 세운 가설을 반박하는 내용임
  + VIS의 red-channel(R images)을 사용하는 것이 NIR을 사용하는 것보다 나음
  + 4개의 방법
    + VeriEye : 상업용, 4개의 알고리즘 중 두 홍채 이미지의 similarity score를 반환하는 유일한 method, 0-40 score -> 다른 홍채, 40- -> 같은 홍채
    + IriCore : 상업용, 가장 좋은 홍채 인식 솔루션 중 하나, IriCore는 dissimilarity score를 반환하며, 0-1.1 score -> 같은 홍채, 1.1-2.0 -> 다른 홍채
    + MIRLIN : 상업용, 같은 홍채는 0에 가까운 값을, 다른 홍채는 0.5 근처의 값을 반환
    + OSIRIS : 학계의 결과, open-source, 같은 홍채는 0에 가까운 값을, 다른 홍채는 0.4-0.45 근처의 값을 반환
+ Fig 2. 시간에 따른 동공의 변화 및 인식 수준
  + 상기 이미지는 시간이 지남에 따라 동공의 변화를 보임
    + 동공 확장 -> 각막 혼탁 -> 각막의 주름 -> 안구 붕괴
  + 아래의 이미지는 OSIRIS(Open Source for IRIS)로 segmentation한 결과이며, 빨간 부분은 홍채로 인식되지 않으므로 비교에서 제외
+ VIS, NIR, R images로 추출된 이미지 비교를 Fig. 3에서 보임
  + 사후 5, 16, 그리고 27시간 후의 이미지
+ Fig. 4
  + 알고리즘으로 Iris segmentation 시 제대로 되지 않을 수 있으므로, 수동으로 Iris mask도 만듦
+ 세 가지 분석 방법
  + short-term analysis : 처음 수집된 데이터들만 사용하여 분석(사후 5시간)
  + long-term analysis : 모든 데이터들을 사용하여 분석(5-814 시간)
  + open-set analysis : False-match 확률 평가 (live sample과 post-mortem sample 비교)
+ Fig. 5 : Short-term analysis
  + red-channel을 사용했을 때 모든 방법들에서 성능이 가장 좋음
  + MIRLIN이 가장 성능이 안 좋음
  + OSIRIS vs. OSIRIS(manual) : manual segmentation과 비교했을 때, manual 쪽이 성능이 좋은 것으로 보아 post-mortem iris의 segmentation의 중요성을 보임
+ Fig. 6-14는 각 방법들의 비교 Score를 보이며 비교 대상은(사후 5시간 된 홍채와 이후 홍채의 비교)
  + 생전과 사후 홍채 이미지를 동시에 얻을 수 없기 때문에 사후 5시간 된 홍채를 생전의 홍채로 가정하고 실험
  + 실험 목적은 사후 얼마나 오랫 동안 홍채가 충분한 특징(feature)를 제공하는가
  + Fig. 6 and Fig. 8 (OSIRIS vs. OSIRIS(manual))
    + genuine 비교의 경우(같은 홍채) 사후 시간이 증가할수록 홍채가 특징을 잃음
    + impostor 비교의 경우(다른 홍채) 사후 시간이 증가하여도 뚜렷한 변화 없음
  + 이후, Figure 들도 비슷한 맥락으로 설명
+ 사후 홍채와 살아있는 다른 사람들의 홍채와 비교하는 실험
  + 74명의 사람들로부터 live-test/live-reference(37명/37명) 각각 600개의 홍채 이미지 추출
  + IriCore method 사용
    + (a) 사후 홍채 vs. live-test 홍채
    + (b) live-test 홍채 vs. live-reference 홍채
    + Fig. 15(left) : 1.1 이 원래 IriCore의 threshold인데 여기서는 둘 다 합리적임, threshold가 커질수록 사후 홍채의 FMR 늘어남, 이유는 설명하고 있음
    + Fig. 15(right) : Threshold 1.2 에서 FMR, 사후 시간과 FMR에는 상관관계가 없음


#### Conclusion
+ **(Q1)** 사후에도 자동 홍채 인식이 가능한가?
  + 가능, 수동으로 홍채 범위를 지정하는 경우 인식률이 더 나아지는 경향을 보임
+ **(Q2)** 홍채 인식 성능 저하를 일으키는 요인은 무엇인가?
  + 신체 붕괴로 인한 홍채 손실과, 홍채를 제대로 segmentation하지 못 함
+ **(Q3)** 사후 홍채 인식에 가장 유용한 이미지는 무엇인가?
  + short-term analysis : 거의 다 좋지만 R-channel 이미지가 가장 좋고, cross하여 비교하는 것은 성능이 낮으므로 추천하지 않음
  + long-term analysis : NIR와 R-channel 이미지 중 뭐가 딱히 좋다고 결론낼 수 없음
+ **(Q4)** 사후 홍채 표본과 비교할 때 에러의 주요인은 무엇인가?
  + **(Q2)** 와 비슷 신체 붕괴로 인한 홍채 손실과, 홍채를 제대로 segmentation하지 못 함
+ **(Q5)** 사후 홍채 인식 성능에 영향을 미치는 요소는 무엇인가?
  + 음독사나 살인의 경우 더 안 좋은 성능을 보임
  + 성별이나 나이는 성능 차이에 영향이 없음
+ **(Q6)** 사후 홍채 이미지와 생체(live) 홍채 이미지에 대해 false-match로 인한 위험은 무엇인가?
  + 생체 홍채 이미지끼리의 FMR보다 사후 홍채 이미지와 생체 홍채 이미지의 FMR이 더 높으므로, 사후 홍채 이미지를 식별할 수 있는 방법이 필요함


## Limitation
+ 작은 데이터셋(37명)
+ 생전 이미지의 부족
+ 그래도 이 정도면 괜찮은 데이터셋임


### Points to note
+ 새로운 홍채 데이터셋 획득(Maybe, both of post-mortem and live)



## Discussion
Editor: Jong-Hyuk Im (임종혁)

+ 윤리적 이슈로 인해 살아있는 사람의 홍채는 획득하지 않았으나 5시간이 지난사람의 홍채 정보는 꼭 획득하였음.
+ 상업용 홍채 인식 제품에도 성능의 차이가 크게 발생하였으며(IrisCore >> MIRLIN), 학계의 결과는 특정 상황에서 좋은 성능을 보이기도 하였음.
+ 여러 제품의 인식 성능을 직접 비교하기보다는, 시각화하여 제공한 논문임
+ 홍채에 국한된 내용인지는 모르겠으나, RGB 채널을 분리하여 얻은 각각의 이미지를 활용하는 것은 다른 이미지 기반 인증에도 적용하여 테스트 해볼수 있을 것으로 보임.


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
