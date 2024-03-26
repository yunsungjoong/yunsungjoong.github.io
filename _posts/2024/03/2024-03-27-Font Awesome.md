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

```javascript

import React from 'react';
import { FontAwesomeIcon } from '@fortawesome/react-fontawesome';
import { faCoffee } from '@fortawesome/free-solid-svg-icons';

const Navbar = () => {
    return (
        <div>
            <div><FontAwesomeIcon icon={faCoffee}/></div>
        </div>
    );
};

export default Navbar;
```




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

## 2. Destructuring 

```javascript

let person = {
	name: "sungjoongYun",
  age: 31
}

let name = person.name
let age = person["age"]
console.log(name,age) // 결과값 : 일반적인 방법의 예시
```

```javascript

let person = {
	name: "sungjoongYun",
  age: 31
}

let name = person.name
let age = person["age"]
let {name,age} = person // 중괄호 사용!
console.log(name,age)
//결과값 : 'sungjoongYun',31

```


---

## 가장 많이 사용되는 문법

```javascript
let array = [1, 2, 3, 4]
let [a, b] = array

console.log(a,b)
```

<br />
## 3.Spread(확산)

```javascript
let person = {name: "sungjoongYun", age:31}
let person2 = {...person} // 객체를 복사함
console.log(person2)
// 결과값 {name: "sungjoong.yun", age:12}
```

```javascript
let person = {name:"sungjoongYun",age:31}
let person2 = {...person}
let person3 = person
console.log(person2)	// 결과값 : {name:"sungjoongYun",age:31}
console.log(person3)	// 결과값 : {name:"sungjoongYun",age:31}

// 두개의 값이 같아보이지만 복사 방법이 다름
// let person3 = person 이부분은 객체의 주소값만 복사
// 즉, 객체는 하나이고 그 객체를 참조하는 변수가 두개!
// ...person 부분은 실제로 객체를 하나 더 생성하는 것!
```

<br />

```javascript
let person = {name:"sungjoongYun",age:31}
let person2 = {...person,address:'성남'}
let person3 = person
console.log(person2)	// 결과값 : {name:"sungjoongYun",age:31, address:'성남'} //기존값에 추가도 가능함
console.log(person3)	// 결과값 : {name:'sungjoongYun',age: 31}
```

```javascript
let person = {name: "sungjoongYun", age:31}
let person2 = {...person, name: "냉면"}
let person3 = person 
console.log(person2) // 결과값 : {name: '냉면', age:12} // 기존값 수정 가능
console.log(person3) // 결과값 : {name: 'sungjoongYun', age:31} // 기존값 수정 가능
```

<br />

---

## Array(배열)
```javascript
let a = [1, 2]
let b = [...a, 3]

console.log(b)
// 결과값 : [1, 2, 3]
```

```javascript
let a = [1, 2]
let b = [...a, 3]
let c = [...a, ...b]

console.log(c)
// 결과값 : [1, 2, 1, 2, 3]
```

## 삼항연산자
```javascript
let person = {name: "sungjoongYun", age: 31}

if(person){
  console.log(person.name)
} else {
  console.log("there this no person")
}

// 결과값 : sungjoongYun


// 삼항연산자
console.log(person ? person.name : "there this no person")
```

이 글은 코딩알려주는 누나님의 온라인 강의 통하여 작성한 글입니다.
