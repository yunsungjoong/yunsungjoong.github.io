---
layout: post
title: "[React] useEffect"
tags: [React, useEffect]
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

# 🔍 리액트 Hooks

- 리액트에서 클래스형 컴포넌트와 함수형 컴포넌트가 있습니다. 그 중에 Hooks는 함수형 컴포넌트에서 사용하는 기능입니다.
- Hooks는 기존에 함수형 컴포넌트에서 할 수 없었던 상태 관리나, 렌더링 후 작업을 설정하는 기능 등의 작업을 할 수 있게 해줍니다.

---

## useEffect

`useEffect` 는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook 입니다.
클래스형 컴포넌트의 `componentDidMount`와 `componentDidUpdate`를 합친 형태로 보아도 무방합니다.

`useEffect`도 사용하려면 import가 필수입니다.

```javascript
useEffect(() => {
  console.log("렌더링 완료");
  console.log({
    name,
    nickname,
  });
});
```

개발자 도구를 확인할 경우, input 란에 무언가 값을 입력할 때마다 리렌더링 되고 콘솔에는 바뀌는 name이나 nickname 값이
출력될 것입니다.

- useEffect에서 설정한 함수 내용을, 컴포넌트가 화면에 맨 처음 리렌더링 될때만(마운트될 때) 실행하고 업데이트 될 때는
  실행하지 않게 할 경우 두 번째 인자에 비어있는 배열인 []

```javascript
useEffect(() => {
  console.log("렌더링 완료. 마운트될 때만 실행");
}, []);
```

- 반대로 특정 state 값이 변할 때마다 작업을 수행하려면 두 번째 인자에 [상태명]으로 입력하여 넣으면 됩니다.
- 아래 코드를 작성하면 name을 input에 입력할 때마다 name 값이 바뀌고 콘솔에 로그가 찍힐 것입니다.

```javascript
useEffect(() => {
  console.log(name);
}, [name]);
```

- 이처럼 useEffect 함수의 두 번째 파라미터 배열에 어떤 것을 넣느냐에 따라 실행되는 조건이 달라집니다.

이 글은 김민준(velopert)님의 <b>리액트를 다루는 기술을참조 </b>하여 작성한 글입니다.
