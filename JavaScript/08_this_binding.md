## 🤔 바인딩(binding)은 도대체 무슨 뜻일까? 
+ 사전적 의미의 bind == '묶다 / 감다 / 싸다' 
+ **코딩에서의 바인딩** == **식별자와 값을 연결하는(묶는) 과정**
  + 변수 선언은 변수 이름과 확보된 메모리 공간의 주소를 '바인딩' 하는 것이다.
  + this 바인딩은 `this`와 `this를 가리킬 객체`를 바인딩 하는 것이다.

***

## ✍ JavaScript의 this 바인딩
![](https://velog.velcdn.com/images/doopal2/post/2987b597-2d47-4d6f-8e23-f4c55eae8d9f/image.png)<br>
>✨**ThisBinding` 은 어디서 한다? ▶ 실행컨텍스트 활성화 될 때 한다!** 앞으로 이 개념을 잘 기억해 두잣

+ 실행 컨텍스트가 생성되는 순간에 this를 바인딩 한다.
  + 실행 컨텍스트는 언제 생성된다? ▶ 이 컨텍스트에 해당하는 함수가 호출되는 순간!
 + **`this`는 함수가 호출 될 때에 비로소 결정된다.**<br>
  `this`는 정적으로 코드만 봤을 때에는 얘의 `this`가 무엇이다~라고 바로 예측 하기 어렵고<br>
  **'이 함수를 어떤 방식으로 호출 했느냐'** 에 따라서 this는 얼마든지 달라질 수 있다. (== 동적으로 바인딩 된다)

<br>

## ✍ 호출 방식에 따른 this의 사용

### ✔ 전역공간에서의 - this
+ **전역 공간에서의 `this`는 전역 객체를 가리킨다.** 
  + 전역 컨텍스트를 실행하는 주체 : 전역 객체
  + 런타임에 따라 전역객체의 정보가 달라진다. **window**(브라우저) / **global**(node.js)<br>
  ![](https://velog.velcdn.com/images/doopal2/post/5615c97f-8345-4805-8e7d-025943baadfa/image.png)

<br>

### ✔ ✨ 함수를 함수로써 호출했을 때 - this
+ **함수로 호출 했을 때도 `this`는 전역 객체를 가리킨다.**  (😵흐음..?)
  + **window**(브라우저) / **global**(node.js)

> 
```javascript
function a() {
    function b() {
        console.log(this);
    }
    b();
}
a();
```
위 코드에서 a함수 호출 할 때에 주체가 전역객체인 건 알겠다능 (a함수 내부에서의 `this`는 전역 객체이다.)<br>
>🤔 ... 근데 b함수는 a함수 내부에서 호출 한 건데 호출한 주체가 a가 아닐까..? 근데 여기서도 주체는 전역객체가 나옴.
>
😹 이게 버그인지..JS의 특성인지는 저는..모르겠읍니다....<br>
**ES6** 에서는 이러한 문제들 때문에 아예 this 바인딩을 하지 않는 **`화살표 함수`**가 나왔음.<br>
>>`화살표 함수` 는 바로 위 컨텍스트에 있는 this를 그대로 가져다 씀 👉스코프 체이닝 상의 `this`에 바로 접근<br>
>>
```javascript
let a = 2;
let obj = {
    a: 3,
    b: function(){
        console.log(this.a);        // 3   // 이 때의 this는 obj
>>>
        const c = () => {           // 화살표 함수는 this 바인딩 ❌ 
            console.log(this.a);    //  3   // 이 때의 this도 obj
        }                         
        c();
    }
};
obj.b();
```
>
😔 anyway.....<br>
**ES5** 환경에서는 **함수로써 호출했을 때 `this`는 무조건..언제나..전역객체를 가리킨다..!**

<br>

### ✔ 함수를 메서드로써 호출했을 때 - this
+ **메서드로써 호출 했을 때의 `this`는 '호출한 주체**(메서드명 앞)**'가 바인딩 된다.**
  + 메서드: 객체 안에 프로퍼티로 정의된 함수 <br>
  💭 원래는 함수인데, 어떤 객체와 관련된 동작을 하게되면 그 때는 메서드라고 부르겠다~<br>
  
> 예제  1)
```javascript
let c = {
    d: function() {
        function e() {
            console.log(this);
        }
        e();
    }
};
c.d();
```
>✨ `c.d();` : `d` 함수를 `c`객체의 메서드로써 호출<br>
✨**`this`는 `.` 앞의 객체를 참조함 **<br>
👉 `.` 앞에 있는 `c`가 `this`가 된다.<br>
>
>>`d` 메서드 안에 `e`라는 내부함수가 또 있다.<br>
6번째 줄 `e();` : 얘는 그냥 함수로써 호출함 ==  여기서의 `this`는 아묻따 전역객체<br>
<br>

> 예제  2)<br>
![](https://velog.velcdn.com/images/doopal2/post/162848f7-428d-49d7-9a3d-5b6e9fe8381e/image.png)<br>
><br>
이번에는 `a.b.c` 호출, 이 때 `c`라는 함수안에서 `this` 호출 하면?<br>
![](https://velog.velcdn.com/images/doopal2/post/9e93c8b4-b2df-4bf4-aa4f-3fbeeaf18e42/image.png)<br>
>
>✨**`this`는 `.` 앞의 객체를 참조함 **<br>
>`.` 앞에 `a.b`가 `this`가 된다. (에디터에서는 색깔로 this, 메서드 구분도 잘 된다 ㅎㅎ)<br>
>_cf. 결과에서 `{c: f}` 는 `a.b`와 동일_<br>
<br>

> 🚨
>**대괄호 표기법 `[]`** 썼을 때 주의!
```javascript
obj.func();     // 이때의 this는 obj
obj['func']();  // 이때의 this는 obj
>
person.info.getName();        // 이때의 this는 person.info
person.info['getName']();     // 이때의 this는 person.info
person['info'].getName();     // 이때의 this는 person['info']
person['info']['getName']();  // 이때의 this는 person['info']
```

<br>

### 💡 명시적 바인딩 (bind, call, apply)
>우리는 상황에 따라 this의 객체가 바뀌는 것을 보고있다..😵
>
기본적으로 `this`는 window객체를 사용하나, <br>
**명시적으로 `this`를 window가 아닌 다른 객체로 바꿔주는 함수**가** `call`, `apply`, `bind`** 이다.<br>
**이때 `this`는 내가 '명시한 객체'에 바인딩 된다.**<br>
> **1. `call`** / `func.call(thisArg[, arg1[, arg2[, ...]]])`
+ 함수를 호출함 / 호출하는 함수의 매개변수를 별개의 인자들로 받음<br>
+ **첫번 째 인자에 `this`로 셋팅하고 싶은 객체를 넘겨주어 this를 바꿔줌**<br>
<br/>

>
**2. `apply`**  / `func.apply(thisArg, [argsArray])`
+ 함수를 호출함 / 호출하는 함수의 매개변수를 배열로 받음
+ **첫번 째 인자에 `this`로 셋팅하고 싶은 객체를 넘겨주어 this를 바꿔줌**
<br>

> **3. `bind`** / `func.bind(thisArg[, arg1[, arg2[, ...]]])`
+ **`bind`**는** 함수가 가리키는 `this`만 바꾸고 함수를 실행(호출)하지 않는다.**
+ 변개의 바인딩한 함수를 반환함. 변수를 할당하여 호출하는 형태로 사용 됨
  + 하드 바인딩 (명시적 바인딩을 함수로 한 번더 래핑함)<br>
  💡 하드 바인딩된 함수를 사용해 다른 함수에서 `this`가 변경되는 일을 방지할 수 있다<br>
  >
![](https://velog.velcdn.com/images/doopal2/post/6287efd3-b375-45e9-8620-d062cd37ba4e/image.png)<br>

>😵 `call`, `apply` 는 이해됐는데, `bind` 부분이 좀 헷갈렸다..!<br>
```javascript
const c = a.bind(b);   // 여기선 아직 함수 호출 X 그냥 this를 들고있는 상태
    c(1, 2, 3);        // 이제야 들고있는 this를 물고 + 나머지 인자를 넣어줌
```
>
```javascript
const d = a.bind(b, 1, 2); // 함수실행 아직 X,  그냥 this를 들고있는 상태 
						   // 먼저 this와 함께 1,2번째 매개변수 넘김
    d(3);				   // 매개변수 3을 넘기면서 함수 호출
```

<br/>

### ✔ 함수를 콜백함수로 넘겼을 때 - this

+ **콜백함수 내부에서의 `this` 기본적으로는 전역객체를 봄**<br>

🤔 기본적이지 않을 때는 어떤데? 👉 **지정하는 바에 따라서 달라 짐**<br>
+ **콜백함수를 넘겨 받는 대상이 콜백함수를 어떻게 처리하느냐에 따라서 `this`가 달라짐**<br>
(콜백 함수 자체가 뭘 어떻게 할 수 있는것은 아님)<br>
<br>

>예 1)<br>
![](https://velog.velcdn.com/images/doopal2/post/8fc766a7-c8d2-404d-b87e-68c1c536e438/image.png)
=<br>
여기서 `cb();` 는 함수로써 호출함 ▶ `this`는 전역객체(window)<br>
so, 콘솔에는 전역객체(window)가 출력됨<br>
<br>

>예 2)<br>
![](https://velog.velcdn.com/images/doopal2/post/71dbac50-2f1e-4427-8814-6c21b1e772d1/image.png)
=<br>
여기서 `cb.call(this);` <br>
call함수 사용 ▶ `this`를 `cb의 this`로 (이 컨텍스트에서 `this` == `obj`)<br>
so, 콘솔에는 `obj`가 출력됨<br>

**📝 (콜백함수 호출 시 -정리)**
+ 기본적으로 함수의 `this`와 같다. (전역객체를 봄)
+ 제어권을 가진 함수가 콜백의 `this`를 지정해 둔 경우도 있다 (ex. addEventListener)
  + 이런 경우에는 지정해 준 `this`를 따름
  + but, 개발자가 `this`를 바인딩해서 콜백을 넘기게되면 그에 따라야 함. (ex. bind 명령 등)


<br>

### ✔ 함수를 생성자함수로써 호출했을 때 - this
+ **`new 연산자`를 쓴다 == 생성자 함수의 내용을 바탕으로 인스턴스 객체를 만드는 명령**<br>
👉 **새로 만들 인스턴스 객체 그 자체가 곧 `this` 가 됨**

>
```javascript
function Person(n, l) {
    this.name = n;
    this.level = l;
}
const doopal = Person('두팔', 100);  
console.log(window.name, window.level);   // 두팔 100
```
일반적으로 `new 연산자` 없이 그냥 Person 함수를 호출 할 경우, <br>
▶ 기본적인 함수로써의 호출 == 이때의 `this`는 전역객체를 가리키게 됨.<br>
<br>
>
```javascript
function Person(n, l) {
    this.name = n;
    this.level = l;
}
const doopal = new Person('두팔', 100);  
console.log(doopal);   // Person {name: '두팔', level: 100}
```
`new 연산자` 사용하여 호출<br>
▶ **생성자 함수로써의 호출 == 새로 생성될 Person의 인스턴스 객체 자신이 곧 `this`가 됨**<br>
객체가 새로 만들어지면서 그 객체 안에 name 프로퍼티, level 프로퍼티가 생성됨<br>
그 객체가 다시 doopal 이라는 변수에 담김<br>

<br/>

### 📚 참고자료
***
[강의]
+ [인프런 - 코어 자바스크립트](https://www.inflearn.com/course/%ED%95%B5%EC%8B%AC%EA%B0%9C%EB%85%90-javascript-flow/dashboard)
_해당 강의 수강 후 정리한 내용입니다 :)_

[사이트]
+ [모던 JavaScript 튜토리얼 - 메서드와 this](https://ko.javascript.info/object-methods)
+ [모던 JavaScript 튜토리얼 - 함수 바인딩](https://ko.javascript.info/bind)
+ [ mdn - Function.prototype.bind()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/bind)
+ [제로초 - 자바스크립트의 this는 무엇인가?](https://www.zerocho.com/category/JavaScript/post/5b0645cc7e3e36001bf676eb)
+ [제로초 - 함수의 메소드와 arguments](https://www.zerocho.com/category/JavaScript/post/57433645a48729787807c3fd)