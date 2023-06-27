## ✍ 프로그래밍에서의 함수
+ **함수(function)**: **일정한 동작을 수행하는 코드**
  + 미리 만들어 두고 원할 때 실행하여 정해진 동작을 수행할 수 있게 함
```javascript
// 함수를 만들 때

// (1) function 예약어
function () {}

// (2) 화살표 기호 사용(== 화살표 함수)
() => {};

// 위 두 함수들은 현재 함수명이 없기 때문에 다른 곳에서 사용 X, 이름을 붙여주자. (익명함수)
  // 익명함수는 딱 한번만 사용할 때는 사용 가능, 여러번 반복해서 사용할 경우 이름을 붙여주자.

// 함수 선언문 (function 키워드 뒤에 함수 이름을 넣어주는 방식)
function a () {}

// 함수 표현식 (변수/상수에 대입하는 방식)
const b = function () {};
const c = () => {};  // 화살표 함수
```

> 같은 함수인데 형태가 왜 다를까? 
다른데는 다 이유가 있다..🤔 

<br>

## ✍ 함수의 선언 과 호출
+ 함수의 선언 : 변수와 마찬가지로 **함수를 만드는 행위**도 선언한다(declare)고 표현
+ 함수의 호출 : **만든 함수를 사용하는 행위** (call)
```javascript
// 함수의 선언
function a() {
  console.log('a');
}

// 함수의 호출
a();    // a
```
<br>

## ✍ 함수의 반환
- 함수를 선언 할 때에는 반환값 undefined
- return 사용하여, 함수 호출 시 반환 값 반환해줌.
  - ✔ **return 사용 시, 함수 실행 종료됨.**
```javascript
// 함수 선언 - 반환값 undefined
function doopal(){
	return '두팔';
  	console.log('두팔2');
}

// 함수 호출 - 반환값 return 값
doopal();  // '두팔'

// return '두팔'을 만나 '두팔' 이라는 값을 반환 후 함수가 종료됨.
//  console.log('두팔2') 는 실행되지 못하고 함수 -끗-
```
- return 값을 여러 개 받고 싶다면 배열로 받거나 or 객체 리터럴로 받기
```javascript
(1)
function doop() {
	return 1, 5, 7;   // 이와 같이 return 을 설정 시-
}

doop();   // 7   // 마지막 값인 7 만 반환됨.

(2)
function doop2() {
	return [1, 5, 7];  // return 값을 배열로 설정 시 
}

doop2();   // [1, 5, 7]   // 배열 전체 반환
```

<br/>

## ✍ 화살표 함수 (Arrow function)
화살표 함수를 이용하면 함수를 좀 더 간결하게 표현할 수 있다.
  + but, 단순히 '짧게'쓰기 위한 용도로만 사용되는 것 ❌
### ✔ 코드 형태 
 +  (param) => {함수 코드};
 + function(){} 의 축약 형태이지만 고려 할 사항 有 
  (함수안에서 this가 참조하는 Object가 다름)
<br>
### ✔ 함수 블록 {} 사용
+ **함수 블록**`{}`과 **return** 작성 생략
```javascript
let func = (a, b) => {
	return a + b;
};
// => 화살표 다음에 바로 { return ~ } 올 경우, 함수블록과 return 생략 가능
let func = (a, b) => a + b;
```
+ **함수 블록**`{}`만 작성
```javascript
let func2 = (a, b) => {};
console.log(func2(1,2));  // undefined

// 함수 블록{} 만 작성하면 undefined 반환 
// == return을 작성하지 않은 것과 같음 (화살표 함수라서가 아니라 JS 문법)
```
+ **{key: value}** 반환
```javascript
const func3 = param => ({name: param});
const result = func3('doopal');
for (const key in result) {
  console.log(key + ': ' + result[key]);
};
// name: doopal
```
<br>

### ✔ 파라미터 (param) 사용
- 인수가 하나밖에 없을 때 (param) 소괄호 생략 가능 
```javascript
// 인수 하나라 (param)에서 괄호 생략
const func3 = param => ({name: param});  
```

- 인수가 하나도 없을 땐 () 비워놓으면 됨. but, 소괄호 생략은 ❌
```javascript
const func4 = () => {}
```
<br>

## ✍ 일반함수와 화살표 함수의 차이
+ `this`를 가지지 않는다.
+ `arguments`를 지원하지 않는다.
+ `new`와 함께 호출할 수 없다.
  + `this`가 없기 때문에 화살표 함수는 생성자 함수로 사용할 수 없다.


> **tip 🎈**
화살표 함수 vs. 일반함수 `.bind(this)`를 사용해서 호출하는 것 사이에는 미묘한 차이가 있다
>
+ .bind(this)는 함수의 '한정된 버전(bound version)'을 만듭니다.
+ 화살표 함수는 어떤 것도 바인딩시키지 않는다.<br>
화살표 함수엔 단지 this가 없을 뿐, 화살표 함수에서 this를 사용하면 일반 변수 서칭과 마찬가지로<br>
this의 값을 외부 렉시컬 환경에서 찾는다

<br/>

### 📚 참고자료
***
[사이트]
+ [모던 JavaScript 튜토리얼 - 화살표 함수 기본](https://ko.javascript.info/arrow-functions-basics)
+ [모던 JavaScript 튜토리얼 - 화살표 함수 다시 살펴보기](https://ko.javascript.info/arrow-functions)

[블로그]
+ []()
+ []()