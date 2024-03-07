---
layout: post
title: "[React] 리액트에서 자주쓰이는 자바스크립트 문법 정리 "
tags: [React, JavaScript]
categories: [JavaScript, React]
banner:
  image: "/assets/images/banners/2024/0201/React.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

# 🔍 React 장점

> 1. 새로고침X -> 않아도 자동으로 업데이트

> 2. 코드 재사용성⬆️ ( 가용성이 좋다)

> 3. JSX문법

- `HTML` + `JavaScript`
- `HTML` 컴포넌트 와 관련된 함수를 뭉쳐 세트로 만든다. 그리고 이 세트는 컴포넌트 라고 한다.

---

## 📋useMemo란?

`useMemo`는 리액트에서 컴포넌트의 성능을 최적화 하는데 사용되는 `Hook`입니다
`useMemo`에서 memo는 `MEMOIZATION`을 뜻하는데 이는 그대로 해석하면 '메모리에 넣기' 라는 의미이며 컴퓨터 프로그램이 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거해 프로그램 실행 속도를 빠르게 하는 기술입니다.

쉽게 말하면 동일한 값을 반환하는 함수를 반복적으로 호출해야한다는 처음 값을 계산할 때 해당 값을 메모리에 저장해 필요할 때마다 다시 계산하지 않고 메모리에서 꺼내서 재사용하는 것입니다.

리액트에서 함수형 컴포넌트는 렌더링 => 컴포넌트 함수 호출 => 모든 내부 변수 초기화의 순서를 거칩니다.

---

useMemo를 사용하면 함수 컴포넌트 내부에서 발생하는 연산을 최적화할 수 있습니다.
먼저 리스트에 숫자를 추가하면 추가된 숫자들의 평균을 보여 주는 함수 컴포넌트를 작성하겠습니다.

```javascript
import { useState } from "react";

const getAverage = (numbers) => {
  console.log("평균값 계산 중...");
  if (numbers.length === 0) return 0;
  const sum = numbers.reduce((a, b) => a + b);
  return sum / numbers.length;
};

const Average = () => {
  const [list, setList] = useState([]);
  const [number, setNumber] = useState("");

  const onChange = (e) => {
    setNumber(e.target.value);
  };

  const onInsert = (e) => {
    const nextList = list.concat(parseInt(number));
    setList(nextList);
    setNumber("");
  };

  return (
    <div>
      <input value={number} onChange={onChange} />
      <button onClick={onInsert}>등록</button>
      <ul>
        {list.map((value, index) => (
          <li key={index}>{value}</li>
        ))}
      </ul>
      <div>
        <b>평균값:</b>
        {getAverage(list)}
      </div>
    </div>
  );
};

export default Average;
```

다음으로 App에서 컴포넌트를 렌더링 하세요

```javascript
import Average from "./Average";

const App = () => {
  return <Average />;
};

export default App;
```

위 코드는 React를 사용하여 간단한 평균값 계산기를 만드는 예제입니다.
`useState` 훅을 사용하여 숫자 목록과 입력값을 관리하고,
입력값을 리스트에 추가하여 평균값을 계산합니다. 사용자는 숫자를 입력하고 '등록' 버튼을 클릭하여 숫자를 추가할 수 있습니다.
이 코드를 통해 `React`의 기초 개념 및 상태 관리 방법을 이해할 수 있습니다

<br />

브라우저에서 숫자들을 등록하면 평균값이 나타납니다.

<img src="/assets/images/img/Gitblog_img/2024_02_22/useMemo.png">

### useState 훅 사용:

- useState 훅을 사용하여 두 가지 상태를 선언합니다.
- list: 입력된 숫자들을 저장하는 배열 상태입니다.
- number: 입력 필드에 입력된 값을 저장하는 문자열 상태입니다.

### getAverage 함수:

- 배열을 매개변수로 받아 해당 배열의 평균값을 계산하는 함수입니다.
- 입력된 배열이 비어있으면 0을 반환합니다.
- 그렇지 않으면 배열의 합을 구하고, 배열의 길이로 나누어 평균값을 계산합니다.

### Average 함수 컴포넌트:

- 함수형 컴포넌트 `Average`를 선언합니다.
- list와 `number` 상태를 `useState` 훅을 사용하여 선언합니다.
- onChange 함수는 입력 필드의 값이 변경될 때마다 호출되어 `number` 상태를 업데이트합니다.
- onInsert 함수는 등록 버튼이 클릭될 때 호출되며,
  `number` 값을 `list` 배열에 추가한 다음 number 상태를 초기화합니다.
- JSX를 반환하여 사용자가 숫자를 입력할 수 있는 입력 필드와 등록 버튼을 렌더링합니다.
- 입력된 숫자들을 보여주기 위해 `list` 배열을 매핑하여 숫자 목록을 만듭니다.
- 평균값을 표시하기 위해 getAverage 함수를 호출하여 `list` 배열의 평균값을 계산합니다.

## useMemo 사용해보기

<b>`useMemo` Hook은 렌더링하는 과정에서 특정 값이 바뀌었을 때만 연산을 실행하고
원하는 값이 바뀌지 않았다면 이전에 연산했던 결과를 다시 사용하는 방식이다</b>

```javascript
import React, { useState } from "react";

const getAverage = (numbers) => {
  console.log("평균값 계산중..");
  if (numbers.length === 0) return 0;
  const sum = numbers.reduce((a, b) => a + b);
  return sum / numbers.length;
};

const Average = () => {
  const [list, setList] = useState([]);
  const [number, setNumber] = useState("");
  const onChange = (e) => {
    setNumber(e.target.value);
  };
  const onInsert = (e) => {
    const nextList = list.concat(parseInt(number));
    setList(nextList);
    setNumber("");
  };
  const avg = useMemo(() => getAverage(list), [list]);
  return (
    <div>
      <input value={number} onChange={onChange} />
      <button onClick={onInsert}>등록</button>
      <ul>
        {list.map((value, index) => (
          <li key={index}>{value}</li>
        ))}
      </ul>
      <div>
        <b>평균값:</b>
        {avg}
      </div>
    </div>
  );
};

export default Average;
```

위에 코드에서 `useMemo` 는 `getAverage` 함수의 결과를 메모이제이션해 , `list` 배열이 변경될 때만
평균값을 다시 계산합니다. 이렇게 함으로써, 리스트에 변화가 없는 한 평균값을 반복해서 계산하는 비효율성을 줄일 수 있습니다.

즉, `useMemo` 를 사용하면 성능을 최적화하고, 불필요한 계산을 피할 수 있습니다.

이 글은 김민준(velopert)님의 <b>리액트를 다루는 기술을참조 </b>하여 작성한 글입니다.
