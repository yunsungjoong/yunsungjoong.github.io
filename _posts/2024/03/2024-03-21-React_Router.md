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

# 1, Router 라이브러리 Install

<b>npm</b>
> npm install react-router-dom
> npm install react-router

<b>yarn</b>
> yarn add react-router-dom
> yarn add react-router



# index.js 수정

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
import Aboutpage from './page/aboutpage';

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

const aboutpage = () => {
    return (
        <div>
            Aboutpage
        </div>
    );
};

export default aboutpage;
```

### 렌더링 결과입니다
<img src="/assets/images/img/Gitblog_img/2024/03/router-about.png"/> 