# 📌 spread 연산자

자바스크립트 spread 연산자 **`...`** 를 사용하면 <br>
기존 배열이나 객체의 전체 또는 일부를 다른 배열이나 객체로 빠르게 복사할 수 있다<br>
<br/>

## ✔ 배열에서의 spread 연산자

```javascript
const noTopingCookies = ['촉촉쿠키', '안촉촉쿠키'];
const topingCookies = ['초코쿠키', '치즈쿠키', '블루베리쿠키', '캬라멜쿠키'];

const allCookies = [...noTopingCookies, ...topingCookies];
console.log(allCookies);
// ["촉촉쿠키", "안촉촉쿠키", "초코쿠키", "치즈쿠키", "블루베리쿠키", "캬라멜쿠키"]

// ㄷㄷ 쩐다
```

> `.concat()` 메서드를 사용해도 합칠 수 있음!<br>
> **but `...` 연산자 사용 시, 요소 중간에도 문자를 자유롭게 넣을 수 있음**<br>

```javascript
const allCookies2 = noTopingCookies.concat(topingCookies);
console.log(allCookies2);
//["촉촉쿠키", "안촉촉쿠키", "초코쿠키", "치즈쿠키", "블루베리쿠키", "캬라멜쿠키"]
>
const allCookies = [...noTopingCookies, "함정쿠키", ...topingCookies];
console.log(allCookies);
// ["촉촉쿠키", "안촉촉쿠키", "함정쿠키", "초코쿠키", "치즈쿠키", "블루베리쿠키", "캬라멜쿠키"]
```

<br/>

## ✔ 객체에서의 spread 연산자

```javascript
const cookie = {
  base: 'cookie',
  madeIn: 'Korea',
};

const chocoCookie = {
  base: 'cookie',
  madeIn: 'Korea',
  topping: 'choco',
};

const cheeseCookie = {
  base: 'cookie',
  madeIn: 'Korea',
  topping: 'cheese',
};

const strawberryCookie = {
  base: 'cookie',
  madeIn: 'Korea',
  topping: 'strawberry',
};
```

위 코드에서 base, madeIn, topping등의 프로퍼티가 중복된다. <br>
이럴 때 `...` 연산자를 통해서 깔끔하게 복사 / 병합할 수 있다 :) <br>

```javascript
const cookie = {
  base: 'cookie',
  madeIn: 'Korea',
};

const chocoCookie = {
  ...cookie,
  topping: 'choco',
};

const cheeseCookie = {
  ...cookie,
  topping: 'cheese',
};

const strawberryCookie = {
  ...cookie,
  topping: 'strawberry',
};

console.log(chocoCookie);
console.log(cheeseCookie);
console.log(strawberryCookie);
```

<br/>

### 📚 참고

---

[강의]

- [인프런 - 한입 크기로 잘라 먹는 리액트(React.js) : 기초부터 실전까지] https://www.inflearn.com/course/%ED%95%9C%EC%9E%85-%EB%A6%AC%EC%95%A1%ED%8A%B8/dashboard
