---
layout: post
title: "[API] json server를 사용해보자"
tags: [API, json-server]
categories: [API, json-server]
banner:
  image: "/assets/images/banners/2024/0201/React.jpeg"
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---


최근에 json-server를 통해 간단하게 쇼핑몰 프로젝트를 수행했다. 
쉽게 테스트버서를 사용할 수 있는 느낌이었는데, 알아두면 유용할 것 같아서 정리해 두고자 한다.   

## 🔍 json-server란

`json-server`란 , 가짜 `API`서버를 만드는 툴이다. 짧은 시간동안 `REST API`가 필요할 때, 간단하게 만들어서 테스트해 볼 수 있다. 
API가 만들어지기 전에 연결 작업을 진행할 때 사용하면 유용할 것 같다.

설치와 사용방법 모두 간단하다. 먼저, npm & yarn 을 통해 설치한다.


### json-server 설치
```zsh

# npm 
npm install -g json-server

# yarn 
yarn global add json-server
```
먼저 폴더를 생성하고 폴더 아래에 db.json 파일을 만들었다. 파일 안에는 아래와 같이 
`products` 이라는 이름의 array 형태로 저장하였다. 

```json
{
  "id": "1",
  "img": "https://noona-hnm.netlify.app/ankle-jeans.jpeg",
  "title": "슬림핏 맘 하이웨이스트 앵클 진",
  "price": 29900,
  "choice": true,
  "new": true,
  "size": [
    "S",
    "M",
    "L"
  ]
}
```

아래 명령어로 실행해보자 !

```zsh
yarn json-server --watch db.json --port 5000
```

그럼 다음과 같이 포트번호를 통해 내가 만든 db.json을 볼 수 있다. 한번 API 테스트를 진행해보겠다.

<img src="/assets/images/img/Gitblog_img/2024/04/03_27_json-server_01.png"

