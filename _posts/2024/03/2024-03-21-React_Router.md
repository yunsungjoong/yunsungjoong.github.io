---
layout: post
title: "[React] React-Router "
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

## Router란?

`React Router`는 `React` 애플리케이션에서 페이지 간의 네비게이션 및 URL 경로에 따른 컴포넌트 렌더링을 관리하는 라이브러리입니다. 주요 기능으로는 선언적 라우팅, 동적 라우팅, 중첩된 라우팅, 그리고 프로그래밍 방식 라우팅을 제공합니다. `React Router`를 사용하면 
SPA를 쉽게 구축하고 복잡한 라우팅 로직을 간단하게 처리할 수 있습니다.


---

## react-router-dom

`react-router-dom`은 `react-router v4` 버전에서 처음 릴리즈 된 라우팅 모듈로, `react-router` 모듈에 `dom`이 바인딩 되어 있는 모듈이다. v3버전까진 `react-router` 모듈 하나만을 사용할 수 있었는데, v4버전 이후 `react-router` 모듈을 코어로, 웹 개발자를 위한 `react-router-dom`과 앱 개발자를 위한 `react-router-native`가 릴리즈 되었다. 우리는 웹을 주로 개발할 것이니 react-router-dom 을 중점으로 사용할 것이다.

---



## React-Router의 주요 컴포넌트

### BrowserRouter
- `HTML5` `History API` 를 사용하며 주소만 바꾸고 페이지는 다시 불러오지 않습니다.
- 서버측에 새로운 요청을 하지 않으며 이를 통해 'history' 를 남겨 SPA에서 '뒤로가기' 를 구현할 수 있습니다.

### Routes
`Route`로 생성된 자식컴포넌트 중에 path와 URL이 매칭되는 첫번째 Route의 컴포넌트를 렌더링 한다.

> 이전의 Switch가 Routes로 바뀌었다. </br>
> `Route` : 컴포넌트 별로 원하는 url을 지정한다. </br>
> `Link` : 클릭시 지정한 URL로 이동하는 링크를 생성한다.  </br> 아예 새로운 페이지를 불러오므로 기존 컴포넌트의 상태값은 소멸된다.

---

## BrowserRouter, Routes, Route
위의 세 컴포넌트는 SPA 구조에서 전체적인 라우팅 틀을 잡기 위해 사용한다. 라우팅 하고 싶은 컴포넌트들을 `<BrowserRouter>`,`<Routes>`로 감싸고 `<Route>`로 컴포넌트에 해당하는 URL을 지정해준다. 아래의 코드는 간단한 라우팅 컴포넌트인데, * 같은 경우 와일드카드처럼 해당되는 모든 URL에 대해 대응한다. 이 때 순서가 중요한데, 만약 와일드카드로 지정한 `<NotFound>`의 라우트가 상단에 배치될 경우, 다른 URL로 라우팅 되야하는 경우에도 `<NotFound>`만 라우팅하게 된다. 이는 원래 의도한 동작과는 큰 차이가 있을 것이다.

---

## Link
- 사용한 `Router` 의 주소를 바꿉니다.
- a태그와 동일하지만 <b>새로고침이 되지 않습니다.</b>
```javascript
<Link to="/about">Goto Aboutpage </Link>
```

특정 주소로 넘어갈 수 있게 해준다. `path`는 상대 경로로 표현하는데, `.` ,`..` 같은 문법도 사용할 수 있다.


## useNaviGate
> 이전의 useHistory가 useNavigate로 바뀌었다.


---

### v6
```javascript
import React from 'react';
import { useNavigate } from 'react-router-dom'; 
const Aboutpage = () => {
    const navigate = useNavigate();
    const goToHompage = () => {
        navigate('/')

    }
    return (
        <div>
            <h1>Aboutpage</h1>
            <button onClick={goToHompage}>Go to Homepage</button>
        </div>
    );
};

export default Aboutpage;
```

## useMatch

```javascript
import { useMatch } from "@reach/router"

const App = () => {
  const match = useMatch('/hot/:item');

  return match ? (
    <div>Hot {match.item}</div>
  ) : (
    <div>Uncool</div>
  )
)
}
```
컴포넌트가 렌더링된 시점의 url가 인자 안의 url이 동일한지를 체크한다. 동일하다면 정보를 담은 객체가, 동잃지 않다면 null을 리턴한다.

> 객체

```javascript
params: {}
pathname: "/pro"
pathnameBase: "/pro"
pattern: {path: "/pro", caseSensitive: false, end: true}
```

## Restful Route

<img src="/assets/images/img/Gitblog_img/2024/04/03_23_Restful_Router.png" /> 
`Restful Router`는 `HTTP` 명령어와 URL을 일치시켜 통일성 있는 URL 디자인을 제공하는 방식입니다. 주로 다음과 같은 `HTTP` 명령어를 사용합니다:

- GET: 데이터를 가져오는 데 사용됩니다.
- POST: 데이터를 생성하는 데 사용됩니다.
- PUT: 데이터를 수정하는 데 사용됩니다. (때로는 PATCH로도 불립니다)
- DELETE: 데이터를 삭제하는 데 사용됩니다.
`Restful Router`는 `URL`을 단순하고 일관된 패턴으로 설계함으로써 가독성을 향상시키고 개발자 간의 협업을 용이하게 만듭니다. 
예를 들어, 쇼핑몰에서는 아이템을 다루는 페이지에서 모든 `CRUD(Create, Read, Update, Delete)` 작업을 하나의 `URL` 패턴 아래에서 수행합니다. 
이를 통해 개발자는 일관된 URL 구조를 유지하면서도 각각의 기능에 대한 `HTTP` 명령어를 명확하게 사용하여 `API`를 설계할 수 있습니다. 
이는 코드의 가독성과 유지 보수성을 높이며, `API`의 확장성과 재사용성을 향상시킵니다. 따라서, `Restful Router는 API` 디자인을 단순화하고 효율적으로 관리할 수 있는 방법으로 활용됩니다.

# 3. react-router 사용해보기

<b>npm</b>
> npm install react-router-dom
> npm install react-router

<b>yarn</b>
> yarn add react-router-dom
> yarn add react-router



## index.js 

이 코드에서
```javascript
import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);

reportWebVitals();

```

아래 코드로 수정
```javascript

import React from 'react';
import ReactDOM from 'react-dom/client';
import './index.css';
import App from './App';
import reportWebVitals from './reportWebVitals';
import { BrowserRouter } from 'react-router-dom';

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(
  <BrowserRouter>
      <App />
  </BrowserRouter>
);

reportWebVitals();

```

## 사용 예시
- 라우터를 사용하기 전에 (App, HomPage, AboutPage )

### ex) App.js
```javascript
import './App.css';
import { Routes, Route } from 'react-router-dom';
import Homepage from './page/Homepage';
import Aboutpage from './page/Aboutpage';

function App() {
  return (
    <div>
      <Routes>
        <Route path="/" element={<Homepage />} />
        <Route path="/about" element={<Aboutpage />} />
      </Routes>
    </div>
  );
}

export default App;
```

### ex)Homepage
```javascript
import React from 'react';

const Homepage = () => {
    return (
        <div>
            Homepage
        </div>
    );
};

export default Homepage;
```

### ex)aboutpage
```javascript
import React from 'react';

const Aboutpage = () => {
    return (
        <div>
            Aboutpage
        </div>
    );
};

export default Aboutpage;
```

### 렌더링 결과입니다
<img src="/assets/images/img/Gitblog_img/2024/03/router-about.png"/> 