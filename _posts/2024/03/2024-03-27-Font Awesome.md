---
layout: post
title: "[React] React에서 Font Awesome 사용하기"
tags: [React, Font Awesome]
categories: [React, Font Awesome]
banner:
  image: "/assets/images/banners/2024/0201/React.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

[Font Awesome 공식문서](https://docs.fontawesome.com/)



## 1. Font Awesome 설치
---

npm 또는 yarn 사용해 아래와 같은 명령어로 설치 가능합니다.

```bash
// npm 일 경우
npm i --save @fortawesome/fontawesome-svg-core
npm install --save @fortawesome/free-solid-svg-icons
npm install --save @fortawesome/react-fontawesome
// 추가 아이콘 사용시
npm install --save @fortawesome/free-brands-svg-icons
npm install --save @fortawesome/free-regular-svg-icons


// yarn 일 경우
yarn add @fortawesome/fontawesome-svg-core --save-dev
yarn add @fortawesome/free-solid-svg-icons --save-dev
yarn add @fortawesome/react-fontawesome --save-dev
// 추가 아이콘 사용시
yarn add @fortawesome/free-brands-svg-icons --save-dev
yarn add @fortawesome/free-regular-svg-icons --save-dev
```

> package.json 에서 위와 같은 내용이 설치 된 것을 알 수 있습니다.

## 2. FontAwesome 을 React에서 사용하기
---

무료 애플 로고를 사용하기 위해 Free 와 Brands 를 누르면 찾을 수 있습니다.

<img src="/assets/images/img/Gitblog_img/2024/04/03_27_img_01.png"/> 

해당 이미지는 HTML에서 아래와 같이 사용 가능합니다.

```javascript

// html 
<i class="fa-solid fa-mug-saucer"></i>
```

하지만, React 에서는 아래와 같이 사용해야 합니다.


```javascript

import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
import { faCoffee } from '@fortawesome/free-solid-svg-icons';

<FontAwesomeIcon icon={faCoffee}/>

```

결과 화면입니다.

<img src="/assets/images/img/Gitblog_img/2024/04/03_27_img_03.png"/> 

Font Awesome Icon 을 가져와 icon은 brands 에 있는 faCoffee 를 사용한다는 의미로 해석했습니다.

