# 이벤트 핸들러 Event handler

## 이벤트 핸들러?

이벤트가 발생했을 때 호출될 함수

함수를 언제 호출할 지 알 수 없으므로 브라우저에게 함수 호출을 위임.

## 이벤트 핸들러 등록

브라우저에게 이벤트 핸들러의 호출을 위임하는 것

### 어트리뷰트 방식

```jsx
<button onclick = "click('me')">Click me</button>

function onclick(event) {
	click(event);
}
```

- on + 이벤트 종류를 나타내는 이벤트 타입 (ex. onclick)
- 함수참조가 아닌 함수호출문 등 문을 할당
- 값: 암묵적으로 생성될 이벤트 핸들러의 함수 몸체
- 따라서 이벤트 객체를 전달받기 위해선 이벤트 핸들러의 첫 매개변수 이름이 무조건 event여야 함
- HTML과 JS는 관심사가 다르므로 분리하는 것이 좋기 때문에 사용하지 않는 것을 권장
- CBD방식의 Angular/React/Svelte/Vue.js 같은 프레임워크/라이브러리는 이벤트핸들러 어트리뷰트 방식으로 처리함. 뷰 구성요소로 보기때문에 HTML,CSS,JS 관심사가 같다고 봄.

### 프로퍼티 방식

```jsx
$button.onclick = () => {
	console.log('click')
}
```

이벤트타깃.on+이벤트타입 = 이벤트핸들러

- 이벤트를 발생시킬 이벤트 타겟 or 전파된 이벤트를 캐치할 DOM에 이벤트 핸들러를 바인딩
- 이벤트 핸들러 프로퍼티에 하나의 이벤트 핸들러만 바인딩가능

### addEventListener 메서드 방식

```jsx
$button.addEventListener('click', () => {
	console.log('click')
}
```

- DOM LEVEL2 도입
- 접두사 on을 붙이지 않음
- 이벤트 핸들러를 인수로 전달

## 이벤트 핸들러 제거

```jsx
$butoon.removeEventListener('click', handleClick)
```

- 전달된 인수가 일치하지 않으면 이벤트 핸들러가 제거되지 않음
- 따라서 무명함수는 제거할 수 없음
- argument.callee로 제거할 수 있지만 코드최적화를 방해하므로 가급적 변수나 자료구조에 저장하여 제거하는 것을 추천
- 프로퍼티 방식으로 등록한 이벤트 핸들러는 해당 메서드로 제거 불가