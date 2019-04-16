---
title: How to write markdown
date: 2019-04-16 00:00:00 Z
description:  How to write markdown.
card_title:   How to write markdown
card_teaser: This post contains instructions on how to add pictures, tags, and files.
card_position: 2
icon: fa-address-book-o
categories: [seminars,guides-for-seminars,common-information]
sidebar: guides-for-seminars
layout: default
slug: guides-for-seminars-how-to-write-markdown
permalink: /:categories/:slug.html
---

{% assign product = 'ce' %}

{% include layout/row_start.html %}
{% include layout/col_start.html column="7" %}

----

## 포스팅에 그림(figure) 추가하는 방법

### step 1. ```assets/img/``` 디렉터리 아래에 그림 파일을 업로드합니다.
> 필요에 따라서, 하위 디렉터리 만들어도 괜찮습니다. 

### step 2. 만약 파일 ```001_create_droplet.png```을 ```/assets/img/help/2019/03/digital-ocean``` 에 업로드 했다면, 다음과 같이 코드를 포스팅에서 원하는 위치에 추가합니다. 
```
{% include articles/figure.html url="/assets/img/help/2019/03/digital-ocean/001_create_droplet.png" legend="Create droplet" %}
```
> ```legend``` 속성으로 캡션을 지정합니다.

----

## 포스팅에 파일(file) 추가하는 방법 : URL 생성하여 첨부하기

### step 1. ```assets/files/``` 디렉터리 아래에 파일을 업로드합니다.
> 필요에 따라서, 하위 디렉터리 만들어도 괜찮습니다. 

### step 2. 만약 파일 ```keepass_file_example.kdbx```를 ```assets/files```에 업로드 했다면, Github 에 업로드된 파일의 URL은 다음과 같이 생성됩니다. ; ```https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/keepass_file_example.kdbx```
> 파일 다운로드 시, Github 페이지가 열리는 것이 아니라, 바로 다운로드 되도록 하려면 ```?raw=true``` 를 붙여 사용합니다. 

예를 들면, 아래 마크다운 코드를 포스팅에서 원하는 위치에 추가합니다.
```[keepass_file_example.kdbx](https://github.com/inhaucs/inhaucs.github.io/blob/master/assets/files/keepass_file_example.kdbx?raw=true)```

----

## 포스팅에 태그(tags) 추가하는 방법

### step 1. 포스팅 작성시 상단에 tags 속성을 추가합니다.

예를 들면, 아래와 같습니다.
```
----
title: UCSLab Paper Review Test posting
date: 2019-04-12 00:00:00 Z
description: test about how to post into this site. 
...
tags: [tag1, tag2, tag3,...]
...
----
```

### step 2. [약자와 태그에 관한 규칙](https://inhaucs.github.io/seminars/guides-for-seminars/common-information/guides-for-seminars-information-for-editors.html)에 맞춰서 tags 속성에 포스팅의 태그들을 나열합니다.

예를 들면, 아래와 같습니다.
```
----
title: UCSLab Paper Review Test posting
date: 2019-04-12 00:00:00 Z
description: test about how to post into this site. 
...
tags: [CCS, 2018, CCS2018, HE, FHE, Biometric, Biometric Authentication]
...
----
```
----


{% include date/updated.html %}

{% include layout/col_end.html %}
{% include layout/col_start.html column="4 last push1" %}

{% include layout/row_end.html %}
