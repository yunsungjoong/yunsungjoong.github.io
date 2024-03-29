---
layout: post
title: "[JavaScript] JavaScript 란? "
tags: [Javascript]
categories: [JavaScript]
banner:
  image: "/assets/images/banners/22/05/js.png "
  opacity: 0.618
  background: "#000"
  height: "100vh"
  min_height: "38vh"
  heading_style: "font-size: 3.25em; font-weight: bold; text-decoration: underline"
  subheading_style: "color: gold"
---

## JavaScript 란 ?

HTML과 CSS로 만들어진 웹 페이지에 생동감을 불어넣기 위해 만들어진 객체기반
프로그래밍 언어로 C, C++ 처럼 컴파일 없이 한줄 한줄씩 해석하며 명령어를 실행하는 인터프리터 언어이다.
HTML의 특정 요소를 선택해 다양한 이벤트 ( 마우스 클릭 , 키보드 입력 등)에 따라 어떤 동작을 하도록 기능을 넣을 수 있다.

## JavaScript 사용방법

### 1. 내부 스크립트

자바스크립트 코드는 `<script>` 태그를 HTML 문서안에 넣어서 사용 가능하다.
HTML문서의 어느위치에서도 사용 가능한데 보통 HTML문서가 전부 로드 되고 나서
`<body>` 아래에 사용한다.

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

</body>
<script>
자바 스크립트 코드
</script>
</html>
```

### 2. 외부 스크립트

자바스크립트 파일을 HTML과 별개인 .js 확장자의 파일로 저장한 후 불러올 수 있다. 외부
자바스크립트를 사용하려면 `<script>`의 src 속성으로 HTML 문서 위치의 기준 파일 경로를
입력해주면 된다.

```
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

</body>
<script src="./index.js"></script>
</html>
```

### 변수 (let | const)

자바스크립트에는 변수형(int , double , string) 이 존재하지 않는다. var 이라는 가변형 변수만 존재해
초기화 할때 형태에 따라서 알아서 할당된다.

```
var i;
var x = 123;
var y = "123";
var z = false;
var w = null;
```

var의 유효 범위는 함수 내부로 조건이나 반복문 안에초기화 된 경우라도 함수 내부 블록이라면
어디서나 호출할 수 있다. 최신 자바스크립트에선 `let` 이라는 가변형 블럭 지역 변수와 `const`라는 불편형
지역 변수가 추가되었다.

```
let a = 123;
a = "123";

const b = false;
y = null // error
```

## 2.연산자

+, - , \* , / , % 등으 ㅣ기본 연산은 물론 ++ , -- 와 같은 증감 연산자도 사용할 수 있다.

```
a = a + 1 (x)
a += 1 (o)
```

자바스크립트에서 `a = a + 1 ` 과 같은 표현은 쓰지 말라고 되어있다. 무조건 할당 연산자를
사용하라고 한다. 가독성을 위함일까 ? 또한 자바스크립트는 자바와 마찬가지로 스트링 컨케트네이션이 되므로
문자열을 덧셈기호로 간단히 붙힐 수 있다.

```
var s = "String1" + "String2"l
console.log(s)
```

```
String1String2
```

## 3.조건문

```
a == b
a != b
a == b && a == c
a == b || a == c
a > b
```

```
if (a > b) {
  console.log("a is more than b.")
} else if ( a == b ) {
  console.log("a is the same as b.")
} else {
  console.log("a is less than b.")
}
```

## 4.함수

선언과 호출은 아래와 같다.

```
function notify(message) {
  console.log('# NOTIFICATION : ' + message);
}

notify('say something');
```

```
# NOTIFITAION : say something
```

자바스크립트의 함수는 굉장히 다채롭게 선언할 수 있다. 가령 아래와 같이 함수를 생성할 수도 있다.

```
var notify = function (message) {
  console.log('# NOTIFICATION : ' + message);
}

