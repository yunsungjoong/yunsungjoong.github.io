---
layout: post
title: "[Android Studio] 안드로이드 스튜디오 앱이름 간단하게 바꾸는 방법 "
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
안드로이드 스튜디오 (Android Studio) 앱 이름 변경하는 방법에 대해 알아보겠습니다. 

---

## 앱 이름 바꾸는 법

AndroidManifest.xml 진입 -> application -> android:label="@string/app_name" 에서 <U>@string/app_name"를 컨트롤 키를 누른 상태에서 마우스를 클릭</U>합니다.
![Android_ReName_000](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/92cf09b1-cc12-430f-8340-ef392c9de4be)


또는 res -> value -> string.xml 로 진입해 안드로이드 스튜디오 앱 이름을 바꿀 수 있습니다.

### 변경 전
![Android_ReName_001](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/3e5943a1-3c85-4473-885c-8f617a7cd1ff)

### 변경 후
![Android_ReName_002](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/195f75b6-92a2-4d22-8f5c-00d23556c09c)


위 방법으로 프로젝트 이름은 바뀌지 않았지만 앱의 이름은 변경이 되었음을 앱실행을 통해 확인할 수 있습니다.

