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

## Android 앱 이름 바꾸는 법

AndroidManifest.xml 진입 -> application -> android:label="@string/app_name" 에서 <U>@string/app_name"를 컨트롤 키를 누른 상태에서 마우스를 클릭</U>합니다.
![Android_ReName_000](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/92cf09b1-cc12-430f-8340-ef392c9de4be)


또는 res -> value -> string.xml 로 진입해 안드로이드 스튜디오 앱 이름을 바꿀 수 있습니다.

### 변경 전
![Android_ReName_001](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/3e5943a1-3c85-4473-885c-8f617a7cd1ff)

### 변경 후
![Android_ReName_002](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/195f75b6-92a2-4d22-8f5c-00d23556c09c)


위 방법으로 프로젝트 이름은 바뀌지 않았지만 앱의 이름은 변경이 되었음을 앱실행을 통해 확인할 수 있습니다.

--- 

## Ionic Cordova 앱 이름 변경하는 방법

Cordova의 경우, 프로젝트 폴더에서  `config.xml `  의 셋팅에 기반합니다.
설정 파일로, 앱의 이름, 버전, 아이콘, 스플래시 스크린, 권한 및 기타 여러 가지 설정을 관리할 수 있습니다.

```zsh
# ionic 프레임워크 활용 ordova 프로젝트 준비
ionic cordova prepare android
```


![image](https://github.com/user-attachments/assets/6421c11f-10ca-4e34-bcf2-96a8b6b3681f)

### 1.앱 이름 변경
```zsh
# 앱의 이름과 설명은 <name> 및 <description> 태그를 사용하여 설정할 수 있습니다.
<name>MyApp</name>
<description>An example Ionic application</description>
```

### 2. 앱 버전 관리
```zsh
# 앱의 버전은 <widget> 태그의 version 속성을 통해 설정할 수 있습니다.
<widget id="com.example.app" version="1.0.0" xmlns="http://www.w3.org/ns/widgets" xmlns:cdv="http://cordova.apache.org/ns/1.0">
```

### 3. 아이콘과 스플래시 스크린 

```zsh
  <platform name="android">
        <icon density="ldpi" src="resources/android/icon/drawable-ldpi-icon.png" />
        <icon density="mdpi" src="resources/android/icon/drawable-mdpi-icon.png" />
        <icon density="hdpi" src="resources/android/icon/drawable-hdpi-icon.png" />
        <icon density="xhdpi" src="resources/android/icon/drawable-xhdpi-icon.png" />
        <icon density="xxhdpi" src="resources/android/icon/drawable-xxhdpi-icon.png" />
        <icon density="xxxhdpi" src="resources/android/icon/drawable-xxxhdpi-icon.png" />
        <splash density="land-ldpi" src="resources/android/splash/drawable-land-ldpi-screen.png" />
        <splash density="land-mdpi" src="resources/android/splash/drawable-land-mdpi-screen.png" />
        <splash density="land-hdpi" src="resources/android/splash/drawable-land-hdpi-screen.png" />
        <splash density="land-xhdpi" src="resources/android/splash/drawable-land-xhdpi-screen.png" />
        <splash density="land-xxhdpi" src="resources/android/splash/drawable-land-xxhdpi-screen.png" />
        <splash density="land-xxxhdpi" src="resources/android/splash/drawable-land-xxxhdpi-screen.png" />
        <splash density="port-ldpi" src="resources/android/splash/drawable-port-ldpi-screen.png" />
        <splash density="port-mdpi" src="resources/android/splash/drawable-port-mdpi-screen.png" />
        <splash density="port-hdpi" src="resources/android/splash/drawable-port-hdpi-screen.png" />
        <splash density="port-xhdpi" src="resources/android/splash/drawable-port-xhdpi-screen.png" />
        <splash density="port-xxhdpi" src="resources/android/splash/drawable-port-xxhdpi-screen.png" />
        <splash density="port-xxxhdpi" src="resources/android/splash/drawable-port-xxxhdpi-screen.png" />
  </platform>
```

### 4. 권한 설정 

```zsh
# 앱이 필요한 권한은 <plugin> 태그를 사용하여 추가할 수 있습니다. 예를 들어, 카메라 접근 권한을 추가하려면
  <plugin name="cordova-plugin-camera" spec="^5.0.1" />
```

### 5. 기본 환경 설정
```zsh
# 앱의 기본 설정은 <preference> 태그를 통해 설정할 수 있습니다. 예를 들어, 앱의 화면 방향을 잠그려면
  <preference name="Orientation" value="portrait" />
```

### 6. 플랫폼별 설정

```zsh
# 플랫폼별로 다른 설정이 필요한 경우 <platform> 태그를 사용하여 구분할 수 있습니다.

# 안드로이드
  <platform name="android">
      <preference name="android-minSdkVersion" value="21" />
      <preference name="android-targetSdkVersion" value="30" />
  </platform>

# IOS
  <platform name="ios">
      <preference name="deployment-target" value="11.0" />
  </platform>
```

