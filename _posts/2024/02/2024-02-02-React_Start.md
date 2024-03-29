---
layout: post
title: "[React] 리엑트 시작하기 "
tags: [React]
categories: [React]
banner:
  image: "/assets/images/banners/2024/0201/React.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

이 글은 김민준(velopert)님의 <b>리액트를 다루는 기술을참조 </b>하여 작성한 글입니다.

# 1-1 왜 리엑트인가?

JS만으로도 규모가 큰 애플리케이션을 만들 수 있는 시대가 됬다. <br/>
규모가 큰 애플리케이션을 관리하기 위해 만들어진 수많은 프레임워크들이 있다. <br/>
이 프레임워크들ㅇ느 주로 MVC(Model-View-Controller), MVVM(Model-View-View Model) 아키텍처를 사용한다.

- 모델(Model) : 애플리케이션에서 사용하는 데이터를 관리하는 영역

- 뷰(View) : 사용자에게 보이는 부분

- 컨트롤러(Controller) : 사용자의 입력이나 조작에 따라 모델 데이터를 조회, 수정하고 반영함.

---

📌 리액트는 오직 뷰(View)만을 신경쓰는 라이브러리이다.
어떤 데이터가 변할 때마다 어떤 변화를 줄지 고민하는 것이 아니라 그냥 기존 뷰를날려버리고 처음부터 새로 렌더링하는 방식

---

## 리액트 이해

리액트는 특정 부분이 어떻게 생길지 정하는 선언체인 컴포넌트(Component) 단위로 프로젝트를 관리한다. <br />
컴포넌트는 재사용이 가능한 API로, 수많은 기능들을 내장하고 있으며 생김새와 작동 방식을 정의한다. <br />
사용자 화면에 뷰를 보여주는 것을 렌더링이라고 하는데, 최초로 실행한 '초기 렌더링 '과 데이터 변경으로 다시 실행되는 '리렌더링'이 있다.

### 초기 렌더링

초기 렌더링은 맨 처음 어떻게 보일지를 정한다. 리액트에서는 이를 render() 함수로 다룬다. <br />
이 함수는 컴포넌트의 뷰가 어떻게 생겼고 어떻게 작동하는지에 대한 정보를 가진 객체를 반환한다.

render 함수를 실행하면

- 내부에 있는 컴포넌트들도 재귀적으로 렌더링하고

- 렌더링이 끝나면 지니고 있는 정보들을 사용하여 HTML 마크업을 만들고

- 실제 페이지의 DOM 요소 안에 주입한다.

### 조화 과정

리엑트에서 뷰를 업데이트 하는 것은 "조화 과정을 거친다" 고 할 수 있다. 변화에 따라 뷰가 변형되는 것이 아니라 새로운 요소로 갈아 끼우기 때문이다.
컴포넌트 데이터를 업데이트 했을 때 업데이트 한 값을 수정하는 것이 아닌 새로운 데이터를 가지고 `render` 함수를 다시 호출한다.

이 때, render 함수가 반환하는 결과를 곧바로 DOM에 반영하는 것이 아니라 이전 컴포넌트 정보와 현재 render 함수가 만든 컴포넌트 정보를 비교하여, 최소한의 연산으로 둘의 차이를 알아내고, DOM 트리를 업데이트 한다.

이러한 방식으로 최대한 성능을 아끼고, 사용자 경험을 개선하기 위해 만든 것이 리액트이다.

---

## 리액트의 특징

## Virtual DOM

### DOM이란?

DOM은 Document Object Model의 약어. 객체로 문서 구조를 표현하는 방법으로 HTML이나 XML로 작성한다.

웹 브라우저는 DOM을 활용하여 객체에 JS와 CSS를 적용한다. DOM은 트리 형태로, 특정노드를 찾거나 수정하거나 제거하거나 원하는 곳에 삽입할 수 있다.

DOM의 단점은 동적 UI에 최적화되어 있지 않다는 것이다. 페이스북에서 스크롤바를 내렸을 때 수많은 데이터가 로딩되는 것을 생각해보자. (페이스북에서 포스트 한 개에새용되는 `<div>` 요소의 수는 약 100개이다.)

이처럼 DOM에 변화가 일어날 때 웹 브라우저는 CSS를 다시 연산하고 레이아웃을 구성하고, 페이지를 리페인트해야 하기 때문에 DOM을 최소한으로 조작해야 성능 이슈를 막을 수 있다.

### Virtual DOM

리액트는 Virtual DOM 즉 실제 DOM에 직접 접근하여 조작하는 대신 이를 추상화한 JS 객체를 구성하여 사용한다. (실제 DOM의 가벼운 사본이라 할 수 있다!)

리액트에서는 데이터가 변해 DOM을 업데이트할 때는 다음의 절차를 밟는다.

1. 데이터를 업데이트하면 전체 UI를 Virtual DOM에 리렌더링한다.

2. Virtual DOM에 있던 내용과 현재 내용을 비교한다.

3. 바뀐 부분만 실제 DOM에 적용한다.

리액트의 Virtual DOM 방식이 무조건 빠른 것이 아니다. 다음은 리액트 메뉴얼에 있는문장이다.

- 📌 지속적으로 데이터가 변화하는 대규모 애플리케이션 구축하기

Virtual DOM이 제공할 수 있는 것은 <b>업데이트 처리 간결성</b>이다.

---

## 기타 특징

리액트는 프레임워크가 아니라 라이브러리. (Vue.js, Angular.js는 프레임워크) 따라서 Ajax, 데이터 모델링, 라우팅 등의 기능은
직접 구현하거나 다른 라이브러리를 사용하거나 다른 웹 프레임워크와 혼용해서 사용해야 한다.
