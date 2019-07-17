---
title: Session 1. Generation of Cancelable Iris Templates via Randomized Bit Sampling
date: 2019-07-15 00:00:00 Z
description: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_title: Session 2
card_teaser: Generation of Cancelable Iris Templates via Randomized Bit Sampling
card_position: 2
icon: fa-server
categories: [seminars,07-15-2019-morning-seminar,presentation]
tags: [TIFS, 2019, TIFS2019, Cancelable biometrics, iris, security, locality sensitive hashing]
sidebar: morning-seminar
layout: default
slug: ms-presentation-hy-july-15-2019
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Hee-Yong Kwon (권희용)
+ 2019-07-15

## [Generation of Cancelable Iris Templates via Randomized Bit Sampling](https://inhaucs.github.io/seminars/07-xx-2019-morning-seminar/presentation/ms-presentation-hy-july-xx-2019.html)

### Information of the paper [(Link)](https://ieeexplore.ieee.org/abstract/document/8672919)
+ Authors: Debanjan Sadhya (ABV-Indian Institute of Information Technology); Balasubramanian Raman (Indian Institute of Technology Roorkee)
+ **Journal** name: IEEE Transactions on Information Forensics and Security (Volume 14, Issue 11)
+ Published date: 2019-03-22
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8672919)


### Abstract
Iris-based biometric models are widely recognized to be one of the most accurate forms for authenticating individual identities. Features extracted from the captured iris images (known as IrisCodes) conventionally get stored in their native format over a data repository. However, from a security aspect, the stored templates are highly vulnerable to a wide spectrum of adversarial attack forms. The study in this paper addresses this issue by introducing a privacy-preserving and secure biometric scheme based on the notion of locality sensitive hashing (LSH). In this paper, we have generated cancelable IrisCode features, coined as locality sampled code (LSC), which simultaneously provides strong security guarantees and satisfactory system performance. The functionality of our proposed framework pivots around the fact that intra-class IrisCode samples are “close” to each other, due to which they hash to the same location. Alternatively, the inter-class IrisCodes features are comparatively dissimilar and consequently hash to different locations. We have rigorously examined the intrinsic properties of the LSCs by estimating the intra-class and inter-class collision probabilities for two distinct IrisCodes. Furthermore, we have formally analyzed the security guarantees of non-invertibility, revocability, and unlinkability in our model by establishing various bounds on the adversarial success probability. Extensive empirical tests on the CASIAv3 and IITD benchmark iris databases demonstrate the superior performance of our proposed model, for which we have obtained the best EERs of 0.105% and 1.4%, respectively.


## Introduction (Korean)
+ 홍채는 나이에 따른 변화가 없고, false match에 강점이 있다는 장점이 있으며, 이로 인해 인증 시스템에 적합
+ 홍채 이미지로부터 추출된 feature는 주로 ***IrisCode*** 라는 bit string으로 표현됨 [[D16]]
+ [[RU11]]에는 biometric system에 대한 여러 공격이 소개되어 있음
  + Privacy invasion, masquerade attack, replay attack, and identity theft
  + 이에 따라 대응책으로 **Biometric Template Protection (BTP)** 에 대한 연구가 진행됨 -> 원본 데이터 대신 변환된 데이터를 저장하여 대응하는 방법
+ 본 논문에서 소개하는 내용은 BTP의 하나인 Cancelable biometrics 를 적용
  + 원본 데이터에 특정 함수를 사용하여 왜곡하는 방법
    + 변환된 데이터는 쉽게 역연산되지 않아야 함
    + 인식 성능이 좋아야 함
  + 효과적인 cancelable biometrics scheme 은 다음을 만족
    + Unlinkability: 같은 데이터로부터 변환된 두 데이터를 구분할 수 없어야 함 -> Countermeasure of cross-matching based attack
    + Non-invertibility: One-way 변환으로 인한 역연산 불가
    + Revocability: (폐지 가능성), 처음 등록한 데이터가 탈취당할 경우, 새로운 변환 데이터를 생성할 수 있어야 함
    + Performance: Baseline 모델에 비해 성능이 많이 떨어지지 않아야 함

