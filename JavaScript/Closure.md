## ✍ 클로저(Closure)란?
>`자신이 선언된 당시의 환경을 기억하는 함수`
자신을 포함하고 있는 외부함수보다 내부함수가 더 오래 유지되는 경우, 외부 함수밖에서 내부 함수가 호출 되더라도<br> 
외부 함수의 지역변수에 접근 할 수 있는데, 이런 함수를 클로저 라고 부른다.<br> 

```javascript
let outer = function () {
  let a = 1;
  let inner = function () {
    return ++a;
  };
  return inner;
};
let outer2 = outer();
console.log(outer2());
console.log(outer2());
```
1. 전역 실행 컨텍스트 실행 ▶  `environmentRecord` - outer :f , outer2 : undefined
   + outer2에는 outer 함수 실행이 종료 시점에 어떤 값이 담김
2. outer 함수 호출, 실행 컨텍스트 생성 - outer의 `environmentRecord` - a =1 , inner:f /<br> 
 `outerEnvironmentReference` - outer의 `environmentRecord`<br> 
inner가 return 되었으니 1번의 outer2 에 inner가 담김.<br> 
>✨ **여기서 outer 함수는 종료되었으나(실행 컨텍스트도 종료), outer2에 의해서 <br> 
다시 언젠가 inner 함수가 호출 될 수 있으므로 a변수의 참조카운트가 0이 아닌 상태임. == 변수가 죽지 않음**
3. outer2()호출 == inner()호출 == inner 함수에 대한 실행컨텍스트 생성<br> 
inner 내부에는 a가 없고 외부환경참조를 하고 있음. <br> 
outer의 a:1 → 2 / inner도 참조하고있으니 같이 바뀜 a:1 → 2 / inner 함수 종료, console.log  2 출력
4. 위와 동일한 과정 반복 console.log 3 출력

<br/>

## ✍ 클로저의 특징 & 활용
> **클로저의 핵심은 '스코프'를 이용하여 변수의 접근 범위를 닫는 것에 있다**<br> 
외부함수 스코프 > 내부함수 스코프 접근 ❌<br> 
내부함수 > 외부함수 스코프에서 선언한 변수 접근 ⭕ <br> 

+ **데이터 보존**
  + 외부 함수의 실행이 끝나더라도 외부 함수 내 변수를 사용할 수 있다.<br> 
  특정 데이터를 스코프 안에 가두어 둔 채로 계속 사용할 수 있게 하는 폐쇄성을 이용하여 데이터를 보존한다.<br> 
+ **정보의 접근 제한 (캡슐화)**
  + 클로저 모듈 패턴 을 사용하여 객체에 담아 여러 개의 함수를 리턴하도록 만든다.<br> 
  이러한 정보의 접근을 제한하는 것을 캡슐화 라고 한다.<br> 
+ **모듈화**
  + 클로저 함수를 각각의 변수에 할당하면 각자 독립적으로 값을 사용하고 보존할 수 있다.<br> 
  이와 같은 함수의 재사용성을 극대화하여 함수 하나하나를 독립적인 부품의 형태로 분리하는 것을 모듈화 라고 한다.<br> 
  클로저를 통해 데이터와 메서드를 묶어다닐 수 있다 == 모듈화에 유리함<br> 

<br/>

### 📚 참고자료
***
[강의]
+ [인프런 - 코어 자바스크립트](https://www.inflearn.com/course/%ED%95%B5%EC%8B%AC%EA%B0%9C%EB%85%90-javascript-flow/dashboard)
_해당 강의 수강 후 정리한 내용입니다 :)_

[사이트]
+ [코어 자바스크립트 - 변수의 유효범위와 클로저](https://ko.javascript.info/closure)

[블로그]
+ [[JS] 📚 클로저 (Closure) 개념 완벽 정리](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%ED%81%B4%EB%A1%9C%EC%A0%80)
+ [[JavaScript] 클로저(Closures)란 무엇일까?](https://hanamon.kr/javascript-%ED%81%B4%EB%A1%9C%EC%A0%80/)