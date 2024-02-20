---
layout: post
title: "[React] 리액트 Hoos_1 useState,useEffect "
tags: [React, useState, useEffect]
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
- 상태(State)란 ?
  - 컴포넌트 내부에 변경될 수 있는 값 props는 부모 컴포넌트로부터 넘겨 받으므로, 컴포넌트 자신은 props를 바꾸지 못하는 특성이 있는 것과는 차이가 있습니다.

---

## useState

함수형 컴포넌트에서도 상태(state)관리를 할 수 있게 해 주는 Hook 입니다.
카운터 값을 증가시키거나 감소시키는 카운터를 구현하는 코드를 짠다고 가정해 보겠습니다. 여기에서 카운터 값이 될 상태 값을
`useState` 함수를 이용해 변할 수 있게 짤 수 있습니다.

> Step1 함수형 컴포넌트에서 state를 관리할 수 있도록 useState import 하고

```javascript
import { useState } from "react";

const Counter = () => {
  const [value, setValue] = useState(0);

  return <div></div>;
};

export default Counter;
```

- useState 함수를 이용하려면 import에 {useState}를 필히 넣어야 합니다.
- 함수 body에 `const [value, setValue] = useState(0);` 라고 쓴 부분이 있습니다. 이것은 처음 상태값
  (value)을 0으로 초기화하고, 그 상태값을 변경할 수 있는 setter 함수를 setValue라고 지정한 것입니다.

> step2 return문에 상태값을 변경할 수 있는 버튼을 넣기

```javascript
import { useState } from "react";

const Counter = () => {
  const [value, setValue] = useState(0);
  return (
    <div>
      <p>
        현재 카운터 값은 <b>{value} 입니다.</b>
      </p>
      <button onClick={() => setValue(value + 1)}>+1</button>
      <button onClick={() => setValue(value - 1)}>-1</button>
    </div>
  );
};
export default Counter;
```

- 버튼 onClick 함수를 지정하고, 그 함수 내부에, useState 함수를 활용하면 됩니다. 지정했던 setter 함수인 setValue함수를 사용 합니다.
- 위 처럼 작성한 형식은 화살표 함수 문법입니다. 즉, 사전에 함수를 따로 지정하고 그 함수 이름을 호출하지 않고도 단순하게 함수 body를 작성할 수 있습니다.
- 화살표 함수 문법은 () => {...body} 와 같은 형태로 작성하는데, 위처럼 body에 들어갈 내용이 하나 뿐이라면 `{, }`
  를 생략할 수 있습니다.

<img src="/assets/images/img/Gitblog_img/2024_02_20_01/Counter.png">

## useState를 여러 번 사용하기

useState 함수는 하나의 상태 값만 관리할 수 있습니다. 컴포넌트에서 관리해야

```javaScript
const [value, setValue] = useState(0);
```

할 상태가 여러 개라면 useState를 여러 번 사용하면 됩니다.

```javaScript
const [name, setName] = useState("");
const [nickname, setNickname] = useState("");

const onChangeName = (e) => {
  setName(e.target.value);
};
const onChangeNickname = (e) => {
  setNickname(e.target.value);
};
```

<img src="/assets/images/img/Gitblog_img/2024_02_20_01/mmm.png">

- name, nickname 이라는 두 가지 상태를 사용할 수 있습니다.
- input 에서 무언가 값을 입력 받을 때, `onChange` 이벤트 핸들링을 위해 onChangeName 등과 같은 함수를 미리 만들어 둔 것입니다.
- 만약 `input` 요소에서 `onChnage` 이벤트 핸들링을 하지 않을 경우, 사용자가 `input`란에 무엇을 입력하더라도 칸에는 아무것도 보이지 않게 됩니다.

---

## useEffect

`useEffect` 는 리액트 컴포넌트가 렌더링될 때마다 특정 작업을 수행하도록 설정할 수 있는 Hook 입니다.
클래스형 컴포넌트의 `componentDidMount`와 `componentDidUpdate`를 합친 형태로 보아도 무방합니다.

이 글은 김민준(velopert)님의 <b>리액트를 다루는 기술을참조 </b>하여 작성한 글입니다.
