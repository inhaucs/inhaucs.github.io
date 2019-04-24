---
title: "Session 5. Surveylance: Automatically Detecting Online Survey Scams"
date: 2019-04-23 00:00:00 Z
description: "Surveylance: Automatically Detecting Online Survey Scams"
card_title: Session 5
card_teaser: "Surveylance: Automatically Detecting Online Survey Scams"
card_position: 5
icon: fa-server
categories: [seminars,04-25-2019-morning-seminar,presentation]
tags: [SNPC, 2018, SNPC2018, ]
sidebar: morning-seminar
layout: default
slug: ms-presentation-th-apr-25-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Tae-Hyun Kim (김태현)
+ 2019-04-25

## [Surveylance: Automatically Detecting Online Survey Scams](https://inhaucs.github.io/seminars/04-25-2019-morning-seminar/presentation/ms-presentation-th-apr-25-2019.html)

#### Information of the paper [(Link)](https://ieeexplore.ieee.org/document/8418597)
+ Authors: Amin Kharraz, William Robertson, Engin Kirda(Northeastern University, University of Illinois Urbana-Champaign)
+ Conference name: 2018 IEEE Symposium on Security and Privacy
+ Published date: 2018-05-20
+ [Paper Link](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8418597)

#### Abstract
Online surveys are a popular mechanism for performing market research in exchange for monetary compensation. Unfortunately, fraudulent survey websites are similarly rising in popularity among cyber-criminals as a means for executing social engineering attacks. In addition to the sizable population of users that participate in online surveys as a secondary revenue stream, unsuspecting users who search the web for free content or access codes to commercial software can also be exposed to survey scams. This occurs through redirection to websites that ask the user to complete a survey in order to receive the promised content or a reward.
In this paper, we present SURVEYLANCE, the first system that automatically identifies survey scams using machine learning techniques. Our evaluation demonstrates that SURVEYLANCE works well in practice by identifying 8,623 unique websites involved in online survey attacks. We show that SURVEYLANCE is suitable for assisting human analysts in survey scam detection at scale. Our work also provides the first systematic analysis of the survey scam ecosystem by investigating the capabilities of these services, mapping all the parties involved in the ecosystem, and quantifying the consequences to users that are exposed to these services. Our analysis reveals that a large number of survey scams are easily reachable through the Alexa top 30K websites, and expose users to a wide range of security issues including identity fraud, deceptive advertisements, potentially unwanted programs (PUPs), malicious extensions, and malware.

## Summary (Korean)
+ Surveylance로 온라인 설문조사와 관련된 웹사이트를 통한 사기(개인정보 탈취, 사기성 광고, 원치않는 프로그램 설치후 가입비 요구, 악성코드 감염 등)를 머신러닝을 이용해서 자동으로 식별한다. 이를 이용해 8623개의 웹사이트를 식별하는데 성공했다. 또한, 온라인 설문조사 사기 관련 기능을 조사하고 이러한 서비스에 노출된 사용자들을 정량화한 첫 분석을 해냈다. 

## Details
+ 대부분의 인터넷 사용자는 최소 한번 이상 설문조사 메일을 받았을 것이다. 이를 이용해 설문조사 참여를 유도하며 기프트카드나 온라인서비스 무료 이용 또는 iPad와 같은 전자제품을 보상으로 약속한다. 이러한 점으로 마케팅 리서치 회사에 유용한 정보를 제공하지만, 공격자에게도 수익성 있는 공격을 가능하게 한다. 개인정보 탈취 및 악성코드 감염 등 불법 활동이 원활하다.
+ 본 논문을통해 설문조사 사기가 심각하고 보안을 위협할 수 있다는 경헙적 증거를 보여줬다는 것이다.
+ 일반석인 피싱이나 악성 코드 웹사이트와 같은 위협을 유발하지만 연구가 많이 되지 않아서 공격 탐지 방법에 대한 정보가 거의 없다.
+ 공격자에 의한 악의적 행위 뿐 아니라 사기의 피해자를 식별하기 위한 경험적 연구를 수개월간 실행했다. 
+ DevTool Extension API를 기반으로 크롤링 툴을 개발했다. Classification Module을 만들기 위해 테스트한 결과 SVM보다 Random forest classifier가 낮은 false positive와 효율적인 탐지를 보여주었다. Random forest 구현을 위해 scikit-learn을 사용했다. 주어진 HTML 페이지에서 natural language data를 추출하기 위해 Python Natural Language ToolKit(NLTK)을 사용했다. 이후 PyQuery를 이용하여 HTML 소스코드의 전체 길이와 링크의 텍스트 길이를 계산했다. 

