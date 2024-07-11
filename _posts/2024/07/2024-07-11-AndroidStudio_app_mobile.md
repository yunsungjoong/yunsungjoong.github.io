---
layout: post
title: "[Android Studio] 패키지 이름과 package 구조"
tags: [Android Studio]
categories: [Android Studio]
banner:
  image: "/assets/images/banners/2024/07/banner_android-studio-logo-hero.jpg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
--- 

안녕하세요.
안드로이드 스튜디오 (Android Studio)에서 프로젝트를 만들 때 프로젝트 이름과 패키지 이름을 정하는걸로 시작합니다.
그런데 이런 패키지 이름을 정하는 것도 규칙이 이씃ㅂ니다.
패키지 이름 규칙에 대해서 알아보도록 하겠습니다.


## 패키지 작명방식
- 일반적으로 패키지 이름을 지을 때는 회사가 개발한 도메인이름을 거꾸로 나열한다.
- 그 뒤에 프로젝트 명을 붙인다.
- 필요하면 그 뒤에 기능별로 세분화하는 방식으로 붙인다.

예시,

- 도메인 : toktok.com
- 프로젝트 이름 : tutorial
- 도메인 이름을 거꾸로 배열 : com.toktok
- 프로젝트 이름 붙임 : com.toktok.tutorial
- 기능별로 세분화
```
com.toktok.tutorial.base
com.toktok.tutorial.toktok
com.toktok.tutorial.android
com.toktok.tutorial.talk
```

---

## 패키지명 변경하기 (Package Change)

### 1. 설정 변경


![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/e493ca60-e620-4cfb-b185-e80ef543cdaf)

`Project` 우측상단 톱니바퀴 아이콘을 클릭해 `Compact Middle Packages`을 해제합니다. (초기에는 대부분 체크되어 있을 것입니다.)



![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/0b1ba653-fa34-4fe5-8463-abb5bb0e8404)

`com.sk.pe.training` 가 `com`, `sk`, `pe`, `training` 으로 분리된 걸 확인할 수 있습니다.



![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/fcb303d3-13ed-498b-b13c-00f83322d27b)

저는 sk패키지 안에 `training` 을 변경하고 싶다면 `pe` 우클릭 -> `Refactor` -> `Rename`을 클릭합니다.


![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/2249010c-312f-4dd9-ab4a-1d7048740b57)

경고창이 뜬다면 `In Whole Project`를 클릭합니다.


![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/696bc74f-fd61-4cf9-ae10-81288ecf066a)

변경할 패키지명을 입력 후 `Refactor` 클릭합니다.

![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/ddc0bff2-d3d3-4ed1-9d7c-34b364f7b2e2)

클릭하면 위 화면이 나오는데 `Do Refactor`를 클릭합니다.

