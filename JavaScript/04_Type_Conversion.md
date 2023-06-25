> 형 변환은 Type Conversion일까? Type Casting일까?
- 1. Type Casting: 타입 캐스팅의 경우 프로그램 설계 중에 프로그래머가 
해당 언어의 캐스팅 연산자를 사용하여 기존 데이터 유형을 다른 데이터 유형으로 의도적으로 변환하는 작업
- 2.Type conversion: 타입 컨버젼의 경우 데이터 타입이 컴파일러 또는 인터프리터 등을 통해 
컴파일러타임, 런타임을 통해 자동으로 다른 데이터 타입으로 변환되는 작업. 
그렇기에 대상 데이터 타입은 변경되는 타입보다 작을 수 없으므로 확장 변환(widening conversion)이라고도 한다. 
그리고 가장 중요한 점은 서로 호환이 가능한 데이터 타입에만 적용할 수 있다.
>> 참조 블로그: [velog - 형 변환은 Type Conversion일까? Type Casting일까?](https://velog.io/@zeebeck/%ED%98%95-%EB%B3%80%ED%99%98)

***

## ✍ 형 변환 (type conversion) 이란?
- 자료형을 변환시켜주는 것
- JS 엔진의 필요에 따른 암시적 변환  ||  개발자 의도에 따른 명시적 변환

***

## ✍ 암시적 형 변환
### 1. 문자형으로 변환
- 문자형과 ➕ 문자형이 아닌 자료형 ➡  문자형이 아닌 자료형들이 문자형으로 자동 형 변환 된다.
```javascript
let result1 = 1 + '2';
console.log(result1);   // 12
console.log(typeof result1);   // string

let result2 = '3' + true;
console.log(result2);   // 3true
console.log(typeof result2);   // string

let result3 = '2' + null;
console.log(result3);   // 2null
console.log(typeof result3);   // string

let result4 = '2' + {};
console.log(result4);   // 2[object Object]
console.log(typeof result4);   // string

// cf. {}, null, undefined + '1' 👉 모두 문자열이 된다.
```

### 2. 숫자형으로 변환
숫자형과 숫자형이 아닌 자료형들을 더하기연산자 제외 다른 산술 연산자로 연산 시 숫자형으로 자동 형 변환된다.
```javascript
let result5 = 5 - '1';
console.log(result5);   // 4
console.log(typeof result5);   // number

let result6 = '3' * '2';
console.log(result6);   // 6
console.log(typeof result6);   // number
```

***

## ✍ 명시적 형 변환
### 1. 문자형으로 변환
```javascript
let result1 = String(123);
console.log(typeof result1);    // string
console.log(result1);    // 123

let result2 = String(null);
console.log(typeof result2);    // string
console.log(result2);    // null
```

### 2. 숫자형으로 변환
```javascript
let result1 = Number('123');
console.log(typeof result1);   // #number
console.log(result1);   // # 123

let result2 = Number(true);
console.log(typeof result2);   // #number
console.log(result2);   // # 1

let result3 = Number(undefined);
console.log(typeof result3);   // #number
console.log(result3);   // # NaN

let result4 = Number({});
console.log(typeof result4);   // #number
console.log(result4);   // # NaN

let result5 = Number('');
console.log(typeof result5);   // #number
console.log(result5);   // # 0
```

### 3. Boolean형으로 변환
```javascript
console.log(Boolean(NaN))    // #false
console.log(Boolean(undefined))    // #false
console.log(Boolean(0))    // #false
console.log(Boolean(''))    // #false
console.log(Boolean('0'))    // #true
console.log(Boolean({}))    // #true
console.log(Boolean('false'))    // #true
```