+ IP주소나 도메인 이름과 같이 쉽게 피할 수 있는 특징에 의존하지 않고, 입력 타입이나 특정 이미지와 같은 특징을 타겟팅한다. 탐지 모델 구성을 위해 웹사이트 내용, 네트워크 트래픽, 위젯 및 페이지의 전반적인 정보를 추출한다. 


#### Feature Set
+ 1) indicative images: 일반적으로 기본페이지는 잘 설계가 되어있는데, 보통 이미지를 만족 보장 또는 소득 보장을 나타내는 로고와 같은 설문 조사를 작성하도록 유도한다. 이러한 이미지가 다른 특징과 같이 있다면 좋은 지표가 된다. 
+ 2) user input fields: redirection 하기전 사용자의 집주소, 이메일 주소, 전화번호와 같은 개인정보를 입력하도록 하는데, 83% 이상의 샘플에서 개인 정보 텍스트 필드가 4개 이상이였다. 사용자 입력 필드의 총 수를 숫자 특징으로 본다.
+ 3) third-party scripts: survey gateway에서는 상당히 많은 third-party script(예: 광고)를 포함한다. 전체 링크 중 third-party links의 비율을 특징으로 사용한다. 
+ 4) link length: third-party links의 길이의 평균과 최대 길이를 계산하여 특징으로 사용한다.
+ 5) website structure: 일반적인 웹사이트는 HTML, CSS, 이미지 및 JavaScript 파일로 구성되어 디렉토리 트리를 형성하지만, survey gateway는 그러지 않은경우가 많아서 boolean 값으로 사용
+ 6) web content: survey gateway의 경우 상당부분 사용자가 볼수 없는 URL을 포함한다. 이 비율을 특징으로 사용한다.
+ 7) sequence of words: 보장된 보상, 쉬운 소득과 같은 문구가 얼마나 들어가있나를 특징으로 사용한다.
+ 8) redirection mechanisms: redirection이 발견되면 boolean 값 1을 특징으로 사용한다.
+ 9) third-party requests: 전체 HTTP 요청의 수에 대한 third-party domain의 수의 비율과 전체 HTTP 요청의 수를 특징으로 사용한다.
+ 10) third-party responses: third-party 소스로부터 들어오는 트래픽의 비율을 특징으로 사용한다. 
+ 11) image size: 신뢰를 주기위해 여러 로고와 보상이미지를 넣는데 survey gateway에서는 이러한 이미 크기가 평균 2KB로 작다는것을 관찰할 수 있었다. 발견된 이미지의 평균 및 최대크기를 특징으로 사용한다. 
+ 12) number of frames: iframe에 광고를 포함하는것이 일반적이였음을 관찰하였고, frame 및 iframe 수를 특징으로 사용한다. 

#### surveylance의 과정 및 결과
+ 웹사이트를 크롤링하고, network trace를 수집하고, classification을 수행한다. 이후 survey gateway 목록을 리스트화한다. 

+ survey gateways: 설문조사를 하기 위한 사이트로 유도하는 광고
+ survey publishers: 해당 광고에 해당하는 설문조사를 진행하기 위해 페이지 리디렉션, 개인정보 수집 및 사이트 가입 유도

+ 새로 출시된 영화, 라이브 스포츠 이벤트, 무료 콘텐츠 다운로드와 같은 사기성 링크를 클릭 후 설문조사를 진행하고, 약속된 보상을 받기 전 개인 정보 입력, 다른 악의적 페이지로의 리디렉션, PUP 다운로드하도록 유도한다.(PUP 배포가 다른 유형의 악성 프로그램보다 많음을 보였다.)

+ 8,623개의 웹사이트를 식별하고, 318,219건의 사기를 발견했다. 결과중 40% 이상이 Alexa의 30,000개 웹사이트를 통해 접근 가능하다.
+ 공격자들은 주로 브라질, 동유럽, 러시아에 인프라를 호스팅한다.
+ True positive: 94.8%, Flase positive: 1.2%

#### 한계
+ 공격자가 탐지를 피하기 위해 전략을 변경할 경우 대처가 늦어질수밖에 없다.
+ 사기꾼의 금전적 이득의 범위는 알 수 없다. 
+ survey gateway는 찾더라도 survey publisher가 해당 정보를 어디에 사용했는지는 알 수 없다.


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
