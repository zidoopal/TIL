## ✍ 콜백함수란?
> **call back** == **회신/답신하다**<br>
**callback function** == **회신되는 함수**<br>

![](https://velog.velcdn.com/images/doopal2/post/852e5548-30af-48aa-b88b-e9d1c0fe0399/image.png)
+ 넘기려는 대상한테 **콜백함수에 대한 제어권을 넘김**(위임)
+ **제어권을 넘겨받은 대상**이 **콜백함수 처리에 대해서 관여**함

<br/>

## ✍ 제어권 위임 
넘겨주게 될 **제어권**에는 **실행시점 / 매개변수 / this**가 있다.
###  🔎 실행 시점 
>ex)
![](https://velog.velcdn.com/images/doopal2/post/9f134e32-8f5d-4554-8e84-e461c25363b0/image.png)
콜백함수를 넘겨주고, '이거 실행해!' 라고 명령을 내려서 실행되는게 아니라<br>
`setInterval`이 알아서 주기마다 실행 해 줌 ( 제어권을 `setInterval` 에게 넘겨줌)<br>
 
###  🔎 매개변수
>ex)
![](https://velog.velcdn.com/images/doopal2/post/d2ce2f64-22da-4c91-8712-d749f92494c5/image.png)
=
```
forEach - 배열에 있는 요소들을 순서대로 하나씩 꺼내서 
첫 번째 매개변수에 값, 두 번째 매개변수에 index를 부여하면서 이 함수를 실행해줌
```
arr에 있는 요소를 하나씩 꺼내서 첫번째 요소(a)로 하고, <br>
그 다음에 (b)에 배열의 index부여 - 이렇게 배열 전체를 한 번씩 돌아쥼<br>
🤔 아직 this 는 뭔지 모르겠음<br>
> <br>
![](https://velog.velcdn.com/images/doopal2/post/096cfa9f-8716-4706-9551-1a9610dddda7/image.png)
=
결과에서 this[0] == 10 이라고 나옴 (두 번째 인자 - 배열의 첫번째 요소가 10임)<br>
> <br>
![](https://velog.velcdn.com/images/doopal2/post/4cf0d9fc-65db-468e-a62b-bf5802d7d12a/image.png)
>
`forEach`  메서드 자체에 규칙이 정해져 있음<br>
`'첫 번째 인자는 콜백 함수를 받고, 두 번째 인자는 thisArg를 받는다(생략 가능)'`<br>
><br>
✨ **내가 제어권을 넘겨주고자 하는 대상의 규칙에 따라야만 동작을 제대로 할 수 있음**

###  🔎 this
>![](https://velog.velcdn.com/images/doopal2/post/268cb135-13ff-4d4b-8e46-9f6dee74ac6d/image.png)
=
`addEventListener(type, callback, options)`<br>
`addEventListener`에는 매개변수가 이벤트 객체로 지정이 되고, `this`에는 currentTarget이 바인딩 된다. 👉 규칙이 정해져 있음<br>

<br/>

## ✍ 콜백함수의 특징
+ 다른 함수(A)의 인자로 콜백함수(B)를 전달하면, A가 B의 **제어권**을 갖게된다.
  + 특별한 요청(`bind`)이 없는 한, A에 미리 정해놓은 방식에 따라 B를 호출한다.
  + 미리정해놓은 방식
    + 어떤 시점에 콜백을 호출 할지?
    + 인자(매개변수)에는 어떤 값들을 지정할지?
    + `this`에는 무엇을 바인딩 할지 등<br>
  👉 개발자는 이러한 규칙에 따라서 정확히 호출해야 원하는 결과를 얻을 수 있음<br>
 + 콜백 == 함수
   + 🚨 메서드로 호출 / 콜백함수로 전달 둘을 잘 구분해야 함
![](https://velog.velcdn.com/images/doopal2/post/363a87cc-3f35-4380-936b-ec22ca704a85/image.png)
   + obj를 this로 지정하고 싶으면?
   ![](https://velog.velcdn.com/images/doopal2/post/d0b8d512-7b16-4d13-8642-34bc2282776f/image.png)


<br/>

### 📚 참고자료
***
[강의]
+ [인프런 - 코어 자바스크립트](https://www.inflearn.com/course/%ED%95%B5%EC%8B%AC%EA%B0%9C%EB%85%90-javascript-flow/dashboard)
_해당 강의 수강 후 정리한 내용입니다 :)_

[사이트]
+ [mdn - Array.prototype.forEach()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach)