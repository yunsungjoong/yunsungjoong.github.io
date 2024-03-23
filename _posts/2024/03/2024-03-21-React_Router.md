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

# 1. Routing 이란?

> 라우팅이란, 어떤 주소에서 어떤 UI를 보여줄 것인가 규칙을 정하는 작업을 말합니다.

과거의 라우팅은 주로. ㅓ버에서 처리했지만, 최근 웹에서는 클라이언트가 관리합니다.



# 2, React-Router 

### React-Router
리액트에서 SPA를 만들기 위해 가장 많이 사용되는 라이브러리이며
컴포넌트를 기반으로 라우팅 합니다.

<b>Next</b>
파일 경로, 이름을 기반으로 라우팅합니다. SSR, Code Splitting 을 매우 쉽게 구현할 수 있습니다.





# 3. react-router 사용해보기

<b>npm</b>
> npm install react-router-dom
> npm install react-router

<b>yarn</b>
> yarn add react-router-dom
> yarn add react-router



## index.js 수

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