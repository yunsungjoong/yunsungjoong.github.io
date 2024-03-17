---
layout: post
title: "[React] 날씨앱-만들기 OpenWeather-API "
tags: [React, JavaScript]
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

# 완성본 



## Teck Stack

`React` , `JS` , `css` , `Weather open API`

## 🔍 날씨 데이터 가져오기 

```javascript
const getCurrentLocation = () => {
    navigator.geolocation.getCurrentPosition(( position ) => {
      let lat = position.coords.latitude; // 위도
      let lon = position.coords.longitude; // 경도
      
      console.log('현재위치', lat, lon);
  });
};
```
<img src="/assets/images/img/Gitblog_img/2024_02_20_01/Counter.png">


---


## 1. Object Shorthand AssignMent

```javascript
// 키와 키값에 들어가는 변수의 이름이 같을때만 사용
let name = "sungjoongYun"
let age = 31

let person = {
	name,
  age
}
console.log(person)
// 결과값 : {name: 'sungjoongYun',age: 31}
```

<br />
---


이 글은 코딩알려주는 누나님의 온라인 강의 통하여 작성한 글입니다.
