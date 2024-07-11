---
layout: post
title: "[Android Studio] 패키지명 변경(AndroidStudio PackageName "
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
안드로이드 스튜디오 (Android Studio) 패키지 변경해야 할 때가 있습니다.

정리해 둘겸 패키지 변경방법에 대해 정리해두려고 합니다.

---

## 패키지명 변경하기 (Package Change)

### 1. 설정 변경


![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/66172e00-c110-406c-82a3-b1ced0f6e759)

`Project` 우측상단 톱니바퀴 아이콘을 클릭해 `Compact Middle Packages`을 해제합니다. (초기에는 대부분 체크되어 있을 것입니다.)



![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/80fc5570-c15d-4476-9282-bdf1a7071a6f)

`com.ionicframework.cordova.webview` 가 `com`, `ionicframework`, `cordova`, `webview` 로 분리된 걸 확인할 수 있습니다.



![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/ae117275-8b99-4dd1-a93e-b11cd525e0d1)

저는 ionicframework 패키지명을 변경하기 위해 `ionicframework` 패키지 -> `Refactor` -> `Rename`을 클릭합니다.