notify('say something');
```

최근 자바스크립트 문법에서 화살표 함수라는 개념이 도입되어 아래와 같이 생성할 수 도 있다.

```
var notify = () => {
  console.log('# NOTIFICATION : ' + message);
}

notify('say something');
```

위 처럼 여러가지 형식을 가지고 있는데 정해진 규칙은 없으므로 자신이 원하는 방식으로 일관성 있게 작성하면 된다.
필자의 경우에는 함수 내부의 함수나 익명 함수는 화살표 함수로 그 외에는 함수 선언식으로 사용된다.
다만 화살표 함수의 경우 최신 문법이므로 구형 브라우저에선 인식되지 않는 다는점을 참고하자

값을 반환하는 함수는 아래와 같이 작성한다.

```
function add(value1, value2) {
  return value1 + value2;
}

var a = 10;
var b = 30;
console.log(add(a,b));
```

```
30
```

화살표 함수로는 아래와 같이 표현

```
var add = (value1, value2) => value1 _ value2;

console.log(add(10,20));
```

```
30
```

화살표 함수의 경우 중괄호 생략할 수 있으며 , 중괄호를 생략할 경우 화살표 다음에 다음에 선언된 식이 'return`
되는 것으로 간주한다.

## 5.배열

변수의 값이 연속적으로 나열된 형식

### 배열의 선언

```
var arr = new Array();
var arr = [];
```

### 배열에 값삽입

#### 초기화시 값 삽입

```
var careers = [
  "Warrior",
  "Archer",
  "Wizard"
];
```

#### 인덱스를 이용하여 삽입

```
var careers = [];
careers[0] = "warrior";
careers[1] = "archer";
crreers[2] = "Wizard";
```

#### `push` 메서드를 사용해 삽입

```
var careers = [];
careers.push("Warrior);
careers.push("Archer");
careers.push(:wizard);
```

### 배열과 관련된 메소드

```
var careers = ["Warrior", "Archer", "Wizard"];
console.log("total careers : " + careers.length);
```

```
total careers : 3
```

`length`는 메서드가 아니다. 자바스크립트에서 `Array`는 하나의 객체이며 `length`는 `Array`가 가진 멤버 변수다.
배열의 길이가 필요할 때마다 길이를 읽어오는 것 보단 O(N) 길이를 가지고 있는게 O(1) 효율적일것이다.

```
var careers = ["Warrior", "Archer", "Wizard"];
console.log("careers : " + careers.join(", "));
```

```
careers : Warrior, Archer, Wizard
```

`join`은 배열을 붙여 하나의 문자열로 만들어 준다.

```
var careers = ["Warrior", "Archer", "wizard"];
console.log("careers : " + careers.reverse().join(','));
```

```
careers: Wizerd , Archer, Warrior
```

`reverse`는 배열을 반대로 뒤집는 역할을 한다.

```
var careers = ["Warrior", "Archer", "Wizard"];
console.log("careers : " + careers.sort().join(', '));
```

```
careers : Archer, Warrior, Wizard
```

`sort`는 배열을 정리한다. 현재는 알파뱃 순서대로 정렬되고 있다. `sort에 함수를 전달하면 자신이 원하는
방식대로 정렬할 수 있다.

```
var careers = ["Warrior", "Archer", "Wizard"];
var careersOnDlc = ["Assassin", "Samurai"]
console.log("careers : " + careers.concat(careersOndlc).join(', '));
```

```
careers : Warrior, Archer, Wizard, Assassin, Samurai
```

`concat`은 두 배열을 합쳐주는 역할을 한다.

```
var careers = ["Warrior", "Archer", "Wizard"];

var x = careers.push("Devill", "Outlaw");
console.log("total careers after push : " + x);

