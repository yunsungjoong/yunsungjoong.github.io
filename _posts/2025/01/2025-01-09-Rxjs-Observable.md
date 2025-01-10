---
layout: post
title: "[Rxjs] Observable"
tags: [Rxjs,Observable]
categories: [Rxjs]
banner:
  image: ""
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

# RxJS란? 
`RxJS`는 `Reactive Extensions For JavaScript` 라이브러리이다.
여기서 `Reactive Extensions` 는 `ReactiveX` 프로젝트에서 출발한 리액티브 프로그래밍을 지원하기 위해 확장했다는 뜻이다.

RxJS는 이벤트 스트림을 Observable 이라는 객체로 표현한 후 비동기 이벤트 기반의 프로그램 작성을 돕는다.

이벤트 처리를 위한 API로 다양한 연산자를 제공하는 함수형 프로그래밍 기법도 도입되어 있다.

## 리액티브 프로그래밍이란
리액티브 프로그래밍이란 이벤트나 배열 같은 데이터 스트림을 비동기로 처리해 변화에 유연하게 반응하는 프로그래밍 패러다임 이다.

외부와 통신하는 방식은 Pull 과 Push 시나리오가 있을 수 있다.

### Pull 시나리오
외부에서 명령하여 응답받고 처리한다.
데이터를 가지고 오기 위해서는 계속 호출해야 한다.

### Push 시나리오
외부에서 명령하고 기다리지 않고, 응답이 오면 그때 반응하여 처리한다
데이터를 가지고 오기 위해서 구독해야 한다.

Reactive Programming 은 Push 시나리오를 채택하고 있다.

```javascript
// javascript
function event() {
  // ...
};
const el = document.getElementsById('Button');
el.addEventListener('click', event)
```
targetElement를 가져와서 addEventListener 로 ‘click’ 이벤트를 구독하였다.
사용자가 마우스 클릭을 하기 전까지는 event function이 발생되지 않는다.

여기서 우리는 Reactive Programming 의 개념중 하나인 Observer Pattern 을 발견할 수 있다.

`Observer pattern`은 객체의 상태 변화를 관찰하는 옵저버들의 목록을 객체에 등록하여 상태 변화가 있을 때마다 메서드 등을 통해 객체가 직접 목록의 각 옵저버에게 통지하도록 하는 디자인 패턴이다.

`addEventListener` 로 `targetElement`가 `click` 이벤트를 구독하도록 옵저버를 등록한후,
click 이벤트가 발생하면 event function을 호출하여 옵저버에게 알린다.

## RxJS
비동기 코드가 많아지면 그만큼 제어의 흐름이 복잡하게 얽혀 코드를 예측하기 어려워진다.
`RxJS` 는 `Javascript` 의 비동기 프로그래밍의 문제를 해결하는데 도움을 준다.
`RxJS`는 `Observer` 패턴을 적용한 `Observable` 이라는 객체를 중심으로 동작한다.


## RxJS Observable
`Observable`은 특정 객체를 관찰하는 `Observer`에게 여러 이벤트나 값을 보내는 역할을 한다.

### observer에는 3가지 메서드가 존재한다.

1. next : Observable 구독자에게 데이터를 전달한다.
2. complete : Observable 구독자에게 완료 되었음을 알린다. next는 더 이상 데이터를 전달하지 않는다.
3. error : Observable 구독자에게 에러를 전달한다. 이후에 next 및 complete 이벤트가 발생하지 않는다.

## RxJS Observable Lifecycle
1) 생성
`Observable.create()`
생성시점에는 어떠한 이벤트도 발생되지 않는다.
2) 구독
`Observable.subscribe()`
구독시점에 이벤트를 구독할 수 있다.
3) 실행
`observer.next()`
실행시점에 이벤트를 구독하고 있는 대상에게 값을 전달한다.
4) 구독 해제
`observer.complete()`
`Observable.unsubscribe()`
구독 해제 시점에 구독하고 있는 모든 대상의 구독을 종료한다.



[참고 URL](https://pks2974.medium.com/rxjs-%EA%B0%84%EB%8B%A8%EC%A0%95%EB%A6%AC-41f67c37e028)