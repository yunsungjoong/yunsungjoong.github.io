---
layout: post
title: "[ionic] Capacitor "
tags: [ionic, capacitor]
categories: [Android]
banner:
  image: "/assets/images/banners/2024/07/banner_ionic-capacitor.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
--- 

## Capacitor란 ?

`Ionic Capacitor`는 `Ionic` 팀에 의해 개발된 크로스 플랫폼 하이브리드 애플리케이션 개발 프레임워크입니다. <br>
이는 최신 웹 기술을 사용하여 모바일, 데스크탑 및 웹에서 실행할 수 있는 애플리케이션을 만들 수 있도록 설계되었습니다. <br>
다음은 `Ionic Capacitor`에 대한 주요 정보입니다.

### 주요 특징

1. 네이티브 API 접근:
- Capacitor는 네이티브 API에 직접 접근할 수 있어 더 나은 성능과 유연성을 제공합니다. 
- Cordova와 달리, 많은 네이티브 기능을 플러그인 없이 직접 사용할 수 있습니다​.

2. Progressive Web App (PWA) 지원:
- `Capacitor`는 `PWA`를 기본적으로 지원합니다. 이를 통해 웹 애플리케이션을 모바일 애플리케이션처럼 사용할 수 있으며, 웹 브라우저에서 직접 설치 및 실행할 수 있습니다.

3. 현대적인 웹 기술 사용:
- `HTML`, `CSS`, `JavaScript`와 같은 최신 웹 기술을 사용하여 개발할 수 있습니다. 
- 이는 웹 개발자가 모바일 애플리케이션 개발로 쉽게 전환할 수 있게 합니다​.

4. 백워드 호환성:
- `Capacitor`는 대부분의 `Cordova` 플러그인과 호환됩니다. 이는 기존의 `Cordova` 프로젝트를 `Capacitor`로 쉽게 전환할 수 있게 합니다​.

5. 클라우드 빌드 및 배포:
- `Ionic` 팀은 `Capacitor`와 통합된 클라우드 빌드 및 배포 서비스를 제공합니다. 이를 통해 개발자는 다양한 플랫폼에서 앱을 쉽게 빌드하고 배포할 수 있습니다​.

### 장점
- 성능: 네이티브 API에 직접 접근할 수 있어 Cordova보다 성능이 우수합니다.
- 유연성: 플러그인 없이 네이티브 기능을 활용할 수 있어 개발이 더 유연합니다.
- 현대적인 개발 경험: 최신 웹 기술을 사용하여 현대적인 개발 경험을 제공합니다.
- 강력한 지원: Ionic 팀과 커뮤니티의 강력한 지원을 받을 수 있습니다.

### 단점
- 상대적으로 새로운 프레임워크: Cordova에 비해 커뮤니티와 플러그인 생태계가 아직 성장 중입니다​ (No-code Mobile Builder)​​ (MobiLoud)​.


### 개발 환경
- `Capacitor`는 CLI 도구를 통해 프로젝트를 생성하고 관리할 수 있습니다. `npx cap init` 명령을 사용하여 프로젝트를 초기화하고, `npx cap add` 명령을 사용하여 플랫폼을 추가할 수 있습니다.
- `Capacitor`는 `Angular, React, Vue`와 같은 프레임워크와 쉽게 통합할 수 있으며, 기존의 웹 프로젝트를 모바일 애플리케이션으로 확장할 수 있습니다

### Ionic 과 Cordova 차이 
- 모바일 `WebView`로부터 디바이스의 `Native` 기능에 접근한다는 점에서 같은 기능을 한다.
- 코도바는 전체를 빌드 하기 떄문에 시간이 많이 걸리고 작은 테스트하기에 번거롭다. 캐패시터는 코도바 `imports` 없이 앱을 만드는데, 대신에 캐패시터 자체의 `네이티브 플러그인`을 `import` 한다. 
- 코도바와 달리 캐패시터는 앱 빌드를 안드로이드 스튜디오 또는 `Xcode`에서 직접한 후, 디바이스 또는 Emulator 에서 테스트가 가능하다. 만족한다면 바로 빌드 및 퍼블리시가 가능하고, 코드를 조금 바꾸어야 한다면 소스 코드를 변경하고 터미널에 `npm run build, npx cap copy` (굉장히 빠름) 한 후 `Xcode` 또는 안드로이드 스튜디오를 열어서 바로바로 테스트 해볼 수 있다. 

### 결론
`Ionic Capacitor`는 최신 웹 기술을 사용하여 크로스 플랫폼 애플리케이션을 개발하려는 개발자에게 매우 유용한 도구입니다. 
특히 성능과 유연성을 중시하는 프로젝트에 적합하며, `PWA` 지원과 같은 현대적인 기능을 제공합니다. `Cordova`에서 `Capacitor`로의 전환을 고려하고 있다면, 대부분의 플러그인이 호환되므로 큰 어려움 없이 전환할 수 있습니다.


