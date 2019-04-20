---
title: Session 3. Rethinking Access Control and Authentication for the Home Internet of Things (IoT)
date: 2019-04-18 00:00:00 Z
description: Rethinking Access Control and Authentication for the Home Internet of Things (IoT)
card_title: Session 3
card_teaser: Rethinking Access Control and Authentication for the Home Internet of Things (IoT)
card_position: 3
icon: fa-server
categories: [seminars,04-22-2019-morning-seminar,presentation]
tags: [USENIX, 2018, USENIX2018, Human, Policy, IoT, LargeSacle, IRB, Analytics, Human-Authenticate]
sidebar: morning-seminar
layout: default
slug: ms-presentation-jh-apr-22-2019
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

## Presenter & Date
+ Jong-Hyuk Im (임종혁)
+ 2019-04-22

## [Rethinking Access Control and Authentication for the Home Internet of Things (IoT)](https://inhaucs.github.io/seminars/04-22-2019-morning-seminar/presentation/ms-presentation-jh-apr-22-2019.html)

#### Information of the paper [(Link)](https://www.usenix.org/conference/usenixsecurity18/presentation/he)
+ Authors: Weijia He (University of Chicago); Maximilian Golla (Ruhr-University Bochum); Roshni Padhi and Jordan Ofek (University of Chicago); Markus Dürmuth (Ruhr-University Bochum); Earlence Fernandes (University of Washington); Blase Ur (University of Chicago)
+ Conference name: 27th USENIX Security Symposium (USENIX Security 18)
+ Published date: 2018-08-15
+ [Paper file](https://www.usenix.org/system/files/conference/usenixsecurity18/sec18-he.pdf)


## Abstract
Computing is transitioning from single-user devices to the Internet of Things (IoT), in which multiple users with complex social relationships interact with a single device. 
Currently deployed techniques fail to provide usable access-control specification or authentication in such settings. 
In this paper, we begin reenvisioning access control and authentication for the home IoT. 
We propose that access control focus on IoT capabilities (i.e., certain actions that devices can perform), rather than on a per-device granularity. 
In a 425-participant online user study, we find stark differences in participants' desired access-control policies for different capabilities within a single device, as well as based on who is trying to use that capability. 
From these desired policies, we identify likely candidates for default policies. We also pinpoint necessary primitives for specifying more complex, yet desired, access-control policies. 
These primitives range from the time of day to the current location of users. 
Finally, we discuss the degree to which different authentication methods potentially support desired policies.

## Summary (Korean)

가정용 IoT 기기들에 대한 Access-control 정책에 대한 새로운 방향을 제시한 논문이다. 이 논문에서는 기존의 가정용 IoT 기기들의 권한 체계는 기기 중심적이며, 역할이 Onwer/Guest 로만 나뉘는 등의 제한적이므로 변화하는 IoT 시대의 패러다임에 맞추기 위해서 이를 적합하게 변경하는 것은 필요하다고 주장한다.

따라서, 이 논문의 목표는 IoT 기기들에 대한 적절한 엑세서 제어 정책을 매핑하는 것이며, 이를 위해 가정용 IoT 기기들과 사용자의 관계를 6가지로 정의하고, 기기 중심적인 권한 체계에서 기능 중심적(IoT 기기 자체의 권한이 아니라, 기기가 수행할 수 있는 특정 동작을 말함)인 체계로 변경시키고, 나아가 새로운 기기들에 대한 잠재적인 권한 부여를 위한 기본 정책을 설립하는 것이다.

이 논문은 425명의 온라인 참가자에 대해 실험을 수행하였으며, 같은 장치 내에서 다양한 기능에 대한 참가자들이 각각 원하는 엑세스 제어 정책은 물론 누가 해당 기능을 사용하려하는지에 따라 명확한 차이가 있음을 확인하였다. 즉, 이러한 실험을 통해 설립된 정책(앞으로 지속적으로 갱신 가능함)을 논문에 제시하였으며, 정책을 지정하는데 필요한 기본 요소(시간이나 사용자의 현재 위치까지도 포함)를 정의하고, 서로 다른 인증 방식이 잠재적인 정책 지원에 어떠한 영향을 미칠 수 있는지에 대한 논의 또한 진행하였다.



## Details

### Contents of the paper
#### Research goals

+ Map desired access-control policies for home IoT devices
  (IoT 기기들에 대한 적절한(?) 엑세스 제어 정책 매핑)
  
  + How <u>policies</u> vary by **relationships** and **capabilities**
  + <u>Identify</u> **potential default polices**
+ What contextual factors affect the user's decision?

#### User study

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-22-fig-usetstudy.PNG" legend="User Study" %}

+ 6 Relationships (각각의 실험자들이 구분한 24개의 관계 중 큰 틀로 분류한 것들)

  + Your Spouse
  + Your Teenage Child
  + Your Child in Elementrary School
  + A Visiting Family Member
  + The Babysitter
  + Your Neighbor
+ 22 Capabilities

  + Order Onlie
  + Live Video
  + Answer Door
  + Mower Rule
  + Lights Rule ...

#### Results

##### 425 Participants

+ Male / Female ( 54 : 46 )
+ Age 25-34 : 47%
+ Computer Science: 19%
+ Home IoT Device (Ai Speaker, CCTV, Nest, Lights): 44%

##### Capability and access-controll policy for one

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-22-fig-result1.PNG" legend="User Study" %}

##### Comparison between capabilities

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-22-fig-result2.PNG" legend="User Study" %}

##### Capabilities within one device

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-22-fig-result3.PNG" legend="User Study" %}

##### Relationships and capabilities

{% include articles/figure.html url="/assets/img/jonghyuk/2019/2019-04-22-fig-result4.PNG" legend="User Study" %}

#### Contextual factors

+ Time of Day
  + "밤에 잔디깎는건 안됩니다..."
+ People around
  + "어린이가 무엇을 작업할 때에는, 보호자와 함께"
+ Location of user
  + "집에 없을 때, 음악을 재생할 필요가 있는가"
+ Location of device
  + "침실에서 CCTV 사용 여부?"
+ Responsible usage
  + "너무 조명을 자주 사용해서는 안됩니다."
+ Understanding
  + "자신의 아이에게 사용법을 가르칠 필요가 있다."
+ Etc...

#### Conclusion

가정용 IoT 환경에서 앞으로 고려할 것은, 기기에 대한 권한이나 Owner/Guest 정도의 구분이 아닌

+ Relationships
+ Capabilites
+ Contextual factors

가 될 것이다. 이에 대해 다시 생각하고, IoT 시대의 새로운 응용을 적용해야 할 것이다.

### Points to note
+ 어떤 대상(e.g. Home IoT devices)에 대한 권한 정책 수립에 있어 대규모 실험을 통해 실제 수요를 확인할 수 있다. 이 또한 논문으로 정리할 수 있다.
+ 이러한 분석/설계 논문을 구성할 때에는 실험을 통해 무엇을 확보할 것인지 구체적으로 고려하는 것이 꼭 선행되어야 할 것이다.
+ 본 논문에서는 Appedix에 Survey 항목을 모두 기재하였다. 저널/컨퍼런스에서 이와 같은 것을 요구할 수 있기 때문에 설문 항목은 잘 작성해야하며 한국어/영어 버전 모두 미리 작성해 두는 것을 잊지 않아야 할 것이다.


## Discussion
Editor: 작성자 이름
(내용 작성)


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
