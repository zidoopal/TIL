> **어이 정규식이**<br/>
> 죄송 (참을 수가 없었음)<br/>

![](https://velog.velcdn.com/images/doopal2/post/ab978cc2-480b-48f7-8b98-2ee76710680e/image.png)<br/>

# 📌 정규 표현식

정규 표현식, 또는 정규식(🙄)은 **문자열에서 특정 문자 조합을 찾기 위한 패턴**

<br/>

## ✔ 정규 표현식 만들기

> - **리터럴 방식**

```javascript
const re = /ab+c/;
```

정규 표현식 리터럴은 스크립트를 불러올 때 컴파일되므로, <br/>
바뀔 일이 없는 패턴의 경우 리터럴을 사용하면 성능이 향상될 수 있다<br/>

> - **`RegExp` 생성자 방식**

```javascript
const re = new RegExp('ab+c');
```

생성자 함수를 사용하면 정규 표현식이 런타임에 컴파일된다.<br/>
바뀔 수 있는 패턴이나, 사용자 입력 등 외부 출처에서 가져오는 패턴의 경우 위와 같이 사용.<br/>

<br/>

## ✔ 정규 표현식 메서드

자바스크립트에서는 **정규 표현식도 객체**이다 🤪<br/>
**`RegExp`**의 메서드 **`exec()`**, **`test()`** 뿐만 아니라<br/>
**`String`** 의 메서드와도 함께 사용할 수 있다. (**`match()`**, **`replace()`**..등등)<br/>
메서드를 이용하여 패턴을 검사하고, 매칭되는 문자열을 추출 / 변환한다.<br/>

- **`/정규표현식/.exec(문자열)`**

  - 문자열에서 정규표현식에 매치되는 항목들을 '배열'로 반환 / 일치하는 값이 없을 시, `null` 반환.
  - `/g` (global)옵션을 넣어놔도 일치하는 첫 번째 값만 반환한다 - `match() 와의 차이점`<br/>
    (But, 캡쳐 값이 있다면 배열로 반환)
    <br>

- **`/정규표현식/.test(문자열)`**

  - 문자열이 정규표현식과 일치하면 true, 아니면 false 반환
    <br>

- **`문자열.match(/정규표현식/)`**

  - 문자열에서 정규표현식에 매치되는 항목들을 '배열'로 반환
    <br>

- **`문자열.search(/정규표현식/)`**

  - 문자열에서 정규표현식에 해당하는 항목들의 '인덱스'를 반환
    <br>

- **`문자열.replace(/정규표현식/, 대체문자열)`**

  - 문자열에서 정규표현식에 해당하는 항목을 '대체문자열'로 변환
    <br>

- **`문자열.split(/정규표현식/)`**
  - 문자열에서 정규표현식에 해당하는 항목으로 쪼개어 배열로 반환
    <br>

## ✔ 정규식 플래그

정규식을 생성할 때 고급 검색을 위한 전역 옵션을 설정할 수 있도록 지원하는 기능

| 플래그 | 설명                                                                           |
| ------ | ------------------------------------------------------------------------------ |
| g      | 전역 탐색 (모든 결과가 배열로 반환, g 플래그 없이는 최초에 발견된 문자만 반환) |
| i      | 대/소문자 구분❌                                                               |
| m      | (==Multi Line) 여러줄에 걸쳐 탐색 (여러 줄 필터링 시 사용)                     |
| u      | (==unicode) 유니코드 전체 지원                                                 |
| s      | `.` 을 `\n` (줄 바꿈 문자) 까지 일치시킴                                       |
| y      | ‘sticky’ 모드(문자 내 특정 위치에서 검색) 활성화                               |

 <br>

## ✔ 정규식 기호

### 📦 그룹 , 레인지 (Groups and ranges)

| 기호 | 설명                                               |
| ---- | -------------------------------------------------- |
| \|   | 또는 (OR)                                          |
| ( )  | 그룹                                               |
| [ ]  | 괄호안의 어떤 문자든 하나라도 만족하는 것을 찾아줌 |
|      | /abc/ == 'abc'를 포함하는                          |
|      | /[abc]/ == 'a' 또는 'b'또는 'c'                    |
|      |                                                    |
|      |                                                    |
| [^]  | 부정 문자셋 ([^a-zA-Z] a~zA~Z 제외하고)            |
| ?=   | 앞쪽 일치                                          |
| ?!   | negative 앞쪽 일치                                 |
| ?<=  | 뒤쪽 일치                                          |
| ?<!  | negative 뒤쪽 일치                                 |

<br/>

### 🧮 수량 (quantifiers)

| 기호      | 설명                                               |
| --------- | -------------------------------------------------- |
| ?         | 있거나 없거나 (zero or one)                        |
| \*        | == {0, } / 없거나 있거나 많거나 (zero or more)     |
| \*?       | == {0} / 없거나, 있거나 and 없거나, 최대 한 개     |
| +         | == {1, } / 하나 또는 많이 (one or more)            |
| +?        | == {1} / 최소 한 개, 있거나 and 없거나, 최대 한 개 |
| {n}       | n개                                                |
| {min,}    | 최소                                               |
| {min,max} | 최소, 그리고 최대                                  |

<br/>

### 🔎 단어 경계 (Boundary-type)

| 기호 | 설명                                  |
| ---- | ------------------------------------- |
| `\`b | 단어 경계                             |
| `\`B | (`\`b와 반대로 작용) 단어 경계가 아님 |
| ^    | 문장의 시작                           |
| $    | 문장의 끝                             |

> ex) `\b` 와 `\B` 사용

```javascript
<Ya YA ya YaYaYa Ya>
```

- `/\b/Ya/g` <span style="color:#A0A0A0"><span style="background-color:#B5F9C0">Ya</span> YA ya <span style="background-color:#B5F9C0">Ya</span>YaYa <span style="background-color:#B5F9C0"> Ya </span></span>
  > <br>
- `/Ya\b/g` <span style="color:#A0A0A0"><span style="background-color:#B5F9C0">Ya</span> YA ya YaYa<span style="background-color:#B5F9C0">Ya</span> <span style="background-color:#B5F9C0">Ya</span></span>
  > <br>
- `/\B/Ya/g` <span style="color:#A0A0A0">Ya YA ya Ya<span style="background-color:#B5F9C0">YaYa</span> Ya</span>
  > <br>
- `/Ya\B/g` <span style="color:#A0A0A0">Ya YA ya <span style="background-color:#B5F9C0">YaYa</span>Ya Ya</span>

<br/>

### 📑 문자 (Character classes)

| 기호       | 설명                                                                     |
| ---------- | ------------------------------------------------------------------------ |
| `.`        | (개행 문자`\n` 제외) 모든 문자열 - 숫자, 한글, 영어, 특수기호, 공백 포함 |
| `\`d       | 숫자                                                                     |
| `\`D       | negative `\d`                                                            |
| `\`w       | word (== `[A-Za-z0-9_(밑줄 포함)]`)                                      |
| `\`W       | negative `\w`                                                            |
| `\`s       | 공백                                                                     |
| `\`S       | negative `\s`                                                            |
| a-zA-Z     | 모든 알파벳                                                              |
| ㄱ-ㅎ가-힣 | 모든 한글                                                                |
| 0-9        | 0~9                                                                      |

<br/>

> #### 🧙‍♂️ 많이 사용하는 정규 표현식
>
> [[javascript] 자주 사용하는 정규 표현식 (Regular Expression) 정리] https://hitomis.tistory.com/68

<br/>

### 📚 참고

---

[동영상]

- [Youtube - 드림코딩 : 정규표현식 , 더이상 미루지 말자 🤩](https://www.youtube.com/watch?v=t3M6toIflyQ)

[사이트]

- [mdn - 정규 표현식] (https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Regular_expressions)
- [코어 자바스크립트 - 패턴과 플래그] (https://ko.javascript.info/regexp-introduction)

[블로그]

- [📚 JavaScript 정규 표현식 문법 총정리 + 응용 예제](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-%EC%A0%95%EA%B7%9C%EC%8B%9D-RegExp-%EB%88%84%EA%B5%AC%EB%82%98-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%89%BD%EA%B2%8C-%EC%A0%95%EB%A6%AC)
