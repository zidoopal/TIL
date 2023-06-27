>자바스크립트의 내부 동작 원리를 알기 위해  
'**실행 컨텍스트**'와 '**실행 스택**(콜 스택)'에 대한 이해는 
호이스팅, 스코프 그리고 클로저와 같은 자바스크립트 컨셉을 이해하기 위한 필수요소 이다.

***

## ✍ 실행 컨텍스트란?

>📌 `실행 컨텍스트` == **코드를 '실행(Execution)'하는데에 필요한 '조건/환경(Context)**'
자바스크립트의 '**동적 언어**'로서의 성격을 가장 잘 파악할 수 있는 핵심 개념

실행 컨텍스트는 자바스크립트 코드가 실행되는 환경이다. 
**자바스크립트에서 동작하는 어느 코드이건, 실행 컨텍스트 내부에서 동작한다.**

실행 컨텍스트는 식별자(변수, 함수, 클래스 등의 이름)를 등록하고 관리하는 
스코프와 코드 실행 순서 관리를 구현한 내부 매커니즘으로, 
**실행컨텍스트 == 자바스크립트의 핵심 원리**이다.

***

## ✍ 실행 컨텍스트의 종류

+ 전역 실행 컨텍스트
  +  실행 컨텍스트의 기본/기초. **함수 밖에 있는 코드는 전역 실행 컨텍스트에 있다.**
  + 브라우저의 경우 window 객체를 생성하여, 이를 글로벌 객체로 설정한다.
  **프로그램에는 오직 한 개의 전역 실행 컨텍스트만 있을 수 있다**.
+ 함수 실행 컨텍스트
  + 함수가 호출 되어 실행 될 때 마다 해당 함수에 대한 실행 컨텍스트가 만들어진다. 
  + 함수 실행 컨텍스트의 수는 제한이 없다. 
  + 새로운 실행 컨텍스트가 생성 될 때마다 정의된 순서에 따라 일련의 단계를 거친다
  (하단에 내용 추가)
+ ~~eval 함수~~
  + 위험한 코드라고 하셨다. ㅋㅋㅋ eval 함수는 문자열로 된 자바스크립트 코드를 전달하면 
그게 그대로 실행되는 함수인데, 속도나 보안이 좋지 않아 현재는 거의 쓰지 않는다. 
여기서 논외로 할 것.  

***

## ✍ 실행 컨텍스트는 언제 생성되는가?
자바스크립트 코드를 실행하는 순간 전역 컨텍스트를 현재 실행 스택에 `push` 한다
**자바스크립트가 실행되는 순간 전역 컨텍스트가 활성화** 된다고 생각하면 된다.
전역 컨텍스트는 모든 코드가 끝날 때 까지 유지된다.

엔진이 함수 호출();을 발견 할 때 마다, 함수를 위한 새로운 실행 컨텍스트를 생성하고
스택의 꼭대기에  `push` 한다.<br>

엔진은 스택 최상단에 있는 함수의 실행 컨텍스트를 실행한다.
이 함수가 완료되면 해당 함수의 실행 스택이 현 스택에서 pop(제거)된다.

✨ 중요한 점은 **함수 실행 컨텍스트**는 **<함수가 실행될 때!> 만들어진다**는 점이다.
**~~함수를 '선언' 할 때~~ ❌❌❌, 함수를 '실행' 할 때다.<br>**

💡
따라서, 자동으로 생성되는 전역공간과 eval을 제외하면
**실행 컨텍스트가 생성되는 시점 == 함수를 실행하는 시점**이다

> ### ✔ **실행 스택(Execute stack)**이란?
**호출 스택**(call stack) 이라고도 불림. 
실행 스택은 후입선출(Last In First OUT: LIFO)구조의 스택이다.
코드 실행 시, 생성되는 모든 실행 컨텍스트가 저장되는데 사용된다.

***

