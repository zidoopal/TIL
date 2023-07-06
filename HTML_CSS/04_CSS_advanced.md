> CSS 심화 - 모든 내용 기재 X 중요하다고 생각되는 내용만 메모메모 📝<br>

<br/>

## Transition

변화할 속성을 일정시간에 걸쳐서 서서히 나타나도록 할 때 사용한다

```CSS
selector {
	transition: 속성 / 시간 / 방식
}
```

- 속성(property) : 트랜지션을 적용할 속성 이름, 전부 적용시 `all`, <br>
  개별적으로 복수의 프로퍼티의 지정하는 경우 쉼표로 구분한다.<br>

```css
ex)
transition: color 1s ease-in-out, background-color 3s ease-in-out;
```

- 시간(duration) : 효과가 나타나는데 걸리는 시간, 기본 값 0s
- 방식(timing-function) : 트랜지션 효과

| 프로퍼티 값   | 효과                                                    |
| ------------- | ------------------------------------------------------- |
| ease (기본값) | 느리게 시작 ▶ 점점 빨라짐 ▶ 느려지면서 종료             |
| lenear        | 시작부터 ▶ 종료까지 속도 일정                           |
| ease-in       | 느리게 시작 ▶ 일정한 속도에 다다르면 종료까지 속도 일정 |
| ease-out      | 일정한 속도의 등속으로 시작 ▶ 점점 느려지며 종료        |
| ease-in-out   | ease와 비슷하게 느리게 시작 ▶ 느려지면서 종료           |

- cubic-bezier(0, 0, 0, 0); 으로 직접 transition 설정을 할 수 있음.

> 💡 **💡 💡 중요 ❗ ❗ ❗ **

- **transition 은 state(:hover, :active, :focus 등)가 없는 요소에 붙여야 한다.**<br>
  root(처음 생긴 곳, 근원)에 써줘야만 변화하고 돌아오는 과정을 거친다.<br>
  >
- **바뀌었으면 하는 속성들(color, border 등등-)은 state에도 꼭 써져있어야 한다.**<br>
  root에 있던 속성들 ▶ state에 있는 속성들로 바뀌는 것이므로!<br>

<br/>

## Transform

CSS로 2D는 물론, 3D까지 할 수 있어! BOOYA~🤩 <br>
Transform 안에는 엄청나게 많은 기능들이 있다.<br>

- transform 은 일종의 '3D transformation' 임! <br>
  이러한 이유로, margin, padding이 적용되지 않고, <br>
  다른 box element, 이미지 등에 영향을 끼치지 않는다(변형시키지 않는다). <br>
  다른 요소의 box를 변형시키지 않고 원하는 요소를 이동시키기 위해서 사용하는 것이다.
  - transform 은 페이지의 픽셀의 다른 부분에서 일어난다.
  - transform 은 box차원에서 일어나지 않는다.
- CSS의 3D는 GPU로 돌아간다 즉 3D작업을 할 수 있다
- transition 과 transform 을 합치면 아름다운 애니메이션을 만들 수 있다 🤩

> 🎈 **tip**<br>
> border-radius: 50% ▶ **원이 된다 !** 🤪

<br/>

## Animations - @keyframes

:hover 처럼 내가 마우스를 올려놓지 않아도 CSS에서 진짜 애니메이션을 구현할 수 있다?! 🙄

- 작성방법

(1) from {} ~ to {}

```css
@keyframes 애니메이션이름 {
  from (== 0%) {
    transform: css-styles;
  }
  to (== 100%) {
    transform: css-styles;
  }
}
```

(2) 0% {} ~ 100% {} (여러 개의 프레임 작성 가능)

```css
@keyframes 애니메이션이름 {
  0% {
    transform: css-styles;
  }
  25% {
    transform: css-styles;
  }
  75% {
    transform: css-styles;
  }
  100% {
    transform: css-styles;
  }
}
```

- 무한으로 반복되게 하려면 뒤에 infinite를 붙여준다.
- 꼭 transform만 써야하는 건 아니지만, transform을 쓰는걸 권한다. <br>
  (일부 property는 애니매이션이 잘 안되기 때문에)

> 📌 **transition VS animation 차이**
>
> transition 속성과 animation 속성은 플래시의 기술이나 <br>
> 자바스크립트의 도움 없이 요소에 직접 애니메이션 효과를 적용하는 속성이다.<br>
>
> transition 속성은 요소의 상태가 변해야 애니메이션을 실행한다.<br>
>
> animation 속성은 요소의 모양과 동작을 키프레임 단위로 변경할 수 있다.<br>
> 키프레임 동작은 재생 횟수, 재생 방향등 여러 애니메이션 속성으로 제어할 수 있다.<br>
>
> transition 속성과 animation 속성의 가장 큰 차이는 <br>
> transition 속성은 요소의 상태가 바뀌어야 바뀌는 상태를 애니메이션으로 표현하지만,<br>
> animation 속성은 요소의 상태 변화와 상관 없이 애니메이션을 실행한다.<br>
> 또한 @keyframes 속성으로 프레임을 추가할 수 있다.<br>

<br/>

### 📚 참고자료

---

[강의]

- [노마드코더 - 코코아톡 클론 코딩](https://nomadcoders.co/kokoa-clone)
  _해당 강의 수강 후 정리한 내용입니다 :)_<br>

[사이트]

- [mdn - CSS > transform] https://developer.mozilla.org/ko/docs/Web/CSS/transform
- [mdn - CSS > transition] https://developer.mozilla.org/ko/docs/Web/CSS/transition
- [mdn - CSS > animation] https://developer.mozilla.org/ko/docs/Web/CSS/animation <br>

[블로그]

- CSS 애니메이션(Animation), 키프레임(keyframes) https://webclub.tistory.com/621<br>

[✨ animation 효과 사이트 추천]

1. https://matthewlein.com/tools/ceaser
2. https://cubic-bezier.com/
