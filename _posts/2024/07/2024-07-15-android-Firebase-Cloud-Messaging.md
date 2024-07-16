---
layout: post
title: "[Android] FCM(Firebase Cloud Messaging)란? "
tags: [Android,FCM]
categories: [Android]
banner:
  image: "/assets/images/banners/2024/07/banner_android-fcm.jpg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
--- 

안드로이드 `FCM(Firebase Cloud Messaging)`은 구글에서 제공하는 무료 서비스로, <br>
안드로이드와 iOS 애플리케이션에 푸시 알림을 전송하기 위해 사용됩니다. 아래 내용은 FCM의 주요 기능과 사용 방법에 대해 정리했습니다.


## 주요기능

### 1. 푸시 알림 전송
- 애플리케이션 서버에서 사용자 기기로 푸시 알림을 전송할 수 있습니다.
- 사용자가 앱을 실행하지 않아도 알림을 받을 수 있습니다.

### 2. 메시지 우선순위 설정
- 메시지의 중요도에 따라 우선순위를 설정할 수 있습니다.
- 높은 우선순위 메시지는 즉시 전달되며, 낮은 우선순위 메시지는 네트워크 상황에 따라 대기 상태로 전송됩니다.

### 3. 주제별 메시지
- 특정 주제를 구독한 사용자들에게만 메시지를 전송 할 수 있습니다.
- 예를 들어, 스포츠 뉴스 업데이트를 구독한 사용자에게만 관련 알림을 보낼 수 있습니다.

### 4. 장치 그룹 메시징
- 여러 기기를 하나의 그룹으로 묶어 해당 그룹에 ㅁ메시지를 전송할 수 있습니다.
- 한 사용자가 여러 기기를 사용할 경우 유용합니다.


## 사용 방법

### 1.FCM 설정방법
- Firebase 콘솔에서 프로젝트를 생성하고, 해당 프로젝트에 FCM을 설정합니다.
- 안드로이드 앱에 Firebase SDK를 추가하고, 필요한 권한을 설정합니다.

### 2.서버와의 통신:
- 애플리케이션 서버에서 Firebase Cloud Messaging API를 사용하여 메시지를 전송합니다.
- HTTP 또는 XMPP 프로토콜을 사용하여 메시지를 보낼 수 있습니다.


### 3.클라이언트 코드 작성:

- 클라이언트 앱에서 FCM SDK를 사용하여 메시지를 수신하고 처리하는 코드를 작성합니다.
- 수신된 메시지를 알림으로 표시하거나, 앱 내부에서 특정 작업을 수행할 수 있습니다.


### 4.주제 구독 및 메시지 전송:
- 사용자가 특정 주제를 구독하도록 하여, 해당 주제에 관련된 메시지를 받을 수 있도록 합니다.
- 주제에 메시지를 전송하는 코드를 작성하여, 구독자들에게 알림을 보낼 수 있습니다.
