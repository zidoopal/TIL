## ✍ 객체 (Object)
+ 객체 - 속성(property) key: value로 구성
  + key 값에는 문자열 (숫자로 시작 시 / 특수문자나 공백 들어갈 경우 ▶ ''써야함)
  + value 값에는 어떤 자료형이든 가넝

## ✍ 객체 리터럴
+ **객체 리터럴**: ** `{ }` 를 사용하여 만든 객체**
 
## ✍ 객체의 생성
```javascript
// 1) 객체 리터럴
let obj1= {
  name : 'doopal',
  level : 10,
  success : true,
};
console.log(obj1)   // {name: 'doopal', level: 10, success: true}


// 2) 생성자 함수
let obj2 = new Object();

obj2.name = 'doopal';
obj2.level = 20;
obj2.success = true;

console.log(obj2);  // {name: 'doopal', level: 20, success: true}


// 3) Object.create()
// 프로토타입 상속을 통해 객체를 만듬 - 부모인 obj의 프로퍼티인 name을 참조

let obj3 = Object.create(obj2);

obj3.name;   // 'doopal'
```

## ✍ 객체 접근
1. `객체.key `
```javascript
let zdp= {
  name : 'doopal',
  level : 10,
  success : true,
};

zdp.name;      // 'doopal'
zdp.success;   //  true
```
2. `객체['key']`
```javascript
let zdp= {
  name : 'doopal',
  level : 10,
  success : true,
};

zdp['level'];  // 10
```

> **tip 🎈**
같은 역할을 하는데 왜 표기가 다름? == 다른데는 다 이유가 있다. (ex 용도가 달리 쓰이거나)<br>
ex) 
```javascript
const obj = {
  abc : 'ㅎㅇ',
  'a-c' : 'ㅎㅇ2',  // 이렇게 key 이름에 특수문자나 숫자가 들어갈경우 ''로 감싸줘야하고
  '2abc' : 'ㅎㅇ3',
};
>
obj.a-c;     // ''로 감싸줬던 key들은 '객체.key'형태로 접근 ❌, 에러남
obj['a-c'];  // 객체['key'] 형태로 접근 가능 
```
![](https://velog.velcdn.com/images/doopal2/post/501b2d48-2a65-4f55-9c7b-0cd4db7eafef/image.png)


<br/>

***

## ✍ 배열 (Array)
+ **배열 : ✨'순서'✨가 있는 컬렉션을 저장할 때 쓰는 자료구조**
<br>

## ✍ 배열의 생성 / 요소 수정 & 추가
### ✔ (1)
```javascript
// 빈배열 생성
let arr1 = [];

// 선언하면서 바로 []안에 요소 넣기
let arr2 = [0, 2, 4];
console.log(arr2)   // [0, 2, 4]

// 배열의 요소 추가
arr1[0] = 1;
arr1[1] = 2;
arr1[2] = 3;
console.log(arr1);  // [1, 2, 3]

// 배열의 요소 수정
arr1[2] = 5;
console.log(arr1);  // [1, 2, 5]
```

### ✔ (2)
```javascript
// 생성자 함수
let arr3 = new Array();

// 배열의 요소 추가 메서드

// unshift - 배열 앞에 요소 추가하고, 배열의 길이를 반환
// push - 배열 맨 끝에 요소 추가하고, 배열의 길이를 반환

arr3.push('사과');
arr3.push('복숭아');
arr3.unshift('포도');

console.log(arr3);  // ['포도', '사과', '복숭아']


// 배열의 요소 제거 메서드

// shift - 배열 앞에 요소 제거하고, 제거한 요소 반환
// pop - 배열 맨 끝 요소 제거하고, 제거한 요소 반환
arr3.pop();   // '복숭아'
console.log(arr3);   // ['포도', '사과']

arr3.shift();   // '포도'
console.log(arr3);   // ['사과']
```

## ✍ 배열 값 읽기
```javascript
let arr2 = [0, 2, 4];

// 인덱스를 넣어 원소에 접근하여 값 읽기
arr2[0];  //  0
arr2[2];  //  4

// 배열 요소 갯수(길이) 확인
console.log(arr2.length);  // 3

```

***

>**tip 🎈**
+ 배열과 객체의 차이점
  + Array : 자료간 순서가 존재
  + Object : 순서 개념 X

<br/>

### 📚 참고자료
***
[사이트]
+ [모던 JavaScript 튜토리얼 - 객체](https://ko.javascript.info/object)
+ [모던 JavaScript 튜토리얼 - 배열](https://ko.javascript.info/array)

[블로그]
+ [[javascript] 배열(array)보다 객체(object)를 써야하는 경우, 배열을 객체로 바꾸는 방법](https://codingbroker.tistory.com/75)
+ [[javascript] 배열(array)와 객체(object) 개념 및 차이](https://amyhyemi.tistory.com/m/225)