## ✍ 실행 컨텍스트의 내부
![](https://velog.velcdn.com/images/doopal2/post/a0adaeb6-1da2-4470-b0eb-ca5d1f16fe63/image.png)![](https://velog.velcdn.com/images/doopal2/post/6b02eadf-c20e-48fb-a403-4e2178675d35/image.png)
실행 컨텍스트에는 3가지 환경 정보들이 담긴다.
>+ `VariableEnvironment` : **식별자 정보 수집** (변화 반영 ❌)
현재 컨텍스트 내 식별자들에 대한 정보 ➕ 외부 환경 정보 
선언 시점의 `LexicalEnvironment`의 스냅샷으로, 변경사항은 반영되지 않는다.
  + environmentRecord (환경 기록)
  + outerEnvironmentReference (외부 환경 참조)
  <br>
+ ✨`LexicalEnvironment` : **각 식별자의 '데이터' 추적 ** (변화 반영 ⭕)
 ```
  일반적으로 함수의 LexicalEnvironment는 
  해당 함수가 가지는 자신의 로컬 스코프 범위를 말한다.
  ```
  + environmentRecord (환경 기록)
  + outerEnvironmentReference (외부 환경 참조)
<br>
+ `ThisBinding` : `this` 식별자가 바라보고 있는 대상 객체


> #### ✔ LexicalEnvironment 집중 포커스
비유) 어떤 실행 컨텍스트 'A'에 대한 환경정보가 담겨있는 사전
`LexicalEnvironment` == **실행 컨텍스트를 구성하는 환경정보들을 모아 사전처럼 구성한 객체**
```
실행 컨텍스트 A 환경사전
* 내부식별자 a: 현재 값은 undefined 이다.
* 내부식별자 b: 현재 값은 20이다.
* 외부 정보: D를 참조한다.
```

<br/>

###  ✔ EnvironmentRecord
  >+ environmentRecord : 현재 문맥의 식별자 정보가 수집됨
  > ✨ environmentRecord 의 정보 수집 과정을 
  좀 더 쉽게 이해하기 위해 만든 허구의 개념이 바로 **'호이스팅(Hoisting)'**
  >> **HOISTING** == 끌어 올리다 == **식별자 정보를 끌어 올리다**
  어디로? == **실행 컨텍스트 맨 위로**.
