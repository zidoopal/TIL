> 여기 저기서 **DOM** 이란 말을 꽤나 많이 들어보았다. <br>
> 어떻게 생겨먹은 애 인지, 어떤 과정으로 생긴 건지 매번 얼렁 뚱땅 넘어가기만 했는데<br>
> 앞으로 자주... 아니...그냥 계속 만날 친구같다...🙄 자세히 알아봐야겠다.

<br>

## DOM 이란?

**'Document Object Model** : **문서 객체 모델'** :

- **HTML 문서를 '객체화'** 한 것
- 웹 페이지에서 자바스크립트로 요소들을 제어하는데 사용되는 Document Object Model을 말한다.<br>

🤔 뭔가 확 와닿지가 않는다. 뭐 어떻게 생겨먹은건데 그래서. 어떻게 써먹는건데.<br>

<br>

```html
<!-- HTML -->
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="UTF-8" />
  </head>
  <body>
    <h1 id="title">사올 것</h1>
    <ul>
      <li>토마토</li>
      <li>감자</li>
      <li>사과</li>
    </ul>
    <button>구매완료</button>
  </body>
</html>
```

위와 같은 html코드를 JS로 변화를 주고자 한다.

```javascript
const title = document.getElementById('title');
title.textContect = '이미 다 샀다';
```

그런데 여기서 `document`, `getElementById()`, `textContent` 는 **자바스크립트 요소가 아니다.**<br>

크롬같은 브라우저 환경의 콘솔창에서 document를 확인해보면 document 객체를 출력 해볼 수 있지만<br>
![](https://velog.velcdn.com/images/doopal2/post/66065ec9-d314-42f9-8f18-13f3da5b4bae/image.png)<br>
자바스크립트 실행하는 Node.js 환경에서 똑같이 `console.log(document);` 를 실행해보니<br>
![](https://velog.velcdn.com/images/doopal2/post/e9140d77-3908-4316-975d-0e388d17d3d1/image.png)document가 없다고 에러가 뜬다 😐<br>
왜 브라우저에서는 되는데 Node.js에서는 안되는걸까?<br>

**애초에 document 객체 자체가 자바스크립트 자체 요소가 아니라 브라우저 환경에서 제공되는 것이기 때문이다**<br>
웹 개발에서 사용되는 document 객체는 브라우저에서 제공되는 **window 객체의 한 요소**이고, <br>
**window.document 객체를 DOM 으로 분류한다.**<br>

```html
window.document <--! Documnet Object Moel (DOM) --> window.location <--! Browser
Object Model (BOM) --> window.navigator window.history ...
```

> **DOM **&&** BOM 👉 Web API 라고 부른다 ** <br>
> 자바스크림트의 기능은 아니지만, 자바스크립트 등을 통해 제어될 수 있도록 브라우저에서 제공되고 있다.<br>
> <br>
> 우리가 웹사이트에 접속하면 브라우저가 HTML(+ CSS,JS) 문서를 읽어들인다.<br>

**HTML 코드**가 어떤 **제품의 설계도**라고 한다면, **브라우저**를 **공장**이라고 생각해보자.<br>
그리고 공장에서 이 **설계도를 해석하는 과정**을 == **파싱(Parsing)**,<br>
그리고 그 결과물로 나온 **제품** == **DOM**이라고 비유할 수 있다.<br>

근데 이 기계(**DOM**)는 왜 만드는 거고, 어떤 모습인걸까?<br>
<br>

## DOM API

위에 HTML 코드를 브라우저가 파싱하면 대략적으로 아래와 같은 구조의 DOM이 만들어지게 된다. (트리 형식)<br>

![](https://velog.velcdn.com/images/doopal2/post/671450ba-fb93-4151-b015-0216ddeb880e/image.png)<br>
DOM 은 이 트리 전체를 말한다. (++ 그림에는 없지만 CSS가 파싱을 거치고 난 CSSOM도)<br>
그리고 이를 구성하는 부품들, document, html, body..요소 하나하나를 Node라고 부른다.<br>
이들은 상속적인 구조를 가지고있다.<br>

<span style="background-color:#FFFF81">**우리가 JavaScript로 웹페이지의 요소들을 제어할 수 있는 건 이것들 하나하나가 모두 [API](https://www.youtube.com/watch?v=ckSdPNKM2pY)이기 때문이다** </span>

<br/>

## JS가 DOM을 사용하면?

- HTML문서의 모든 HTML 요소를 변경 할 수 있다!
- HTML문서의 모든 HTML 속성을 변경할 수 있다!
- HTML문서의 모든 CSS 스타일을 변경할 수 있다!
- 새로운 HTML 요소, 속성을 추가할 수 있다!
- HTML문서에 있는 모든 HTML 이벤트에 반응할 수 있다!
- HTML문서에 새로운 이벤트를 추가할 수 있다!

<br/>

> ❔ 파싱(parsing) 과 컴파일(compile)의 차이점?

- **Parse : (문장을 문법적으로) 분석하다 / <낱말의> 품사·문법적 관계를 설명하다**
  - 파싱하다는 문법적으로 해부하는 뜻으로 이해하면 될 것 같다.
- **Compile : (프로그램을) 다른 부호[기계어]로 번역하다**
  - 컴파일에는 파싱이 선행이 된다!
    > 요 두 단어가 헷갈렸는데, 예시를 보니까 이해가 잘 되었다 :)<br>
    > `I am a boy` 라는 문장을 (기계어 대신)한국어로 컴파일 한다고 가정했을 때, <br>

1. **해당 단어에 맞게 각각 잘라서 번역을 하고 (파싱)**

- `I` 나 + `am` 는 ~이다 + `a` 어 `boy` 뽀이

2. **한국어로 번역한다. (컴파일)**

- `I am a boy` 나는 뽀이다.

<br/>

### 📚 참고자료

---

[동영상]

- [Youtube: 얄팍한 코딩사전 - 웹개발 필수개념! DOM이 뭔가요? (+ Web API)] (https://www.youtube.com/watch?v=mFawNZz_Uu0)
- [Youtube: 코딩애플 - 코딩초보들이 헷갈리는 용어 : API가 뭐냐면] (https://www.youtube.com/watch?v=ckSdPNKM2pY)

[사이트]

- [mdn - DOM 소개] https://developer.mozilla.org/ko/docs/Web/API/Document_Object_Model/Introduction

[블로그]

- [[JavaScript] JS DOM 이란?] https://mingmeng030.tistory.com/223?category=1013860