[D16]: <https://ieeexplore.ieee.org/abstract/document/7328287> "J. Daugman, “Information theory and the iriscode,” IEEE Trans. Inf. Forensics Security, vol. 11, no. 2, pp. 400–409, Feb. 2016."
[RU11]: <https://jis-eurasipjournals.springeropen.com/articles/10.1186/1687-417X-2011-3> "C. Rathgeb and A. Uhl, “A survey on biometric cryptosystems and cancelable biometrics,” EURASIP J. Inf. Secur., vol. 2011, no. 1, p. 3, Sep. 2011. [Online]. Available: https://link. springer.com/article/10.1186/1687-417X-2011-3"

+ Contributions
  + Randomized bit sampling 을 사용하여 IrisCode에 적용할 Locality-sensitive hashing (LSH) 생성 $\rightarrow$ 이를 Locality Sampled Code (LSC) 라 명명 : Template
    + LSC는 modulo threshold를 사용하여 비가역연산(Non-invertible)
  + CASIAv3 and IITD 데이터베이스에 대해 분석


## Related Work
+ Cancelable iris scheme은 두 개의 카테고리로 나눌 수 있음: Salting & non-invertible transform
+ Salting
  + 데이터 변환을 위해 원본 biometrics 데이터와 보조 데이터(e.g., password, token)를 조합
    + One of the first study: [[CJL06]] - inner-product 사용
    + Two salting techniques: [[ZRC08]] - 인공적인 시드를 IrisCode에 더해서 변환 & 임의의 키와 XOR 연산
    + Random Projection: [[TY07], [PPC+10]] - 원본 biometrics 를 임의의 수의 부분으로 나누어 projection하는 방법
+ Non-invertible transform
  + one-way transformation functions 을 기반으로 수행
    + Tokenless iris template protection model: [[OTN10]] - **Bio-encoding**
    + [[OTN10]]의 문제점 분석: [[L12]]
    + Use modified Bloom filters for generating cancelable iris templates: [[RBB13]], [[RB14]]
    + Modified Bloom filters 를 사용한 연구 공격: [[HMP14]] - Cross-matching based attacks


## Preliminaries
+ Locality Sensitive Hashing (LSH)
  + 높은 차원의 데이터를 차원 축소하는 해시
  + 비슷한 데이터에 대해 collision을 높임
    + 이로 인해 비슷한 데이터는 같은 값으로 해시됨
+ Bit sampling based LSH
  + LSH family를 만드는 효율적인 방법인 Bit sampling 사용한 LSH를 사용

[CJL06]: <https://www.sciencedirect.com/science/article/pii/S107731420600004X> "C. S. Chin, A. T. B. Jin, and D. N. C. Ling, “High security iris verification system based on random secret integration,” Comput. Vis. Image Understand., vol. 102, no. 2, pp. 169–177, 2006."
[ZRC08]: <https://ieeexplore.ieee.org/abstract/document/4761886> "J. Zuo, N. K. Ratha, and J. H. Connell, “Cancelable iris biometric,” in Proc. 19th Int. Conf. Pattern Recognit., Dec. 2008, pp. 1–4."
[TY07]: <https://ieeexplore.ieee.org/abstract/document/4305292> "A. B. J. Teoh and C. T. Yuang, “Cancelable biometrics realization with multispace random projections,” IEEE Trans. Syst., Man, Cybern. B, Cybern., vol. 37, no. 5, pp. 1096–1106, Oct. 2007."
[PPC+10]: <https://ieeexplore.ieee.org/abstract/document/5495383> "J. K. Pillai, V. M. Patel, R. Chellappa, and N. K. Ratha, “Sectored random projections for cancelable iris biometrics,” in Proc. IEEE Int. Conf. Acoust., Speech Signal Process., Mar. 2010, pp. 1838–1841."
[OTN10]: <https://ieeexplore.ieee.org/abstract/document/5596070> "O. Ouda, N. Tsumura, and T. Nakaguchi, “Tokenless cancelable biometrics scheme for protecting iris codes,” in Proc. 20th Int. Conf. Pattern Recognit., Aug. 2010, pp. 882–885."
[L12]: <http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.736.2059&rep=rep1&type=pdf> "P. Lacharme, “Analysis of the iriscode bioencoding scheme,” Int. J. Comput. Sci. Secur., vol. 6, no. 5, pp. 315–321, Oct. 2012."
[RBB13]: <https://ieeexplore.ieee.org/abstract/document/6612976> "C. Rathgeb, F. Breitinger, and C. Busch, “Alignment-free cancelable iris biometric templates based on adaptive bloom filters,” in Proc. Int. Conf. Biometrics, Jun. 2013, pp. 1–8."
[RB14]: <https://www.sciencedirect.com/science/article/pii/S0167404814000029> "C. Rathgeb and C. Busch, “Cancelable multi-biometrics: Mixing iriscodes based on adaptive bloom filters,” Comput. Secur., vol. 42, pp. 1–12, 2014."
[HMP14]: <https://ieeexplore.ieee.org/abstract/document/7029413/> "J. Hermans, B. Mennink, and R. Peeters, “When a bloom filter is a doom filter: Security assessment of a novel iris biometric template protection system,” in Proc. Int. Conf. Biometrics Special Interest Group, Sep. 2014, pp. 1–6."


