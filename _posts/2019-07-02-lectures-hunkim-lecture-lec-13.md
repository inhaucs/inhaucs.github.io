---
title: Lecture 13. TensorFlow를 AWS에서 GPU와 함께 돌려보자
date: 2019-07-02 00:00:00 Z
description: Lecture 13
card_title: Lecture 13
card_teaser: TensorFlow를 AWS에서 GPU와 함께 돌려보자
card_position: 14
icon: fa-server
categories: [lectures,hunkim-lecture,contents]
sidebar: hunkim-lecture
layout: default
slug: hunkim-lecture-lec-13
permalink: /:categories/:slug.html
use_math: true
---

{% assign product = 'ce' %}
{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Writer
+ Hee-Yong Kwon (권희용)
+ 2019-09-26

### Information of the lecture
#### [Youtube(Lecture)](https://www.youtube.com/watch?v=-SHPG_KMUkQ&list=PLlMkM4tgfjnLSOjrEJN31gZATbcj_MpUm&index=41)

### Lecture
#### TensorFlow를 AWS에서 GPU와 함께 돌려보자
+ Tensorflow를 Amazon Web Service에서 실행하는 방법
+ Deep Network은 학습에 많은 데이터가 필요하고, forward/backward propagation을 모두 수행하기에 시간이 오래 걸림
  + 이를 해결하기 위한 방법 $\rightarrow$ GPU: 행렬 연산이 매우 빠름
  + Tensorflow 설치 시에 GPU 버전 확인 필요
+ GPU가 없는 경우 클라우드 서비스를 통해 사용 가능
+ AWS 사용 방법에 대해 설명
  + hunkim 교수님께서 이미 AWS에 CUDA 설치를 완료한 이미지 만들어 놓음
    + N. Virginia: ami-9e39dcf3
    + oregon: ami-38f60658
  + GPU 사용시의 속도 향상 보임
  + 저렴하게 사용하는 방법 (Spot Instance) 설명 $\rightarrow$ bidding
  + 사용하지 않는 경우 꼭 server stop

{% include date/updated.html %}
{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}
{% include layout/row_end.html %}
