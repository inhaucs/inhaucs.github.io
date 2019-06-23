---
title: A4NT. Author Attribute Anonymity by Adversarial Training of Neural Machine Translation
date: 2019-06-24 00:00:00 Z
description: A4NT. Author Attribute Anonymity by Adversarial Training of Neural Machine Translation
card_title: Session 5
card_teaser: A4NT. Author Attribute Anonymity by Adversarial Training of Neural Machine Translation
card_position: 5
icon: fa-server
categories: [seminars,06-24-2019-morning-seminar,presentation]
tags: [USENIX, 2018, USENIX2018, NPL, Anomymity, obsfucation, Neural Network]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-june-24-2019
permalink: /:categories/:slug.html
---

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-06-24

## [A4NT: Author Attribute Anonymity by Adversarial Training of Neural Machine Translation](https://inhaucs.github.io/seminars/06-24-2019-morning-seminar/presentation/ms-presentation-jh-june-24-2019.html)

### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/shetty)
+ Authors: Rakshith Shetty; Bernt Schiele; and Mario Fritz; Max Planck (Institute for Informatics)
+ **Conference** name: USENIX Security 2018
+ Published date: 2018-08-17
+ [Paper Link](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-shetty.pdf)


### Abstract
Text-based analysis methods enable an adversary to reveal privacy relevant author attributes such as gender, age and can identify the text's author. 
Such methods can compromise the privacy of an anonymous author even when the author tries to remove privacy sensitive content. 
In this paper, we propose an automatic method, called the Adversarial Author Attribute Anonymity Neural Translation ($\text{A}^{4}\text{NT}$), to combat such text-based adversaries. 
Unlike prior works on obfuscation, we propose a system that is fully automatic and learns to perform obfuscation entirely from the data. 
This allows us to easily apply the $\text{A}^{4}\text{NT}$ system to obfuscate different author attributes. 
We propose a sequence-to-sequence language model, 
inspired by machine translation, and an adversarial training framework to design a system which learns to transform the input text to obfuscate the author attributes without paired data. 
We also propose and evaluate techniques to impose constraints on our $\text{A}^{4}\text{NT}$ model to preserve the semantics of the input text. 
$\text{A}^{4}\text{NT}$ learns to make minimal changes to the input to successfully fool author attribute classifiers, while preserving the meaning of the input text. 
Our experiments on two datasets and three settings show that the proposed method is effective in fooling the attribute classifiers and thus improves the anonymity of authors.

## Summary (Korean)
글 저자의 개인 정보를 난독화하는 자동화된 프레임워크로 GAN을 이용함.

## Main explanation

### Motivation
Text-based 분석 방법(자연어 처리: Natural Language Processing (NLP))을 이용하면, 공격자(adversary)가 저자의 성별, 나이와 같은 개인정보 관련 저자 속성(attributes)들을 복원(reveal)하여 글의 작성자(저자)를 식별할 수 있다.
최근의 유명한 사례로 이러한 authorship attribution tools은 J.K Rowling이 익명()으로 작성한 A Cuckoo's Calling의 진짜 저자임을 확인하는데 사용되기도 하였다 [[Joula]].
이러한 방법은 익명의 저자가 자신의 민감한 정보를 제거하려할 때에도 그 저자의 개인정보를 침해할 수 있다.
**즉, 이러한 공격을 막는 방법이 필요하다.**

### Proposed method
이 논문에서는 이러한 텍스트 기반의 공격자에 대응하기 위해 Adversarial Author Attribute Anonymity Neural Translation (A^4NT)이라는 자동화된 방법을 제안한다.
이 방법은 이전에 수행된 난독화(obfuscation)에 관한 연구와는 달리, 데이터로부터 완전히 자동(**fully automatic**)으로 난독화를 수행한다.
즉, A4NT 시스템을 간단히 적용하는 것으로 다양한 저자의 속성(attributes)을 난독화할 수 있다.
+ A4NT는 machine translation으로부터 영감을 얻은 seq2seq 언어 모델 및
  + machine translation: 구글 번역기와 같은 자동 번역 방법
  + seq2seq language model: sequence-to-sequence language model로, 번역기와 같은 Encoder/Decoder를 이용한 변환 모델임
  
+ 입력된 텍스트를 변환하여 paired data없이 저자의 속성을 난독화하는 시스템을 설계하기 위한 Adversarial training framework를 제안한다.
  + Adversarial training: GAN으로 생성된 이미지를 training set에 포함시키는 방법, 최근까지는 가장 현실적인 방법 중 하나라 함.
  
#### Goals
결과적으로, 이 논문의 목표는 입력 텍스트의 의미를 보존하면서도, Author Attributes Classifier를 속일 수 있도록, 입력 텍스트를 적절히 자동으로 변환하도록 학습하는 기계 번역 모델을 제안하고, 이를 이용한 Encoder/Decoder로 난독화를 수행하는 자동화된 시스템을 만드는 것이다.

### Kewords of related works
+ Authorship and attribute detection
+ Authorship obfuscation
+ Machine translation
+ Generative adversarial networks (GAN)
+ Attacks against machine-learning models

### Threat model and the system
이 시나리오에서 블로그 포스트, 트위터 글 등과 같이 대량의 글을 공격자가 수집할 수 있는 상황이며, 제안된 시스템은 자동적으로 사용자의 writing style을 숨겨 age group, gender, identity를 난독화한다.

### GAN framework to train the A4NT network.

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-overview.PNG" legend="Overview of A4NT GAN framework" %}

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-attribute-classifier.PNG" legend="Block diagram of the attribute classifier network" %}


### Experiments

#### Dataset
+ Blog dataset
+ Political speech dataset

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-datasets.PNG" legend="Datasets" %}

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-datasets-detail.PNG" legend="Details of datasets" %}

#### Performance of attribute classifiers.

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-f1scores-of-attribute-classifiers.PNG" legend="F1-scores of the attribute classifiers." %}


#### Performance of obfuscation

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-related-works.PNG" legend="Related Works" %}

Example: Age

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-06-24-fig-performance-age.PNG" legend="obfuscation performance - age." %}

+ Meteor: 유사성점수 metric [[METEOR]]으로, 0이면 완전히 다른, 1이면 완전히 동일한 문장을 의미함.

### Conclusion
+ Automatic authorship obfsucation framework A4NT
+ Deep learning based solution which learns transformations from data
+ Learning from un-paired data opens up the solution to other settings.


### Points to note
+ GAN의 좋은 사례 중 하나라고 

## Discussion


[Joula]: https://goo.gl/mkZai1
[METEOR]: https://www.cs.cmu.edu/~alavie/METEOR/pdf/meteor-1.5.pdf


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
