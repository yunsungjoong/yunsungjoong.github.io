---
layout: post
title: "[Android] KeyStore란? 생성 방법 및 역할 "
tags: [Cordova]
categories: [Android]
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
안드로이드 디버그 키스토어(Android Debug keystore)는 무엇이고 `debug.keysotre`를 이용해 
앱 설치 파일을 만드는 방법에 대해 알아보겠습니다.

# 키 스토어(key store)
흔히 안드로이드 개발자는 3가지 키스토어라는 용어를 듣습니다.
1. 디버깅용 키스토어 
보편적으로 정식 상용버전이 아닌, 개발용도의 목적으로 서명할 때 필요한 키스토어입니다. 일반적으로 내가 사용하고 있는 JDK가 가지고 있는 키스토어를 사용해 서명하게 됩니다. <br>
이 경우는 각자의 개발환경마다 고유한 파일이기 때문에 또 자바(JDK)에서 제공하는 범용 키스토어이기 떄문에 따로 개개인이 암호를 설정해줄 필요는 없습니다.
<br>
2. 릴리즈용 키스토어
실제 서비스를 위한 키스토어입니다. 이 모드는 나 이외에 사용자가 인증 또는 서명할 수 없는 상태이며, <br> 
PC환경에 상관없이 1개의 키스토어로써 서명을 진행하게 됩니다.
추가적으로 키스토어의 주인이 암호 또는 일련의 과정을 더합니다. 
절대 분실해서는 안됩니다.
<br>
3. 구글 사이닝 키스토어
구글 사이닝 키스토어는 기존에 안드로이드 서명 및 배포 방식에서 없던 방법으로 하지만 요 몇년전 키스토어 관리 또는 인증에 있어
이슈들이 다발적으로 발생했고 구글에서 한 가지 방법을 개발자들에게 제시하게 되는데,
예를 들면 : "최종 앱 안전 서명은 구글이, 대신 원래 릴리즈(실 서비스)용으로 서명하던 키스토어는 딱 Play Console에 업로드할 때만 쓰는 Upload 키스토어로 스길 바란다" 는 내용입니다.
개발자 및 서비스 제공자는 구글 사이닝 키스토어를 사용할지 아닐지 선택할 수 있습니다. 구글 측에서는 적극적으로 구글 사이닝을 권하는 추세이며 대부분 진행하는 곳이 많습니다.
<br>
각각 APK를 서명하는데 들어가는 키스토어의 종류가 다릅니다. 다 같으면 나는 개발용으로 테스트 했는데 이게 적용되지 않아야 할 릴리즈 모드에 적용되거나 오작동을 일으킬 수 있기 때문입니다.

---

## 디버그 키스토어란(Android Debug keystore)?

1. 안드로이드 애플리케이션을 개발하고 디버깅 할 때 사용하는 디지털 서명 파일입니다. 
- 1) 흔히 안드로이드 앱을 개발하고 내가 만든거야! 라고 서명하는데 필요한 암호화 파일입니다.
- 2) 키스토어란 말 그대로 열쇠로 설치파일(APK)를 인증하기 위해서는 꼭 맞는 반드시 동일한 파일이여야 합니다.
이를 통해 개발 중인 애플리케이션을 테스트하기 위해 디버깅 모드에서 실행할 수 있습니다.


### 1. 목적
안드로이드 애플리케이션은 서명되지 않은 상태로는 실행할 수 없습니다. `디버그 키스토어`는 개발자가 애플리케이션을 서명하고, <br>
애뮬레이터나 실제 기기에서 테스트할 수 있도록 합니다.

안드로이드 API를 이용하려면 다음과 같이 `debug` , `release` 용 등 자신이 사용할 용도에 따라 keystore를 만들어주어야 합니다.
만드는 작업은 구글 사이트에 자세히 설명되어 있습니다.



### 3. 디폴트 위치

1) 각 운영체제별로 디버그 키스토어의 기본 위치는 다음과 같습니다.

```zsh
#터미널 실행한다.(택 1)

# 1. 이동방법 1 
/Users/(사용자명).android 위치를 이동하면 debug.keystore 파일을 찾을 수 있다.

# 2. 이동방법 2

cd Users
cd {user name}
cd .android
```

2) ls 명령을 입력해 debug.keystore 파일이 존재하는지 확인한다.

<img width="582" alt="cd_debugstore" src="https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/908c9f4f-ff5a-49d8-90c2-d3b44962c251">

<br>

3) 구글에서 제시해주는 명령은 다음과 같습니다.

```zsh
keytool -exportcert -keystore path-to-debug-or-production-keystore -list -v
```
위 명령어중 `keystore`의 `path`를 입력하는 부분 `debug`용 혹은 `release`용 `keystore` 파일의 위치를 적어주면 됩니다.



### 제한사항 
- 디버그 키스토어는 오직 개발 및테스트 용도로만 사용해야 합니다. 실제 배포용 앱은 별도의 릴리스 키스토어를 사용해야 합니다. 배포 시 디버그 키스토어로 서명된 앱은 신뢰할 수 없는 소스로 간주되어 설치되지 않을 수 있습니다.



## Android Studio에서 APK 파일 생성을 위한 Key Store 생성 및 앱에 서명해서 APK 추출

Android Studio에서 APK 파일을 생성을 위한 Key Store 생성 및 앱에 서명해서 APK 추출하기 


1. 
![Android_debug_apk00](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/258f32bb-5c1b-45c2-95a9-506c4c2ec9a4)


![Android_debug_apk01](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/88cdb7a7-6a79-465c-be9f-a1c6ffbfb73f)