var y = careers.pop();
console.log(pop career :: " + y);
```

```
total careers after push : 5
pop careers : Outlaw
```

`push`와 `pop`은 자료구조 `Stack`에서 다뤄지며 여기서도 동일한 기능을 수행한다. push는 맨 뒤에 요소를
삽입 `pop`은 맨 뒤 요소를 꺼내느 것이다. 주로 팬케이크에 비유되곤 한다.

`push`의 `return type`은 `push` 후 배열의 길이이고 `pop`의 `return type`은 꺼내진 개체다.

```
var careers = ["Warrior", "Archer", "Wizard"];

var x = careers.shift();
console.log("shift career : " + x);

var y = careers.unshift("Knight")
console.log("total careers after unshift : " + y)
```

```
shift career : Warrior
total careers after unshift : 3
```

`shift`는 맨 앞의 요소를 빼는 기능을 , unshift는 맨 앞에 요소를 삽입하는 기능을 한다.

## 6.오브젝트(Object)

구조체(struct) 처럼 내부에 여러 변수를 가질 수 있고 클래쓰(class)처럼 내부에 메소드를 포함하고 있는 형식이다.
JSON이라고 많이 알려진 형식이다.

### 오브젝트의 선언

```
var obj = new Object();
var obj = {};
```

### 변수를 가진 오브젝트

hp와 mp를 가진 player를 생성해보자

```
var player = {};
player.hp = 100;
player.mp = 300;

var player = {
  hp: 100,
  mp: 300
};
```

### 메소드를 가진 오브젝트

플레이어가 후려맞는(?) 기능을 넣어보자

```
var player = {
  hp: 100,
  mp: 300,
  hit: function (damage) {
    this.hp -= damage;
    console.log('player hit damage : ' + damage);
    return this.isDie();
  },
  isDie: function() {
    if (this.hp <= 0) {
      console.log('player is die...');
      return true:
    }
    return false;
  }
};

player.hit(150);
console.log('player left hp : ' + player.hp);
```

```
player hit damage : 150
player is die...
player left hp : -50
```

### 오브젝트 할당

위는 플레이어 객체가 선언됨과 동시에 사용되고 있다. 만일 클래스 혹은 구조체처럼 단지 구조만 선언하고 싶은
경우에는 어떻게 표현할 수 있을까? 오브젝트를 함수로 선언하면 된다.

```
var Player = function(name) {
  var name = name;
  var hp = 100;
  var mp = 300;

  return {
    hit: function (damage) {
      hp -= damage;
      console.log(name + ' hit damage : ' + damage);
      return this.isDie();
    },
    isDie: function () {
      if (hp <= 0) {
        console.log(name + ' is die...');
        return true;
      }
      return false;
    }
  }
}

var medic = new Player('medic');
medic.hit(50);
// medic hit damage : 50


var fireBet = new Player('fireBet');
fireBet.hit(100);
// fireBet hit damage : 100
// fireBet is die ...
```

위는 클로저라는 개념을 응용한 방식인데 위와 같이 선언하면 하나의 객체를 여러 변수에서 할당받아 사용할 수 있다.
다만 이 경우 같은 기능을 하는 함수가 변수마다 새로 할당되는 문제가 발생한다. 이럴때는
`prototype` 을 사용하면 객체끼리 공유하는 함수를 만들 수 있다.

```
var Player = function(name) {
    this.name = name;
    this.hp = 100;
    this.mp = 300;
}

Player.prototype.hit = function (damage) {
    this.hp -= damage;
    console.log(this.name + ' hit damage : ' + damage);
    return this.isDie();
}

Player.prototype.isDie = function () {
    if (this.hp <= 0) {
        console.log(this.name + ' is die...');
        return true;
    }
    return false;
}

var medic = new Player('medic');
medic.hit(50);
// medic hit damage : 50

var fireBet = new Player('fireBet');
fireBet.hit(100);
// fireBet hit damage : 100
// fireBet is die...
```

다만 위 코드에선 프로그래머 혹은 사용자가 `medic.hp` 변수를 접근이 가능하다 .

```
console.log(medic.hp)
// 50
```

그럼 클로저는 왜 사용할까? 사실상 `hp`는 직접적으로 변경 되어서는 안되는 은닉이 필요한 변수이다.
클로저를 응용한 방식에서는 2개의 함수만 반환했기에 `hp` 변수에 접근할 방법이 없다.

## 7. 반복문

반복문이 이렇게 아래에 나오는 이유는 위에 얻은 개념으로 반복문을 더욱 효율적으로 응용할 수 있기 때문이다.
아래 가장 기본적으로 사용되는 방식의 반복문이다.

```
// for 문
for (var i=0; i<5; i++) {
  console.log(i);
}
```

```
// while 문
var i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

```
0
1
2
3
4
```

### for(변수 in 오브젝트 또는 배열)

```
var arr = [10, 20, 30, 40, 50];

for (var i in arr) {
  console.log(i);
}
```

```
0
1
2
3
4
```

배열의 경우 배열의 인덱스가 `i`에 할당되어 반복한다.

```
var obj = {
  a: 1,
  b: 2,
};

for (var key in obj) {
  console.log(key + ' : ' + obj[key]);
}
```

```
a : 1
b : 2
```

오브젝트의 경우 키가 `key`에 할당되어 반복한다.

### for (변수 of 배열)

```
var arr = [10, 20, 30, 40, 50];

for(var i of arr) {
  console.log(i);
}
```

`of`의 경우에는 배열 값이 `i`에 할당되어 반복이 진행된다. 혹은 `forEach`나 `map`을 이용하여 같은 작업을
수행할 수 있다.

```
var arr = [10, 20, 30, 40, 50];

arr.forEach((value, idx) => {
  console.log(idx, value);
});

arr.map((value, idx) => {
  console.log(idx, value);
});
```

둘다 똑같이 아래의 결과를 출력한다.

속도는 `forEach`가 빠르다고 알려져 있다. `map`은 함수형 프로그래밍에 사용되는 개념으로 `forEach`와 달리
새로운 객체를 반환한다는 차이가 있다.

## 8.문자열

문자열은 가장 기본적인 구조인데 이렇게 뒤에 있는 이유는 알아둬야 할 함수가 생각보다 많아서다.
그 중에서도 중요한 것만 기록할 예정이다.

```
var welcome = "ONDE Planet is the most peaceful space in the universe";

console.log(welcome.charAt(0));
// charAt(n) : n번째 문자를 출력한다.  결과는 0

console.log(welcome.charCodeAt(0));
// charCodeAt(n) : n번째 문자의 유니코드를 출력한다. 결과는 79

console.log(welcome.indexOf("x"));
// indexOf("?") : ? 라는 글자가 있다면 글자의 인덱스를, 없다면 false(-1)을 출력한다. 결과는 -1

console.log(welcome.includes("space"));
// includes("?") : ? 라는 글자가 있다면 true(0), 없다면 false(01)을 출력한다. 결과는 0

console.log(welcome.replace("peaceful", "nasty"));
// replace("a", "b") : a를 b로 교체한다. 결과는 ONDE Planet is the most nasty space in the universe.

console.log(welcome.search("universe"));
// search(?") : ? 라는 글자를 검색하여 첫 문자의 시작 지점을 알려준다. 결과는 46

console.log(welcome.slice(0,4));
// slice(n, n') : n~n'-1 까지의 문자를 가져온다. 결과는 ONDE

console.log(welcome.split(" "));
// split("?") : ? 라는 문자를 기준으로 문자열을 분리한다. 결과는 ONDE,Planet,is,the,most,peaceful...

console.log(welcome.trim());
// trim() : 앞, 뒤의 공백을 제거하는 역할을 한다. 이 값에서는 공백이 없으므로 결과가 본래의 문자열과 동일하다.

console.log(welcome.length);
// length : 문자열의 길이를 반환한다. 결과 55
```

### 더 알아야할 내용들

`relace`의 경우에는 처음 발견된 문장만 변경하는데 만일 다수의 문자을 변경하고 싶은 경우엔 어떻게 할 수 있을까?
가령 `replaceAll`처럼 말이다. 바로 정규표현식을 사용하면 되는데 여기서 자세한 내용을 다루진
않는다. 대략 아래와 같은 모양이다.

```
console.log(welcome.replace(/ gi, "-"));
// 모든 공백이 -로 바뀐다.
```

`slice`에는 음수를 넣을 수 있다. 음수를 선택하면 뒤에부터 가져오므로 상당히 유용한 기능이며,
배열에도 사용할 수 있다.

```
console.log(welcome.slice(-3));
// 맨 뒤에 3글자만 가져온다.
```

## 9.수학연산

Math라는 기능을 이용해 사용할 수 있는 연산들이다.

```
Math.abs(-3);
// math.ads(n) : n을 절대값으로 바꾼다.

Math.ceil(3.1);
// Math.ceil(n) : n값을 올림한다.

Math.floor(3.9);
// Math.floor(n) : n값을 내림한다.

Math.round(3.5);
// Math.round(n) : n값을 반올림한다.

var a = Math.random();
// Math.random() : 난수를 생성한다.

var b = Math.random()*10+10;
// Math.random()*x+y : y~x+y 범위에서 난수가 생성된다.

var c = Math.floot(Math.random() * (max - min)) + min;
// min 부터 max - 1 까지 범위의 난수

```

## 10.형변환

```
// Number -> String
var num = 2018;
var str = String(num); // "2018"
var str = num.toString(); // "2018"

// String -> Num
var str = "2018.08";
var mInt = Number(str); // 2018
var mInt = parseInt(str); // 2018
var mfloat = parseFloat(str); // 2018.08

// Object -> String
var user = {
  name: '윤',
  age: 24,
};
console.log(user); // { name: '윤' , age : 29}

var strUser = JSON.stringify(user); // 문자열 JSON
console.log(strUser); // "{\"name\":\"윤\",\"age\"29}"

var strUserToObject = JSON.parse(strUser);
// JSON 형식의 문자열이면 parse를 이용해서 Object로 변환할 수 있음
```

## 11.전개구문

전개구문은 이름 그대로 배열이나 객체를 전개(내용을 전진시켜 퍼 나감) 시킨다고 생각하면
이해하기 쉬운 것 같다.

우선 아래는 배열에 대한 전개구문이다.

```
const number = [1, 2, 3, 4, 5];
console.log([...numbers, 6, ,7 , 8, 9, 10]);
```

```
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
```

위와 같이 확장의 개념으로 사용할 수 있고

```
const numbers = [1, 2, 3, 4, 5];
const copyNumbers = [...numbers];
```

복사의 개념으로도 사용할 수 있다. `numbers`를 바로 대입하는 것과는 달리 위 코드는
각각의 값이 복사된 전혀 새로운 객체가 할당된다. 깊은 복사가 이뤄지는 셈이다.
이제 이름이 착 달라붙지 않는가? 말 그대로 자신의 객체들을 전개시키는 문법이다. 배열에서는
각각의 객체를 전개시키지만 객체를 전개시키지만 객체에서는 키와 값을 전개시킨다.

```
const user = {
  name : '윤',
  age : 29,
};
console.log({
  ...user,
  hobby : '게임'
});
```

```
{name : ' 윤', age: 29, hobby: '게임'}
```

위와 같이 키와 값을 그대로 전개시킨다.

```
const user = {
  name : '윤',
  age : 29,
};
console.log({
  age : 99,
  ...user,
});
```

```
{ name : '윤' , age: 29 }
```

위와 같이 작성하면 전개구문에 의해서 `age`의 값이 덮어 써진다는 점을 고려하자, 전개 구문을 사용한 지점에서
해당 객체를 그대로 불러오는 개념으로 이해하면 된다.

## 12.함수형 메서드

자바스크립트에서는 함수형 프로그래밍에 대부분 사용되는 `map` , `fitter`, `reduce` 함수가 제공된다.
이터레이블 객체(배열 등) 에서만 사용가능 한 점 참고하자. 우선 아래와 같은 배열에 대해
각각의 함수의 사용방법을 알아보자

```
const users = {
  {
      name : '윤',
      age : 29,
      hobby : '게임'
  },
  {
      name: '김미소'.
      age : 24,
      hobby : '음악'
  },
  {
      name : '아이유',
      age : 26.
      hobby : '음악'
  },
};
```

### map

`map`은 단순한 반복문이다. 다만 전달한 함수에 맞게 처리된 개체가 담긴 `배열`이 반환된다.
위 데이터에서 이름과 나이로만 구성된 오브젝트로 재구성 한다고 생각해보자.

```
const newUser = users.map(function(user) {
  return {
    name: user.name,
    age: user.age
  };
});
console.log(newUsers);
```

```
[
  { name: '윤' , age : 29},
  { name: '김미소' , age : 24},
  { name: '아이유' , age : 26}
]
```

### filter

필터는 반복을 진행하면서 전달한 함수의 결과가 `true`인 개체의 `배열`을 리턴하는 함수다.
취미가 `음악` 인 사람들만 뽑아보자

```
const newUsers = users.filter(function(user) {
  return user.hobby == '음악'
});
console.log(newUsers);
```

```
[
  { name : '김미소' , age : 24, hobby : '음악' },
  { name : '아이유' , age : 26, hobby : '음악' }
]
```

그럼 이번에는 필터와 맵을 함께 사용해 취미가 음악인 사람의 이름만 출력해보자. 이번에는 위와 다르게
화살표 함수를 이용해 문법을 간소화 시켜보겠다

```
const newUsers = users
  .filter(user => user.hobby == '음악')
  .map(user => user.name);
  console.log(newUsers);
```

```
[ '김미소' , '아이유' ]
```

### reduce

`reduce`는 배열의 개체를 누적으로 처리하기 위해 사용된다. 누적으로 처리할 일이 뭐가 있을까?
예를 들면 합계를 내거나 배열을 오브젝트로 만들거나 , 지금 당장 생각나는 부분은 2가지인듯 하다.
그 외 다양하게 사용될 수 있을 것이다.

우선 `reduce`를 활용해 모든 유저의 나이의 평균을 내보자

```
const userTotalAge = users.reduce((acc, user) => acc += user.age, 0);
console.log(userTotalAge / users.length);
```

```
24.666666666666668
```

`reduce`는 `map`이나 `filter`와 다르게 개체뿐 아니라 누적된 값이 함께 매개변수로 들어온다. 필자는 이
변수를 대부분 acc(accumulate)라고 표현한다. 또한 중요한 점은 함수 다음에 초기값을 넣어준다.
위 코드에서는 `0`. 맨 처음 실행될 때 `acc` 의 값으로 `reduce`에서는 이 초기값을 꼭 설정해야 하는 점을 기억하자

이번에는 각각의 이름을 키로 나이를 값으로 사용하는 오브젝트인 `reduce`를 이용해서 생성해보자.

```
const usersObject = users.reduce((acc, user) => {
  return {
    ...acc,
    [user.name] : user.age
  }
}, {})
console.log(usersObject);
```

```
{ 'yun': 24, '김미소': 24, '아이유': 26}
```

전개구문을 이용해 기존 오브젝트의 키와 값을 살리면서 새로운 키와 값을 추가하는 방식이다.

[참고한 블로그링크 : javascript 기본 문법 정리](https://blex.me/@baealex/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8javascript-%EA%B8%B0%EB%B3%B8-%EB%AC%B8%EB%B2%95-%EC%A0%95%EB%A6%AC "Javascript 문법정리")
