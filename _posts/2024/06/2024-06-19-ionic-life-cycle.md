b---
layout: post
title: "[ionic] Ionic life cycle 정리"
tags: [ionic,angular]
categories: [ionic]
banner:
  image: "/assets/images/banners/2024/06/17-nvm.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

## Ionic Page Life Cycle 

근무하고 있는 곳에서 `Ionic & Angular` 로 구축된 모바일 프로젝트 진행 중이다.
`Page life cycle`가 어떤 순서로 작동하는지 알아둘 필요가 있어 공부겸 정리해본다.


## Ionic 페이지 생명 주기

`Ionic` 및 `Angular`로 구축된 앱에서 페이지 수명 주기가 작동하는 방식을 다룹니다.
생명주기는 아래 순서대로 이벤트가 발생합니다. `Ionic`에서 `Angular`의 생명주기 이벤트도 수용하고 있기 때문에, `Angular` 로 구현되어 있다면
`Angular`의  `LifeCycle`도 같이 고려해 보아야 한다.

![image](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/7a77d13c-d02a-40ac-a7a4-d5141bfdb24e)

1. ngOnInit
2. ionViewWillEnter
3. ionViewDidEnter
4. ionViewWillLeave
5. ionViewDidLeave
6. ngOnDestory

1번과 6번을 제외하고는 비슷한 단어라 유추하기 쉽다. 
1번과 6번은 `Angular`에서 제공하는 대표적인 생명 주기 이벤트이고 
나머지는 Ionic에서 제공하기 때문에 Ionic에서 제공하기 때문에 ion이라는 키워드가 붙는다

--- 

## Angular 생명주기 이벤트

| 이벤트 이름 | 설명 |
|----------|----------|
| ngOnInit   | 컴포넌트 초기화 중에 1번 실행된다. 로컬 멤버를 초기화하고 딱 한 번만 수행하면 되는 서비스를 호출할 때 사용한다.   |
| ngOnDestroy | Angular가 해당 뷰를 파괴하기 직전에 실행된다. 예를 들어 Observable 구독 취소 같이 정리시 유용하다.   |



## Ionic 생명주기 이벤트

`Ionic` 생명주기 이벤트는 쉽게 설명하자면 처음 페이지에 들어갈 경우 2,3번이 호출되고 해당 페이지를 나가면 4,5번이 호출된다.

| 이벤트 이름 | 설명 |
|----------|----------|
| ionViewWillEnter   | 페이지가 로드되고, active 되기 전에 호출된다. event listener 등 뷰에 진입하는 초기에 해야 하는 작업들을 선언하기에 적합하다.   |
| ionViewDidEnter | 페이지가 active 된 직후에 호출된다. 직전 ionViewWillEnter와 비슷하게 사용한다. (데이터 로드시 ionViewWillEnter를 사용해 성능 문제가 발생하면 대신 ionViewDidEnter에서 데이터 호출을 수행할 수 있다)  |
| ionViewWillLeave   | 페이지에서 나가고, active 상태가 해제되기 직전에 호출, event listener의 해제 등, 페이지를 나가는 시점에 해야 하는 작업들을 선언하기에 적합하다.   |
| ionViewDidLeave | 페이지가 active 상태가 해제된 직후에 호출된다.   |



## Ionic & Angular 생명주기 예시 

아래는 ionic docs에서 제공하는 Ionic & Angular lifeCycle 예시다, 2개의 페이지를 왔다갔다 이동하면서 Ionic 생명주기의 순서를 확인할 수 있다.

![ioniclifecycle-test](https://github.com/yunsungjoong/yunsungjoong.github.io/assets/96567925/63fef148-2e30-48ce-a4f9-f5fcca4cb31e)


### page 1 페이지 진입시 생명주기

- page 1 ngOnInit   // 최초 1번만 실행
- page 1 ionViewWillEnter // page 1 진입 예정
- page 1 ionViewDidEnter   // page 1 진입

### page 1 -> page 2 버튼 클릭시 생명주기

- page 2 ngOnInit   // 최초 1번만 실행
- page 1 ionViewWillLeave
- page 2 ionViewWillEnter   // page 2 진입 예정
- page 2 ionViewDidEnter   // page 2 진입
- page 1 ionViewDidLeave


### page 2 -> oage 1 버튼 클릭시 생명주기

- page 2 ionViewDidLeave
- page 1 ionViewWillEnter   // page 1 진입 예정
- page 1 ionViewDidEnter   // page 1 진입
- page 2 ionViewDidLeave
- page 2 ngOnDestroy

<br>
---

## 정리

페이지 진입 시에는 `angular`가 먼저 시작된 후 `ionic`이 실행되며,
페이지를 나갈 때에는 `ionic`이 먼저 종료된 이후, `angular`가 종료된다.


참고 
[ionic Docs](https://ionicframework.com/docs/angular/lifecycle)
[블로그 참고](https://velog.io/@msdio/ionic-lifecycle)
