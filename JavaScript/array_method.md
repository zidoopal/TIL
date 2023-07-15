# 배열내장함수

## [`forEach()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)

- 주어진 callback 함수를 배열의 모든 요소에 한번씩 순회할 수 있게 해주는 내장 함수
  - 원본 배열의 값을 바꾸지도 않고, 값을 return 하지도 않음

```javascript
// syntax
arr.forEach(callback(currentvalue[, index[, array]])[, thisArg])

// example
const arr = [1, 2, 3, 4, 5]
function print(num, i) {
	console.log(`${i}위치의 요소 : ${num}`);
}

arr.forEach(print)

// 0위치의 요소 : 1
// 1위치의 요소 : 2
// 2위치의 요소 : 3
// 3위치의 요소 : 4
// 4위치의 요소 : 5
```

<br>

## [`map()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/map)

- callback 함수를 배열의 요소에 대해 한번씩 실행해서 그 함수의 반환값으로 새로운 배열을 만든다.
  - `forEach()` 와 비슷한 로직을 가졌으나, 새로운 배열을 '반환'한다는 차이점이 있다.
  - **만약 어떤 함수를 적용해서 처리한 결과를 저장해야 한다면 `map()` 함수를 사용하잣 😺**

```javascript
// syntax
    arr.map(callback(currentValue[, index[, array]])[, thisArg])
```

<br>

## [`includes()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)

- 배열에 주어진 요소가 포함되는지 여부에 따라서 `true` || `false` 반환
- `===` 연산자로 비교하는것과 비슷하다고 생각하면 good

```javascript
// syntax
includes('element');

// inclueds() 사용
console.log(arr.includes(num)); // true
```

<br>

## [`indexOf()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf)

- 배열에서 지정된 요소를 찾을 수 있는 **첫 번째 '인덱스'를 반환**하고 **존재하지 않으면 -1을 반환**

```javascript
// syntax
arr.indexOf(searchElement[, fromIndex])
```

<br>

## [`find()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/find) : 주어진 판별 함수를 만족하는 **첫 번째 요소의 값을 반환**

- 만족하는 요소 없으면 `undefined` return

<br>

## `findIndex()`

- 주어진 판별 함수를 만족하는 배열의 **첫 번째 요소에 대한 '인덱스'를 반환**

```javascript
// syntax
 arr.find(callback[, thisArg])
 arr.findIndex(callback(element[, index[, array]])[, thisArg])

// example
const arr = [1, 2, 3, 4, 5];

console.log(arr.find((num) => num > 3));  // 4  (요소 반환)
console.log(arr.findIndex((num) => num > 3));  // 3  (요소의 인덱스 반환)
```

<br>

## [`fill()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)

- 배열을 지정한 값으로 채워주는 메서드.
  - **'원본 배열 그 자체를 수정'한다.**

```javascript
arr.fill(value[, star[, end]])
// value 채울 값
// start 시작 인덱스 (기본 값 0)
// end 끝 인덱스 (주어진 인덱스 이 전까지) (기본 값 this.length)
```

<br>

## [`slice()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/slice)

- 배열의 begin 부터 end 이전 까지(end 미포함)에 대한 얕은 복사본을 새로운 배열 객체로 반환함
  - **원본 배열은 바뀌지 않는다.**

```javascript
// syntax
arr.slice([begin(i)[, end(i)]])

// exapmle
const arr = [1, 2, 3, 4, 5];

console.log(arr.slice(2));       //  [3, 4, 5]
console.log(arr.slice(1, 4));    //  [2, 3, 4]
console.log(arr.slice(-1));      //  [5]
console.log(arr.slice());        //  [1, 2, 3, 4, 5]
```

<br>

## [`splice()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/splice)

- 배열의 기존 요소를 삭제 또는 교체하거나 새 요소를 추가하여 원본 배열의 내용을 변경하는 메서드

```javascript
// syntax
array.splice(start(i)[, deleteCount(제거 할 요소의 수)[, item1[, item2[, ...]]]])

// exapmle
const arr = [1, 2, 3, 4, 5];

console.log(arr.splice(2));       //  [1, 2]
console.log(arr.splice(2, 1));      //  [1, 2, 4, 5]
console.log(arr.splice(1, 0, 0));      //  [1, 0, 2, 3, 4, 5]
```

<br>

## [`concat()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/concat)

- **인자로 주어진 배열이나 값들을 기존 배열에 합쳐서 새 배열을 반환하는 메서드**

```javascript
// syntax
  array.concat([value1[, value2[, ...[, valueN]]]])

// exapmle
const arr1 = [1, 2, 3];
const arr2 = [4, 5, 6];

console.log(arr1.concat(arr2));  // [1, 2, 3, 4, 5, 6]
```

