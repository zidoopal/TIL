> <span style="background-color:#B5F9C0">**구조 분해 할당</span>** (비구조화 할당) 이란,<br>
> <span style="background-color:#B5F9C0"> **배열**이나 **객체**의 **속성을 해체**하여 **그 값을 개별 변수에 담을 수 있게 하는 JavaScript 표현식**</span>입니다.
> [출처 : mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
>
> 간편하게 배열과 객체 안의 값을 꺼내 먹어보장 😺

<br/>

## 📌 비구조화할당 전 코드 예시

각 배열/객체 안에 있는 요소들을 꺼내서 사용하려면 배열의 인덱스나 객체의 프로퍼티를 찾아서 매칭시켜줘야 한다.

```javascript
// (1) Array
const arr = [1, 2, 3, 4, 5];

let one = arr[0];
let two = arr[1];
let three = arr[2];

// (2) Object
const obj = {
  one: 1,
  two: 2,
  three: 3,
  four: 4,
  five: 5,
};

let one = obj.one; //	[1]
let two = obj.two; //	[2]
let three = obj.three; //	[3]
```

<br/>

# ✍ 배열 구조 분해

## ✔ 기본 문법

```javascript
const [a, b, c, ...rest] = [1, 2, 3, 4, 5, 6];

console.log(a); //	[1]
console.log(b); //	[2]
console.log(rest); //	[4, 5, 6]
```

# ![](https://velog.velcdn.com/images/doopal2/post/f075c051-abaa-4d7d-8eda-87200d0a2827/image.png)

- 좌항 : **호출 될 변수명 집합** / 우항 : **할당 될 값**
- **같은 인덱스를 가지는 우항의 배열 값들이 할당**됨
- 전개 연산자(`...`) 를 이용하면 매칭된 값 이외의 모든 데이터 값을 할당 할 수 있다.<br>
  ✨ **전개 연산자를 사용하려면 반드시 가장 마지막 요소에 넣어야 함**!!! ✨

## ✔ 임의의 인덱스 값만 가져오기

```javascript
const arr = [1, 2, 3, 4, 5];

const [a, b, , , z] = arr;

console.log(a); //	[1]
console.log(b); //	[2]
console.log(z); //	[5]
```

<br/>

# ✍ 객체 구조 분해

## ✔ 기본 문법

```javascript
const { a, b, c, ...rest } = { a: 1, b: 2, c: 3, d: 4, e: 5, f: 6, g: 7 };

console.log(a); //	1
console.log(b); //	2
console.log(c); //	3
console.log(rest); //	{d: 4, e: 5, f: 6, g: 7}
```

- 좌항 : **호출 될 객체명 집합** / 우항 : **할당 될 값**
- **우항의 key 값이 좌항의 변수명과 매칭**이 됨<br>
  ✨객체의 비구조화 할당은 순서가 아닌, key값을 기준으로 이루어진다✨

## ✔ key이름 대신 다른 변수명 사용하기

원래의 key 값과 다른 변수명으로 사용하는 방법 `key명:바꿀변수명`

```javascript
const {
  a: new_a,
  b: new_b,
  c,
  ...rest
} = { a: 1, b: 2, c: 3, d: 4, e: 5, f: 6, g: 7 };

console.log(new_a); //	1
console.log(new_b); //	2
console.log(a); //	Error: a is not defined
```

<br/>

## 기본 값 지정

만약 지정한 변수 이외에 매칭 할 값이 없다면 `undefined`가 발생한다.<br>
이 때 `undefined`가 아닌 **원하는 기본값으로 출력되도록 지정**해 놓을 수 있다.<br>

```javascript
// 배열 - 기본 값 설정 X
[a, b] = [10];
console.log(a); // 10
console.log(b); // undefined
// 배열 - 기본 값 설정 후
[a, b = 'defalut'] = [10];
console.log(a); // 10
console.log(b); // defalut

// 객체 - 기본 값 설정 X
var { a, b, c } = { a: 0, b: 1 };
console.log(b); // 1
console.log(c); // undefined
// 객체 - 기본 값 설정 후
var { a, b, c = '얄루' } = { a: 0, b: 1 };
console.log(b); // 1
console.log(c); // 얄루
```

<br/>

> 😺 **연습**

```javascript
const 티모 = {
  name: '티모',
  mp: 334,
  skill: '실명다트',
  skillMp: 40,
  crazy: true,
};
>
const 조이 = {
  name: '조이',
  mp: 425,
  skill: '헤롱헤롱쿨쿨방울',
  skillMp: 50,
  crazy: true,
};
>
function game(챔피언) {
  const text = `${챔피언.name}님이 ${챔피언.skill}을(를) 사용하여 MP가
    ${챔피언.mp - 챔피언.skillMp}만큼 사용 되었습니다.`;
  console.log(text);
}
>
game(티모);
```

<br> 
👉 비구조화 할당 이후<br>

```javascript
const 티모 = {
  name: '티모',
  mp: 334,
  skill: '실명다트',
  skillMp: 40,
  crazy: true,
};
>
const 조이 = {
  name: '조이',
  mp: 425,
  skill: '헤롱헤롱쿨쿨방울',
  skillMp: 50,
  crazy: true,
};
>
function game(챔피언) {
  const { name, skill, mp, skillMp } = 챔피언;
  const text = `${name}님이 ${skill}을 사용하여 MP가 ${
    mp - skillMp
  }만큼 사용 되었습니다.`;
  console.log(text);
}
>
game(티모);
```

<br/>

### 📚 참고

---

[사이트]

- [mdn - 구조 분해 할당] (https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

[블로그]

- [[JS] 📚 비구조화(구조분해) 할당 💯 정리] (https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EB%B9%84%EA%B5%AC%EC%A1%B0%ED%99%94%EA%B5%AC%EC%A1%B0%EB%B6%84%ED%95%B4-%ED%95%A0%EB%8B%B9#%EA%B8%B0%EB%B3%B8_%EB%AC%B8%EB%B2%95_-_%EB%B0%B0%EC%97%B4)
