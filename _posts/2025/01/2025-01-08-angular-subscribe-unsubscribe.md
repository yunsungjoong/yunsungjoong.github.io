---
layout: post
title: "[Angular / Rxjs] subscribe, unsubscribe"
tags: [Angular,Subscribe,unsubscribe]
categories: [Angular]
banner:
  image: ""
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---


`Rxjs`에서 `Observable`과 `asObservable`를 이용해 데이터를 주고 받고 변화한 값을 알아낸다.

## subscribe란?
현재 사용하고 있는 변수의 값이 변화했는지? 변화 했다면 어떻게 변화 했는지를 알고 대응하고 싶을때 사용하는 것이 `subscribe`이다.

## unsubscribe란?
`subscribe`는 엄청나게 편리한 기능이다. 하지만 편리한 만큼 잘못관리한다면 성능에 엄청난 영향을 미칠 수 있다. 이유는 간단하다. subscribe(구독)을 하게되는 순간 값이 변화하게 된다면 우리가 `unsubscribe`하거나 `complete`를 하지 않는다면 계속해서 관찰(동작)하게 되고 이는 곧 메모리 낭비 또는 의도치 않은 값의 변화를 유발할 수 있다.


### subscription
`subscription`은 내가 구독하고 있는 `subscribe`를 관리하기 위해 만들어준 변수라고 생각하면 된다. `interval`에 닮겨서 구독되어지고 있는 상황이고 그로 인해 `time`의 값은 계속해서 변하고 있다. 그러나 내가 화면을 클릭할 시 `timeSubscription`을 `unsubscribe`하게 되고 이후엔 `time` 값이 변하지 않아 console이 찍히지 않는 모습을 볼 수 있다.

### complete
`subscribe`를 구독완료 즉 앞으로 구독하지 않겠다. 내가 할 일은 완료되었다. 라는 뜻이다. `complete`를 하게되면 `time`을 다시 `new Subject`로 등록하지 않는 한 `time`이라는 `Subject` 변수는 더 이상 사용할 수 없게 된다.

[참고 URL](https://velog.io/@leehangeul/Angular-Rxjs-subscribe-unsubscribe)