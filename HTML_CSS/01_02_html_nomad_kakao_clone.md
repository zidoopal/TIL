## HTML - 노마드코더 코코아톡 클론코딩\_1~2강

> html, css 빠르게 훑어보기 - 모든 내용 기재 X <br>
> 잊었던 것 / 새로 알게된 것 / 중요하다고 생각되는 내용만 메모메모 📝

## HTML

### HTML 문서의 구조를 작성하는 방법

- `<!DOCTYPE html>` : 이건 html 문서야
  <br>

- `<head>` 파트 : 웹사이트의 환경 설정 (외부적으로 보여지지않는 설정)
  - `<meta>` 태그 : 부가적인 정보
    - 2개의 attributes 有
    1. name: 속성값에 **description** 들어가면 웹 페이지에 대한 설명
    2. content: 구글에서 웹 사이트 검색 시, 타이틀 아래 나와있는 웹사이트 설명== content의 내용
    - ✨ meta charset: 브라우저에게 text를 어떻게 그려달라는지 말해줌<br>
      👉 **한글이나 다른 특수문자가 있는 언어를 입력할 때, 이 charset 메타 태그가 없으면 <br>
      브라우저가 이해를 못해서 사이트에서 글자가 깨져서 보일 수 있음. 꼭 넣어주기**
    - lang `<html lang="en">`: 우리 사이트에서 사용되는 주된 언어가 무엇인지 말해줌 - 검색엔진에 도움
    - og: ~ 태그(open graph) : 콘텐츠의 요약내용이 SNS에 게시되는데 최적화된 데이터로 가지고갈 수 있도록 설정 <br>
      👉og:~~ 카카오톡, 네이버, 다음 등<br>
      👉fb:~~ 페이스북 <br>
      👉twitter:~~ 트위터등등등
      <br>
- `<body>` 파트: 사용자가 볼 수 있는 content 영역<br>

  - `<div>` 태그 : division(분할, 구분) 단어에서 나옴, content 분할 요소.<br>
    **`<div>`==박스** 라고 생각하자!<br>
  - `<span>` 태그 : 짧은 text를 위한 태그
  - `<p>` 태그: 문단 (paragraph) 태그

> 🤩 **중요!** **tip!**
> **가능한 semantic 태그로 작성하자!** == 이해하기 쉬운 html 문서를 만드는 방법!
>
> - non-semantic tag : 기능은 있으나 의미는 없는 tag( `<div>`, `<span>` 등)
> - semantic 태그 == 문서를 보기만해도 그 의미를 짐작할 수 있는 tag( `<header>`, `<footer>` 등)<br>
>   ![](https://velog.velcdn.com/images/doopal2/post/4aa94b8b-0fb4-45d1-bf78-f44b8ff16117/image.png)

- `<a></a>` 태그 : anchor(닻)을 뜻함 / 다른 웹사이트로 이동<br>
  `herf` (HTTP reference / hyperlink reference) 부가정보가 필요함 == 이동할 곳 <br>
  `<a href="https://velog.io/@doopal2">두팔이 벨로그</a>`

- `<img>` 태그 : self-closing tag / `<img src="img 주소">`
  - 로컬에 있는 이미지도 사용 가능 <br>
    ▶ 같은 폴더 내에 있을 시 `<img src="파일명.확장자">`<br>
    ▶ 상위 폴더는 같으나 but 다른 폴더에 있을 시 `<img src="img 파일있는 폴더명/파일명.확장자">`<br>
- forms - ✨`<input>`태그 : 모든 웹사이트는 `<input>` 태그를 가지고 있음<br>
  매우매우 많은 유형들이 있음 - 유형마다 다른 attribute 적용 가능

      ✅ ex 1. required attribute (form - validation) 적용 화면<br>

  ![](https://velog.velcdn.com/images/doopal2/post/6dcb2433-63df-4a0c-81ac-4cf2352f42fd/image.png)<br>

      ✅ ex 2. minlength attribute (input의 최소한의 length) 적용 화면

  ![](https://velog.velcdn.com/images/doopal2/post/cd94bab0-c8d0-4b61-9643-f79bde890bfe/image.png)<br>

      ✅ ex 3. type 유형
      - email, url, file 등 값을 넣으면 원하는 유형의 정보만을 받을 수 있게 해줌

      input type="file" - (파일 확장자.pdf만 가능하게) 적용 화면

  ![](https://velog.velcdn.com/images/doopal2/post/551e1176-b4de-48d9-87b9-c92585357c6c/image.png)![](https://velog.velcdn.com/images/doopal2/post/af4686f3-7fa5-4a6c-a671-3b707aae648d/image.png)<br>

       input type="file" - (모든 이미지파일 전부 가능하게) 적용 화면

  ![](https://velog.velcdn.com/images/doopal2/post/276d153f-315b-4ade-962e-bfcc9011e67a/image.png)![](https://velog.velcdn.com/images/doopal2/post/70e319af-9a09-4549-8f1d-4c4c5e2baa4c/image.png)<br>

      ✅ ex 4. <label>태그 - input과 함께여야 작동이 됨
      label 에는 for (attribute), input 에는 id - for과 id 값이 같아야 함
      👉 Profile phto 글씨를 누르면 파일선택창이 뜸!

  ![](https://velog.velcdn.com/images/doopal2/post/3b3eb414-e3d5-49c8-94c1-1d76a343097a/image.png)![](https://velog.velcdn.com/images/doopal2/post/d9c45292-2767-4eb1-bf11-4fe925fa2f34/image.png)<br>

- ✨ 어떤 태그든 id를 가질 수 있음. <br>
  but, **element(태그) 당 오직 하나의 id만을 가질 수 있고, id 값은 유일해야 함 (unique identifier)** <br>
  👉 why? scripting / css 식별하려는 목적을 가진 것이 바로 id 이기 때문에 <br>
  <br>

- 태그 / attribute 다 외우라는 것 ❌ <br>
  mdn 같은 사이트 보면서 **어떻게 작성했는지**만 기억하면 됨<br>

> **위 작업들은 모두 사이트의 정보를 브라우저에게 알려주는 용도<br>
> 최대한 명확하게 우리의 웹사이트가 무엇인지 브라우저에게 알려주는 것**

<br/>

### 📚 참고자료

---

[강의]

- [노마드코더 - 코코아톡 클론 코딩](https://nomadcoders.co/kokoa-clone)
  _해당 강의 수강 후 정리한 내용입니다 :)_

[사이트]

- [MDN - HTML 요소 참고서](https://developer.mozilla.org/ko/docs/Web/HTML/Element)
