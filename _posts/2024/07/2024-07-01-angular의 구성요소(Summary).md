---
layout: post
title: "[Angular] 구성요소(Summary)"
tags: [Angular]
categories: [Angular]
banner:
  image: "/assets/images/banners/2024/06/17-angular_01.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

https://www.howdy-mj.me/angular/angular-structure
위 링크 참고 해서 내용정리 할것 

## Angular 구조

Angular에는 크게 `Component(컴포넌트)`, `Template(템플릿)`, `Directive(디렉티브)`, `Service(서비스)` 그리고 `Module(모듈)`이 존재한다.
![image](https://github.com/user-attachments/assets/9f3708ae-3614-424a-9d01-93c7a62cfaa3)


Angular 프로젝트를 생성하면 기본으로 만들어지는 모듈과 컴포넌트가 있다. 모듈은 `app-routing`.`module.ts`와 `app.module.ts`가 있으며, 컴포넌트는 `app.component.html`, `app.component.scss`, `app.component.ts`, `app.component.spec.ts`가 있다.

### 컴포넌트 
컴포넌트는 템플릿과 메타데이터, 컴포넌트 클래스로 구성되며, 데이터 바인딩에 의해 이들이 연결됩니다. 컴포넌트의 주된 역할은 화면을 구성하는 뷰(View)를 생성하고 관리하는 것입니다. 화면은 1개 이상의 컴포넌트를 조립하여 구성됩니다. 컴포넌트는 . 뷰계층의 기본 단위로, 재사용 가능하고 독립적인 UI 요소를 정의합니다,


### 디렉티브
디렉티브는 애플리케이션 전역에서 사용할 수 있는 뷰(View) 관련 공통 관심사를 컴포넌트에 분리하여 구현한 것입니다. 이를 통해 컴포넌트의 복잡도를 낮추고 가독성을 높일 수 있습니다.디렉티브는 크게 
`구조 디렉티브`, `어트리뷰트`로 구분됩니다. 구조 디렉티브는 DOM 레이아웃을 변경하며, 어트리뷰트 디렉티브는 DOM 요소의 동작이나 외관을 변경합니다. 큰 틀에서 컴포넌트 또한 디렉티브의 . 한종류로 볼 수 있습니다.

### 서비스
서비스는 다양한 목적의 애플리케이션 공통 로직을 담당합니다. 컴포넌트에서 애플리케이션 전역 관심사를 분리하기 위해 사용하며, 의존성 주입이 가능한 클래스로 작성됩니다. 서비스는 `데이터 처리`, `API 호출`, 비즈니스 로직 등을 포함해 컴포넌트 간에 재사용될 . 수있는 로직을 제공합니다.

### 모듈
모듈은 기능적으로 구성된 구성 요소를 하나의 단위로 묶는 매커니즘을 말합니다. 모듈 관련이 있는 기능들이 응집된 기능 블록으로 애플리케이션을 구성하는 하나의 단위를 만듭니다. 모듈은 다른 모듈과 결합할 수 있으며, `Angular`는 여러 모듈을 조합하여 애플리케이션을 구성합니다.
`컴포넌트`,`디렉티브`,`파이프`, `서비스`등의 
`Angular`의 구성요소는 모듈에 등록되어야 사용할 . 수있습니다.