![](https://velog.velcdn.com/images/doopal2/post/76baf35f-378a-44d9-ba24-a8e02032f14e/image.png)
```javascript
function a() {
    return 'a';
}
var b;
var c;
```
>>호이스팅이 완료된 결과를 보면 **위에 끌어올려진 내용 전체가 바로 environmentRecord임
👉 실행 컨텍스트가 처음 생성되는 순간, 제일 먼저 하는일이 바로 이거임**
>>
>>현재 컨텍스트에서 선언되어 있는 식별 자들이 무엇이 있는가~ 하는 정보를 
코드 순서대로 수집하다보니 호이스팅 한 것이랑 똑같은 개념이 되어버림
>>
✨
environmentRecord가 수집한 이 정보들은 실제로 일어난 일임.
위 그림에서 오른쪽과 같이 보여지는 코드는 이해하기 쉽게 만들어놓은 허구의 개념일 뿐임
(그러나 개념은 같으니 오른쪽 처럼 이해해도 문제는 없음)

<br/>

### ✔ outerEnvironmentReference (outer)
>+ outerEnvironmentReference : 외부 환경에 대한 참조
  > 여기서 '환경' == `LexicalEnvironment`
  so, '외부 환경' 이라는 것은 외부의 `LexicalEnvironment`대한 참조 라는 의미
  **즉, 현재 문맥과 관련있는 외부 식별자 정보를 참조한다.**
  
>💡 
#### ✔ 스코프(scope)
  > outerEnvironmentReference 를 이해하기 위해서, 먼저 '스코프' 개념을 이해해야한다.
  + 스코프 == 식별자에 대한 유효 범위 (전역 스코프 / 지역 스코프)
  👉**변수의 유효범위는 실행 컨텍스트에 의해 만들어 짐.**
>>
```javascript
let a = 1;
function scope() {     // 함수 스코프
  let b = 2;
  console.log(a);     // 1
  console.log(b);     // 2
}
console.log(a);       // 1
console.log(b);       // Uncaught ReferenceError: b is not defined
```
>
스코프 함수 외부에서 선언한 변수 a는 함수 스코프 안에서도 접근이 가능하다.
그러나 함수 안에서 선언한 변수 b는 오직 함수 안에서만 접근할 수 있다.
변수 a는 전역 스코프 / 변수 b는 지역 스코프에 있기 때문이다.
>
**자바스크립트는 변수의 유효범위를 검색 할 때 안에서부터 바깥으로 찾아 나가는데,
이것을 스코프 체인 이라고 한다.**
👉 **스코프 체인 현상은 outerEnvironmentReference 에 의해서 만들어 짐**
>
전역 스코프에 선언된 변수들은 어느 곳에서든 접근이 가능하나,
지역 스코프는 선언된 함수의 내부에서만 접근이 가능하다.

    
![](https://velog.velcdn.com/images/doopal2/post/7106004a-5304-4656-8c3e-3d933687512a/image.png)
outerEnvironmentReference는 현재 호출된 함수가 선언되는 시점에서의 
LexicalEnvironment를 참조하는 포인터 이다.

outerEnvironmentReference는 연결리스트 형태를 띄며
'선언 시점의 LexicalEnvironment'를 계속 찾아 올라간다.

'선언 시점의 LexicalEnvironment'라는 건 결국 해당 함수가 속한 상위 스코프의 범위이다.

각 함수의 outerEnvironmentReference는 
오직 자신이 선언된 시점의 LexicalEnvironment 만 참조하고 있기 때문에
가장 가까운 요소로부터 위로 차례대로 접근 할 수 있다.

```javascript
let outerWrap = function () {
  let a = 1;

  let outer = function () {
    let b = 2;

    let inner = function () {
      console.log(a, b);        
      console.dir(inner);
    };

    inner();
    console.log(a);  
  };

  outer();    
};

outerWrap();

```
중첩 구조가 많아져도, 각 함수들이 자신이 선언된 시점의 
상위 `LexicalEnvironment`를 참조하고 있다는 것을 기억하면 어렵지 않다.
위의 코드에서 `console.dir(inner)`로 `inner` 함수의 계층 정보를 열어보면
`[[scopes]]` 프로퍼티에서 상위 스코프 정보를 확인 할 수 있다.
![](https://velog.velcdn.com/images/doopal2/post/586b38b2-a323-435d-9e45-5497302ed8a3/image.png)

+ 0번째 스코프에는 함수 outer의 `LexicalEnvironment`에서 선언된 
변수 b와 함수 inner가 있다.

+ 한 단계 올라간 1번째 스코프에는 함수 outerWrap의 `LexicalEnvironment`에서 선언된 
변수 a가 있다.

+ 그 다음 단계로 올라가면 전역 컨텍스트가 노출된다. 
이렇게 체인을 통해서 상위 스코프로 접근 할 수 있음을 알 수 있다.

cf. 전역 컨텍스트에서의 outerEnvironmentReference는 `null` 이다.

<br/>

### ✔ ThisBinding
이 컴포넌트에서, this의 값은 결정되거나 set 된 것이다.

전역 실행 컨텍스트에서, this의 값은 전역 객체를 참조한다.
(브라우저일 시, 윈도우 객체 참조)

함수 실행 컨텍스트에서, this의 값은 함수가 어떻게 호출되는지에 달려있다.
만약 객체 참조로부터 호출되면, this의 값은 해당 객체로 set 되고, 
그렇지않을 경우, 전역 객체 또는 undefined(strict 모드)로 set 된다.

this에 대한 내용은 이후에 더 자세하게 다뤄보즈아



<br/>

### 📚 참고자료
***
[강의]
+ [인프런 - 코어 자바스크립트](https://www.inflearn.com/course/%ED%95%B5%EC%8B%AC%EA%B0%9C%EB%85%90-javascript-flow/dashboard)
_해당 강의 수강 후 정리한 내용입니다 :)_

[블로그]
+ [실행 컨텍스트란 무엇인가요?](https://velog.io/@edie_ko/js-execution-context)
+ [자바스크립트의 실행 컨텍스트 (execution context)](https://velog.io/@ggong/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8%EC%9D%98-%EC%8B%A4%ED%96%89-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8-execution-context)
+ [[Javascript] Execution Context와 Lexical Environment](https://iamsjy17.github.io/javascript/2019/06/10/js33_execution_context.html)
+ [자바스크립트의 실행 컨텍스트(Execute Context)와 실행 스택(Execute Stack) 이해하기](https://velog.io/@bisu8018/Understanding-Execution-Context-and-Execution-Stack-in-Javascript)