## Methodology
{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-15-fig-generation_LSCs.png" legend="Generation of LSCs." width="75%" %}
+ 홍채 이미지로부터 추출된 IrisCode 를 $n$ 개의 블록으로 나눔
+ $l$ 개의 bit sampling hash function 을 사용하여, $l$ 개의 $k$-bit 샘플링
  + $l$, $k$ 이 커질수록, 안전성은 높아지고 성능은 낮아짐
+ 샘플링된 데이터들을 10진수로 표현 후, modulo 연산 $\rightarrow$ non-invertible


## Experimental Results and Analysis
+ databases
  + [CASIAv3-Iris-Interval database](http://biometrics.idealtest.org/)
  + IIT Delhi Iris database [[KP10]]
+ Pre-processing
  + Segmentation process: [[UW12]]
  + Feature extraction process: [[MTW+04]] $\rightarrow$ 04년도 논문을 사용?
+ Results

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-15-tbl_EER.png" legend="Variation of EER (%)." width="75%" %}

{% include articles/figure.html url="/assets/img/heeyong/2019/2019-07-15-tbl_comp.png" legend="Comparative Analysis." width="75%" %}
+ CASIAv3 데이터셋에 대해 실험한 결과는 기존의 논문들보다 낮은 EER을 보이며, IITD의 경우도 준수함
  + IITD에서 다른 연구보다 높지 않은 이유에 대해, 다른 연구에서는 Multiple biometric characteristics에 기반한 fusion strategy를 사용했는데 본 연구에서는 사용하지 않았기 때문이라고 함

[KP10]: <https://www.sciencedirect.com/science/article/pii/S0031320309003343> "A. Kumar and A. Passi, “Comparison and combination of iris matchers for reliable personal authentication,” Pattern Recognit., vol. 43, no. 3, pp. 1016–1026, 2010."
[UW12]: <https://ieeexplore.ieee.org/abstract/document/6199821> "A. Uhl and P. Wild, “Weighted adaptive hough and ellipsopolar transforms for real-time iris segmentation,” in 5th IAPR Int. Conf. Biometrics, Mar./Apr. 2012, pp. 283–290."
[MTW+04]: <https://ieeexplore.ieee.org/abstract/document/1298831> "L. Ma, T. Tan, Y. Wang, and D. Zhang, “Efficient iris recognition by characterizing key local variations,” IEEE Trans. Image Process., vol. 13, no. 6, pp. 739–750, Jun. 2004."
<!-- []: <> "" -->


### Points to note
+ 취소가능한 템플릿을 만드는 새로운 방법 제시
  + Bit sampling based LSH 사용
+ 실제 홍채 데이터셋에 대한 실험 및 분석 수행



## Discussion


{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