<br>

## [`filter()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/filter)

- **주어진 함수의 결괏값이 참인 요소만 모아 새로운 배열로 반환해주는 메서드**
  - 특정한 요소를 만족하는 요소들을 배열로 반환받고싶다~~!! 할때 사용하자 🤪

```javascript
// syntax
arr.filter(callback(element[, index[, array]])[, thisArg])

// exapmle
const yummy = ["potato", "tomato", "pizza", "mango", "ham"];
console.log(yummy.filter((yum) => yum.length >= 6));
```

<br>

## [`sort()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/sort)

- **배열의 요소를 적절한 위치에 정렬한 후 그 배열을 반환해주는 메서드**
  - **기본 정렬 순서는 문자열의 유니코드 코드 포인트값에 따라 정렬된다.**
  - **'원본 배열 그 자체를 수정'한다.**

```javascript
// syntax
arr.sort([compareFunction]);

// exapmle
let chars = ['나', '다', '가'];
chars.sort();
console.log(chars); // ["가", "나", "다"]

let nums = [7, 0, 11, 8, 5];
nums.sort();
console.log(nums); // [0, 11, 5, 7, 8]

// 😵 문자열 기준(유니코드 코드 포인트값)으로 정렬되니까 숫자는 이렇게 정렬되는구나!
// 숫자도 정렬 시킬 수 있는 함수를 만들어서 sort()에 인수로 넣어주장

let nums = [7, 0, 11, 8, 5];

function doopal(x, y) {
  return x - y;
}
// ↓ ↓ 화살표 함수로 변경
nums.sort((x, y) => x - y);

console.log(nums); //  [0, 5, 7, 8, 11]
```

> 😺 숫자 정렬 함수 로직

```javascript
nums.sort((x, y) => {
  console.log(x, y);
  // 0 7	 // 0 과 7 중 0이 더 작으니까 배열 앞으로	👉  [0, 7, 11, 8, 5];
  // 11 0	 // 0 과 11 중 0이 더 작음  이미 앞에 있으니까 위치 그대로  👉  [0, 7, 11, 8, 5];
  // 11 7	 // 11 과 7 중 7이 더 작음  이미 앞에 있음, 그대로 있어랑	👉  [0, 7, 11, 8, 5];
  // 8 7	 // 8 과 7 중 7이 더 작음  이미 앞에 있음, 그대로 있어랑	👉  [0, 7, 11, 8, 5];
  // 8 11	 // 8 과 11 중 8이 더 작음, 내 앞으로오셈	👉  [0, 7, 8, 11, 5];
  // 5 8	 // 5 와 8 중 5가 더 작음, 내 앞으로오셈	👉  [0, 7, 5, 8, 11];
  // 5 7	 // 5 와 7 중 5가 더 작음, 내 앞으로오셈	👉  [0, 5, 7, 8, 11];
  // 5 0 	 // 5 와 0 중 0이 더 작음 다 끝났셈	👉  [0, 5, 7, 8, 11];
  return x - y;
});
```

<br>

## [`join()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/join)

- **배열의 모든 요소들을 합쳐서 문자열로 반환해주는 메서드**

```javascript
// syntax
arr.join([separator(구분자)]);

// exapmle
const arr = ['두팔', '님이', '로그인', '하셨습니다'];
console.log(arr.join()); //  두팔,님이,로그인,하셨습니다
console.log(arr.join('')); //  두팔님이로그인하셨습니다
console.log(arr.join(' ')); //  두팔 님이 로그인 하셨습니다
```

<br>

## [`reduce()`](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)

- **배열의 각 요소에 대해 주어진 리듀서 (reducer) 함수를 실행**하고, **하나의 결과값을 반환**한다.
  - 리듀서 함수는 네 개의 인자를 가진다
    - 누산기 (acc)
    - 현재 값 (cur)
    - 현재 인덱스 (idx) [opt]
    - 원본 배열 (src) [opt]

```javascript
// syntax
arr.reduce(callback[, initialValue])

// exapmle
// (누적 계산값, 현재값) => { return 누적 계산값 + 계산값 };
const arr = [1, 2, 3, 4, 5];

const result = arr.reduce((prev, cur) => {
  // 처음에 초기값(prev) == 0, 현재값 == 1.
  return prev+cur; // return의 누산값: 1, cur의 현재값 1  ▶ 누산값 3 (요런 로직이당)
}, 0) // 초기 값 0 설정

console.log(result);  // 15
```

<br/>

### 📚 참고

---

- [mdn] https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array