## Capacitor 시작하기

```zsh
# ionic CLI 설치 
npm install -g @ionic/cli@7.1.1

# 노드버전 v16 으로 변경 
nvm use 16 

# 노드 v16 설치
npm install --legacy-peer-deps     

# Angular v15 패키지 설치
npm i @angular/cli@15.0.0

```


### Capacitor 설치 및 초기화 
```zsh

# Capacitor 설치 및 초기화
npm install @capacitor/cli@4.7.1 @capacitor/core@4.7.1

# 초기화 과정에 애플리케이션 이름과 ID를 묻습니다. 적절한 이름과 ID를 입력합니다
npx cap init  
```

### 2.Capacitor 플랫폼 추가

#### Android iOS 플랫폼을 추가합니다.
```zsh
# capacitor 플랫폼 추가 (Android , iOS)
npm install @capacitor/android@4.7.1 
npm install @capacitor/ios@4.7.1 

# 안드로이드 플랫폼 추가 
npx cap add android

# # iOS 플랫폼 추가
npx cap add ios
```

#### 작업 후 안드로이드 빌드 전 

```zsh
# Android 빌드 하기전에 아래 명령어를 통해 리소스 및 변경된 플러그인을 싱크(업데이트) 합니다.
npx cap sync android
```


### 안드로이드 & iOS 이름 및 버전 변경방법

Capacitor는 각각 안드로이드면 안드로이드 스튜디오 
iOS 이면 스위프트에서 Name, Version 등 세부적인거는 각 플랫폼에서 진행해야 한다.

![image](https://github.com/user-attachments/assets/74fbe27f-6744-4ce5-b9a3-d4463bdf3382)

```zsh
# 앱의 이름을 변경하려면 다음 값을 변경 app_name하세요 strings.xml.

<string name="app_name">MyApp</string>

# 특히 앱에 단일 활동이 있는 경우 활동 이름을 일치하도록 변경하는 것이 좋습니다.

<string name="title_activity_main">MyApp</string>
```


#### 버전 변경방법

![android_capacitor01](https://github.com/user-attachments/assets/5b7fa292-9d91-45ac-9e9e-051ca1471e21)

```zsh
# build.gradle 파일 수정
# android/app/build.gradle 파일을 열고 versionCode와 versionName 속성을 설정합니다

```

### `@capacitor/splash-screen`설치

먼저, `@capacitor/splash-screen` 플러그인을 설치합니다.

```zsh

# 스프래시 스크린 설치 & 버전에 따라 재설정할 필요 있음
npm install @capacitor/splash-screen 

# 필자는 버전에 맞춰 설치
npm install @capacitor/core@4 @capacitor/cli@4 @capacitor/android@4 @capacitor/device@4 @capacitor/splash-screen@4 --legacy-peer-deps

# 안드로이드 동기화
npx cap sync android
```


#### 스플래시 화면 및 아이콘 

`@capacitor/assets` 도구를 사용하여 `iOS`, `Android` 또는 프로그레시브 웹 애플리케이션용 
스플래시 화면과 아이콘을 생성할 수 있습니다 .

1. 먼저, 다음을 설치하세요  `@capacitor/assets`

```zsh 
npm install @capacitor/assets --save-dev
```

2. 프로젝트 루트 디렉터리에 `resources` 폴더를 만듭니다.

3. `resources` 폴더 안에 `icon`, `splash.png` 파일을 추가합니다.
```plaintext
resources/
├── icon-only.png
├── icon-foreground.png
├── icon-background.png
├── splash.png
└── splash-dark.png
```

- 아이콘 파일은 최소한 1024pxx 이상이어야 합니다 1024px.
- 시작 화면 파일은 최소한 2732pxx 이상이어야 합니다 2732px.
- 형식은 jpg또는 일 수 있습니다 png.

```zsh
npx capacitor-assets generate --android

# 안드로이드 동기화
npx cap sync android

```
안드로이드 동기화 후 안드로이드 스튜디오에서 실행 

4. 스플래시 참고사항
- 안드로이드 12 이상
Android12 이상에서 Google은 스플래시 화면이 표시되는 방식을 변경하여 Android 11 이하에서 가능했던 전체 화면 이미지 대신 색상이 있는 작은 아이콘을 사용했습니다. 이 변경 사항에 대한 추가 문서는 [developer.android.com] (https://developer.android.com/develop/ui/views/launch/splash-screen#splash-screen-resources) 에서 찾을 수 있습니다 .

