---
layout: post
title: "[Cordova]코르도바 안드로이드 스튜디오 실행 "
tags: [Cordova]
categories: [Cordova]
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

회사업무로 안드로이드 스튜디오 구버전을 사용해야 하는 상황이라 
안드로이드 스튜디오의 구버전을 다운로드 하는 방법에 대해서 정리해 보았습니다.


## 필요한 재원 
- 안드로이드 스튜디오 v3.6.3
- Node.js v10.24.1 
- Cordova v10.0.0
- ionic v5.4.16



### Cordova
```zsh
# 개발 환경에 맞게 코르도바 설치 명령어 
npm install -g cordova@10.0.0

```

```zsh
# 설치 제대로 되었는지 버전 확인
cordova -v
```

### Node 
```zsh
# nvm 현 버전 확인 
nvm -v 

# nvm 버전 설치
nvm install 10.24.1

# 해당버전으로 Change
nvm use 10.24.1 
```


## Ionic 안드로이드 플랫폼 추가

### Cordova를 이용해 안드로이드 플랫폼을 추가

```zsh
ionic cordova prepare android 
```


## 안드로이드 스튜디오에서 프로젝트 열기
1. 안드로이드 스튜디오를 실행합니다.
2. "Open an existing Android Studio project" 를 선택합니다.
3. platforms/android 디렉토리를 선택합니다. (예: /path/to/ionic_default_v4/ionic_default_v4/platforms/android)

## 앱 빌드 및 실행

### 안드로이드 스튜디오에서 실행
1. 상단 메뉴에서 Build > Make Proejct를 선택하고 프로젝트를 빌드합니다.
2. 빌그다 완료되면 상단 메뉴에서 Run > Run 'app'를 선택합니다. 연결된 안드로이드 디바이스 선택합니다.

### 핸드폰에서 실행
1. USB 연결하면 디버깅이 활성화되고 안드로이드 디바이스를 컴퓨터에 연결합니다.
2. 다음 명령어를 실행하여 디바이스 설치한 후 실행합니다.

```zsh
ionic cordova run android #  또는 스타트 버튼 누르면 됩니다. 

```

### 추가 참고사항
1. 환경 설정
- 안드로이드 디바이스에서 개발자 옵션과 USB 디버깅을 활성화해야 합니다. 
- 빌드 중 문제가 발생할 경우, 콘솔 로그를 확인해 필요한 추가 패키지 설치 또는 설정 변경을 수행합니다. <br> 이 과정에 따라압축 파일에서 안드로이드 소스를 생성하고,안드로이드 스튜디오와 실제 디바이스에서 앱을 실행할 수 있습니다.

