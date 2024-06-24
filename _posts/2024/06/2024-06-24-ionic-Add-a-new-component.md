---
layout: post
title: "[Ionic] 쿰포넌트 생성"
tags: [ionic,angular]
categories: [ionic]
banner:
  image: "/assets/images/banners/2024/06/19-ionic.png"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

# 새 컴포넌트를 추가 해야 할 때
현재 환경 : mac m1 / Ionic5 / angular(TypeScript)
/src/app 하위에 heroes 컴포넌트에 대한 폴더가 생성되고
하위에 총 4개 파일

- <컴포넌트명>.component.ts 컴포넌트 파일
- <컴포넌트명>.component.html 템플릿 파일
- <컴포넌트명>.component.css CSS 스타일 파일
- <컴포넌트명>.component.spec.ts 테스트 파일이 생성된다.


## Ionic Component 생성

컴포넌트는 아래 명령어로 생성할 수 있습니다.
줄여서 `ng g c 컴포넌트이름`으로도 생성이 가능합니다.

```
ng generate component 컴포넌트명
```

1) CREATE : html, css, ts, spec,ts 파일 생성
- html, css 파일 그리고 ts(typeScript)까지는 알겠는데 spec.ts 라는 파일도 생성되었습니다.
- spec.ts는 컴포넌트 유닛 테스트를 위한 스펙 파일이라고 하며, 없어도 된다고 합니다.

<img width="582" alt="component-creat" src="https://github.com/yunsungjoong/ionic-angular-study/assets/96567925/0a086c0d-8246-482b-a075-efb20ce00c45">

2) UPDATE : src/app/app.module.ts 파일이 업데이트 

새로 생성한 컴포넌트를 앱에서 사용하기 위해 등록하는 동작입니다.

<img width="529" alt="appModuleComponent" src="https://github.com/yunsungjoong/ionic-angular-study/assets/96567925/58f6c793-3d3f-4544-9694-a142f36e3be5">

`import`한 컴포넌트를 `declarations`에 추가하는 내용으로 제가 생성한 컴포넌트(ItemDetail)에 맞게
7번,12번 라인이 추가되었습니다.

추가로 커맨드를 사용해 컴포넌트를 생성하지 않고 임의로 복붙하여 만드는 경우 역시 
app.module.ts에 동일한 내용을 추가해 주어야 사용이 가능합니다.



<U></U>

참고 

[블로그 참고](https://nagy.tistory.com/30)
