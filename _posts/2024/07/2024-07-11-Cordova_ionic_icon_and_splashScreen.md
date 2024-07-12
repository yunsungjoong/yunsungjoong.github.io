---
layout: post
title: "[Cordova] ionic&cordova 아이콘, 스플래시 스크린"
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
`Splash Screen` 은 맨 처음에 어플을 시작할때 잠깐 나왔다가 들어가는 이미지 및 애니메이션 입니다.
알아보고 적용해보겠습니다.


![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/8314813c-e643-4362-b74e-c3053da0041a)

카카오에 들어갈때 화면입니다. 위 이미지 처럼 로딩이 끝나면 fade-out 되면서 채팅 목록이 나오죠
이런 기능이 바로 `splash screen` 입니다. 시간은 우리가 직접 정해주도록 합시다.


공식홈페이지 먼저 보고 다음 구현하는법을 알아보도록 하겠습니다.

icon 
http://cordova.apache.org/docs/en/7.x/config_ref/images.html#page-toc-source


splash screen  (with git)
http://cordova.apache.org/docs/en/7.x/reference/cordova-plugin-splashscreen/index.html#page-toc-source
https://github.com/apache/cordova-plugin-splashscreen

  

## icon 

icon 같은 경우에는 다른 것 필요없이 이미지와 코드 몇개 입력하면 바로 적용이 가능합니다.


<img width="698" alt="image" src="https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/87a30fd4-fbb3-4033-a7b2-22344557e67d">

위에 해당되는 코드를 넣을 겁니다. 코드는 공식홈페이지에 있는 그대로 따라오시면 됩니다.

```android
‹ platform name="android">
<! --
Lapi : 36x36 px| mapi : 48x48 px| hdpi : 72x72 px xhdpi : 96x96 px|
xxhdpi : 144x144 px| xxxhdpi : 192x192 px|
‹icon src="res/android/ldpi.png" density="1dpi" />
‹icon src="res/android/mdpi.png" density="mdpi" />
‹icon src="res/android/hdpi.png" density="hdpi" />
«icon src="res/android/xhdpi.png" density="xhdpi" /›
«icon src="res/android/xxhdpi.png" density="xxhdpi" /›
‹icon src="res/android/xxxhdpi.png" density="xxxhdpi" /›
</platform>
```

`<platform>` 안에 `icon`태그를 넣고 해당 경로설정을 제대로 해주시면 됩니다.
예제는 위처럼 나와있지만 `icon` 이라는 경로가 하나 더 들어가게 될 겁니다. 경로는 직접 눈으로 확인해주시면서 작업하시면 될 겁니다.
이렇게 하면 `icon` 은 끝입니다. 

## splash screen

```zsh 
ionic cordova plugin add cordova-plugin-splashscreen
npm install @ionic-native/splash-screen
```


하고 실행하면 된다. 
`조건은 ` `$ ionic cordova prepare android`  인 경우 문제없이 동작 

