## ✍ 자료형 (Data type)
### 1. 숫자형 (number)
- 자바스크립트에서는 정수와 실수 구분이 없음. type은 모두 number.
- 정수는 -(2^53) ~ (2^53) 까지 표현할 수 있음.
- Infitinity, -Infinity == ∞ 도 숫자형. 어떤 숫자든 0으로 나누면 무한대를 얻을 수 있음.
- NaN == Not a Number   부정확하거나 정의되지 않은 수학 연산 시 (ex. 문자열을 숫자로 나눔)
  - NaN 은 양/음이 없음    -(NaN)   # NaN
  - 주어진 값이 NaN 인지 확인하는 방법

```javascript
// NaN 판별 

let x = 1 / 'doopal';
console.log(
	x,  // NaN
    x == NaN,  // false
    x === NaN,  // false
    isNaN(x),   // true
    Number.isNaN(x)   //true
);

isNaN('doopal'); // true 
Number.isNaN('doopal'); // false

// 🔑 isNaN, Number.isNaN 을 사용하면 가장 분명하게 NaN을 판별할 수 있다.
// 	✔ isNan 과 Number.isNaN의 차이
// 	- isNan : 인자를 Number로 변환후 > 그게 NaN이면 true
// 	- Number.isNaN : 걍 인자로 들어온 값이 NaN 이어야만 true
    
// 👉 NaN은 다른 모든 값과 비교 시(==, ===, !=, !==) false 
// 👉 같은 NaN과 NaN 끼리 비교해도 false
// 👉 ❗❗ 오로지 NaN 만이 자기 자신과 비교했을 때 같지 않다고 나온다.
```
### 2. BigInt 
- 숫자형에서 표현할 수 없는 훨씬 더 크고 더 작은 정수를 표현할 때 사용
- 변수명 bigInt, 값의 끝에 n을 붙이면 만들 수 있다.
  - const bigInt = 1234567890123456789012345678901234567890128901234567890n;

### 3. 문자형 (string)
- 문자열을 따옴표로 묶어준다. (큰 따옴표/ 작은따옴표 구분 X)
  - 따옴표의 종류 : ①" " 큰 따옴표  /  ② ' ' 작은따옴표  /  ③ ` ` 역따옴표(백틱)
  - 템플릿 리터럴 ==
백틱 (\`)  사용하여 변수나 표현식을 감싼 후 ${ } 안에 넣어주면 문자열 중간에 쉽게 넣어 줄 수 있음
const userName = 'Doopal';
ex.  console.log("Hello, ${userName}!");     #  Hello, ${userName}!
ex.  console.log(`Hello, ${userName}!`);     #  Hello, Doopal!

### 4. 불린형 (boolean)
- true / false
- 직접 할당되기 보다 반환값으로 곳곳에 활용된다.

### 5. null
- 존재 하지 않는 값(nothing) / 비어있는 값(empty) / 알 수 없는 값(unknown)
- 의도적으로 비어있음을 표현 한 값이다.
- 값이 없는 것이 아님❌ null 역시 값은 값임. '비어있다'라는 값.

### 6. undefined
- 값이 할당되지 않은 상태라는 뜻의 값. 값이 없는 것이 아님❌ 
- 변수를 선언했지만 할당을 하지 않았다면 해당 변수에 undefined가 자동으로 할당된다.
- 명시적으로 undefined를 할당하는것도 가능하긴 함 (but  권장 ❌,  null 사용 권장 ⭕)

### 7. 심볼형 (symbol)
- 객체의 고유한 식별자를 만들 때 사용


### 8. 객체형 (object)
- 위 7가지 자료형과 달리 객체형만 하나 이상의 데이터를 담을 수 있다.
- { } 안에 key : value 쌍으로 구성된 프로퍼티를 여러 개 넣을 수 있다.
- key에는 문자형 /  value에는 모든 자료형이 허용된다.
🗃 서랍장을 상상하면 이해가 쉽다.
빈 서랍장 (==객체) 안에 파일(==프로퍼티)을 여러 개 넣을 수 있다.
파일에 각각 붙어있는 이름표(==key )
- 프로퍼티 출력하기
  - console.log(변수명.key);    ||    console.log(변수명['key'])

***

## ✍ typeof 연산자
- 뒤에 오는 값의 자료값을 반환 해 준다.
```
typeof  'a'          # 'string'
typeof  42          # 'number'
typeof  (2<3)     # boolean
```
- **typeof의 반환값은 string**
***

## ✍ 원시타입 & 객체타입
### 1) 원시타입 (Immutable data types: primitives types)
- 자료형들 중 객체형(object)을 제외한 모든 자료형들이 원시타입이다.
- 원시타입의 변수를 생성하면 메모리에 해당 변수만을 위한 공간이 할당이 되고, 
그 곳에 원시타입의 값이 저장이 되고, 그 값 딱 하나만 저장된다.
  - so, 원시타입의 변수는 직접적으로 이 값을 가리키는 형태가 된다.
- 메모리 영역 안에서 변경 불가능하다.
만약 원시타입이 mutable 했다면 값을 변경 할 수 있게 되고 할당된 메모리 공간을 초과하게 될 것이다. 
- 변수에 할당 할 때 완전히 새로운 값이 만들어져 재 할당된다.
원래 값이 없어지는게 아니라 가리키는 값이 바뀌는 것
- **✨🚨 null 은 원시타입이나, 초기오류로 typeof 연산자 사용하면 object가 반환된다. (객체는 원시타입 X)**
  -  so,  null 여부 확인은 아래와 같이 확인할 것
      ex. let  a  = null;
      console.log( a === null); ✨

### 2) 객체타입 (Mutable types: Object type, Reference type)
- 원시타입 데이터들의 집합, 몇 개나 될지 모르는 여러 개의 값을 저장하기 때문에
원시타입처럼 고정된 크기의 메모리를 한 번에 할당 받는 것이 아니라 힙(Heap)이라는
별도의 메모리에 값을 저장하고 변수에는 이 메모리를 가르키는 주소 값만 저장한다.
  - so, 이 변수를 사용할 때 주소값을 참조해서 사용한다.
- 원시타입을 제외한 나머지 값들 (배열, 객체, 함수 등)등은 모두 객체이다