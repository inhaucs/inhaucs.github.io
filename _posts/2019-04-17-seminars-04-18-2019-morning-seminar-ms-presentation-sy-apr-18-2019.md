---
title: "Session 3. Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
date: 2019-04-17 00:00:00 Z
description: "Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
card_title: Session 3
card_teaser: "Efficient Function-Hiding Functional Encryption: From Inner-Products to Orthogonality"
card_position: 3
icon: fa-server
categories: [seminars,04-18-2019-morning-seminar,presentation]
tags: [RSA, 2019, RSA2019, CT-RSA, CT-RSA2019, functional encryption, FE, function-hiding, orthogonality]
sidebar: morning-seminar
layout: default
slug: ms-presentation-sy-apr-18-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Seong-Yun Jeon (전성윤)
+ 2019-04-18

## Information of the paper
+ Authors: Manuel Barbosa(INESC TEC and FCUP, Portugal), Dario Catalano(Universit`a di Catania, Italy), Azam Soleimanian(Kharazmi University of Tehran, Iran and École Normale Supérieure, Paris, France), and Bogdan Warinschi(University of Bristol, Bristol, UK)
+ Conference name: The Cryptographers' Track at the RSA Conference 2019
+ Published date: 2019-03-04
+ [Paper Link](https://doi.org/10.1007/978-3-030-12612-4_7)

## Abstract
We construct functional encryption (FE) schemes for the orthogonality (OFE) relation where each ciphertext encrypts some vector ***x*** and each decryption key, associated to some vector ***y***, allows to determine if ***x*** is orthogonal to ***y*** or not. Motivated by compelling applications, we aim at schemes which are function hidding, i.e. ***y*** is not leaked.
Our main contribution are two such schemes, both rooted in existing constructions of FE for inner products (IPFE), i.e., where decryption keys reveal the inner product of ***x*** and ***y***. The first construction builds upon the very efficient IPFE by Kim et al. (SCN 2018) but just like the original scheme its security holds in the generic group model (GGM). The second scheme builds on recent developments in the construction of efficient IPFE schemes in the standard model and extends the work of Wee (TCC 2017) in leveraging these results for the construction of FE for Boolean functions. Conceptually, both our constructions can be seen as further evidence that shutting down leakage from inner product values to only a single bit for the orthogonality relation can be done with little overhead, not only in the GGM, but also in the standard model.
We discuss potential applications of our constructions to secure databases and provide efficiency benchmarks. Our implementation shows that the first scheme is extremely fast and ready to be deployed in practical applications.

## Summary (Korean)

## Details
### Contents of the paper
#### Research questions
+ **(RQ1)** 가변적인 암호 만료 정책 (password policy of variable expiration)이 사용자가 선택하는 암호에 어떠한 영향을 주는가?
+ **(RQ2)** 새로운 암호 규칙 및 정책의 도입에 대해 다른 대답을 하는 식별 가능한 그룹이 있는가?

#### RQ1: 가변적인 암호 만료 정책이 사용자가 선택하는 암호에 어떠한 영향을 주는가?

+ 1979년, 대학에서 컴퓨터 사용자의 사용 시간 위임을 위해 처음 적용되었던 암호 만료 (The expiration of passwords)는, 이후 범정부 지침을 통해 전 세계적으로 적용되었다.
+ 연구자, 정책 설계자 등 대부분의 사람은 암호가 오래 살아있으면 ("alive") 손상 위험이 높다고 생각하고 있어, 암호 만료 정책에 신경을 쓰고 있었다.
+ 그러나, 2010년[[ZMR10]]과 2015년[[CO15]]에 발표된 논문들에서 암호의 만료가 안전성을 향상하는데 도움이 되지 않는다는 이론적인 연구들이 발표되었다.
+ 이러한 이전 연구들에서 알려진 바에 따르면, 암호의 온라인 공격에는 $10^6$의 추측 공격이 필요하며 오프라인 공격에는 $10^{14}​$의 추측 공격이 필요한데, 오프라인 공격까지 해결할 수 있는 암호는 사람이 기억하기 매우 어려워 실용적인 복잡도로 볼 수 없다는 문제점이 여전히 존재한다.
+ 본 논문에서는 이러한 암호 자체의 복잡도 보다는, 전체적인 시스템에서의 관점을 통해 암호의 복잡도와, 만료 시점 이에 따른 이익과 비용을 계산하는 연구가 필요하다는 점을 강조하였다.
  + 예를 들어, 기억하기에 너무 많은 암호가 있으면, 재사용을 하는 것이 좋고, 계정의 그룹화를 하는 등의 방식을 적용할 수 있다.
+ 본 논문에서는 다음과 같은 새로운 정책을 대학 구성원에게 적용하는 실험을 수행하였다.
  + Variable expiration
  + 8-30 characters
  + Can't be the same as previous
  + 3 out of:
    + Lowercase character
    + Uppercase character
    + Numbers
    + Symbols
  + Discount if substring part of 306k dictionary.
+ 그 결과 샤넌 엔트로피가 50 bits인 경우에는 만료일이 100일, 120 bits인 경우에는 만료일이 350일이 되었다.
+ 사용자는 암호를 처음 설정하거나, 변경 및 재설정 할 때 해당 정책에 따라 가변적인 암호 수명을 얻게 된다.

##### The data

+ 실험을 통해 획득한 데이터는 몇 가지 흥미로운 양상을 보였다.
+ 먼저, 만료되지 않은 암호에 대한 사용자의 암호 변경(Change, 이전 암호를 기억하고 있으며 변경하는 것)은 암호 만료를 알리는 메일이 보내진 최근 시점에 굉장히 높은 변경률을 보였으며, 이를 통해 많은 사용자가 암호 만료 기간 이전에 이미 설정된 암호를 기억하고 있으며, 의도적으로 수정한다는 것을 알 수 있었다.
+ 상기 내용은 Figure 5에 나타나며, 암호 재설정(Reset, 이전 암호를 모른 상태로 새로운 암호로 재설정하는 것)보다 많이 이루어지고 있다는 것이다.
  + 200k password changes
  + 115k password resets
+ 또한, Figure 2에 따르면 암호 reset은 신학기에 주로 이루어지는 것을 알 수 있었다.
+ 이러한 결과에도 불구하고 전체 사용자 중 66%는 적어도 한 번 reset을 한 것으로 나타났고, 평균적으로 한 사람당 1.1번의 resets과 2.4번의 changes를 한 것으로 나타났다.
  + 주된 reset의 이유는 암호를 잊어버리거나, 만료된 것 이었다.
+ 이 실험에서 reset을 하는 비용은 change에 매우 크게 설정되어 있다. (실제 help desk에 연락하거나, 휴대폰 인증 기반의 시스템을 이용해야 함)
  + 그 결과, 여러 번의 reset을 경험한 사용자는 보다 쉬운 수준의 암호를 선택하는 경향이 있었다.
  + 휴가에 다녀왔을 시.. 많은 사람이 reset을 수행한다.
+ 또한, Figure 1에 따르면 모든 비밀번호의 강도 분포는 대부분 100~225일 사이의 uniform distribution에 가깝고, 평균적으로 change된 암호는 147.74일, reset된 암호는 146.6일의 안전성을 지니는 것으로 확인되었다.
+ Figure 8에 따르면, 사용자들이 시스템에 익숙해짐에 따라 암호의 평균 강도가 145.5일에서 170.1일로 증가하는 것을 확인할 수 있는데, 사용자가 제안하는 암호 정책에 천천히 적응하고 궁극적으로 암호를 강화하여 암호 수명을 늘릴 수 있는 능력을 활용한다는 것을 의미한다.



#### RQ2: 새로운 암호 규칙 및 정책의 도입에 대해 다른 대답을 하는 식별 가능한 그룹이 있는가?

+ 본 논문에서는 정책이 암호의 안전성에 기인하는 부분에 대해서도 분석하였다.
  + 논문에서도 학교이기 때문에 인류통계학적인 정보가 포함되어 가능했다며 "행운"으로 표현했다.
+ 그 결과, Figure 9에 나타나 있듯 대학별로 큰 차이를 보이었다.
  + 수학, 물리학과나 공대 등은 높은 안전성을 선호
  + 교육학과 쪽은 매우 낮은 안전성을 선호
+ 또한, Figure 10에 나타나 있듯 직위별로 다른 경향을 보였다.
  + 교직원은 가장 높은 안전성을 선호했고, 연구를 하는 학생 또한 높은 위치에 있었다.
  + 학부생이나 졸업생은 매우 낮은 안전성을 선호하였는데, 특이한 점은 연구를 수행하지 않는 대학원생은 가장 낮은 안전성을 선호하고 있는 것으로 확인되었다.



#### Conclusion

본 논문의 실험 결과에 따르면, 10만명의 사용자에게 새로운 비밀번호 정책이 미치는 영향을 평가했으며, 이러한 개입은 100일 정도의 시간이 소요되어 사람들에게 적응되기 시작했고, 초기 평균인 146일 (63 bits) 보다 더 높은 170일 (70 bits)의 암호 라이프 사이클로 변화하기 위해 12개월 이상이 소요된 것을 확인할 수 있었다.

이 정책은 개별 사용자에게 명백한 비용과 잠재적인 비용을 모두 제공하는데, 그중 66%의 사용자가 암호를 여러 번 변경(change)하는 대신 재설정(reset)하는 것을 경험하였다.

평균적으로 사용자는 연구를 수행하는 동안 3.5개의 암호를 가졌으며, 재설정(reset) 절차의 구현에 따라 실제 사용자가 인식하는 비용이 변화할 수 있다고 주장하고 있다. 또한, 실험의 분석 결과 정책 참여 수준이 인류학적 분류에 따라 다르게 나타났다.

이 논문에서 제안된 정책은 사용자에게 강요하는 것이 아닌, 만료 기간과 암호 관리 비용의 균형을 사용자에게 부여하더라도 온라인 공격에 대한 충분한 암호의 안전성을 확보하는 데 시간이 필요할 뿐 정착시킬 수 있다는 가능성을 확인하였다.



### Points to note

+ 이 논문의 실험은 실제 환경에서의 실제 서비스(대학 IT 서비스)에 적용하여 진행하였으며, 90여명의 유저 피드백을 논문에 정리하여 포함했으므로, 추후 이러한 실험 중심의 논문을 작성할 때 참조할 수 있을 것으로 보인다. 또한, IRB 승인을 받았다는 내용 또한 포함되어 있다. (피드백 부분에 포함되어 있음)
+ 이동 평균을 사용하는 이유는, 이 논문의 경우에서는 주말에 학교 IT 서비스를 대부분 사용하지 않기에 경향에 큰 노이즈로 작용할 수 있기 때문이었다. 추후 시계열 데이터의 분석을 할 경우 이를 꼭 고려할 것을 권장한다.
+ 인터뷰를 인용할 때, 사람의 말 자체를 인용하였으며, 이때 E## (Employee/Staff)나 S## (Student) 등으로 익명화하여 표기하는 것을 확인할 수 있었다. 나중에 적용 가능한 부분으로 보인다.


[ZMR10]: <https://dl.acm.org/citation.cfm?doid=1866307.1866328> "The security of modern password expiration: an algorithmic framework and empirical analysis"
[CO15]: <https://link.springer.com/article/10.1007%2Fs10623-015-0071-9> "Quantifying the security advantage of password expiration policies"

## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
