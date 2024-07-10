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


## 디버그 키스토어란(Android Debug keystore)?

안드로이드 애플리케이션을 개발하고 디버깅 할 때 사용하는 디지털 서명 파일입니다. 이를 통해 개발 중인 애플리케이션을 테스트하기 위해 디버깅 모드에서 실행할 수 있습니다.

### 1. 목적
안드로이드 애플리케이션은 서명되지 않은 상태로는 실행할 수 없습니다. `디버그 키스토어`는 개발자가 애플리케이션을 서명하고, <br>
애뮬레이터나 실제 기기에서 테스트할 수 있도록 합니다.

안드로이드 API를 이용하려면 다음과 같이 `debug` , `release` 용 등 자신이 사용할 용도에 따라 keystore를 만들어주어야 합니다.
만드는 작업은 구글 사이트에 자세히 설명되어 있습니다.


### 2. 디폴트 위치

1) 각 운영체제별로 디버그 키스토어의 기본 위치는 다음과 같습니다.

```zsh
#터미널 실행한다. 

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