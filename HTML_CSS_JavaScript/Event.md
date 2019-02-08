### Event
---

<br>

>### 이벤트(Event)란?

<br>

__웹 브라우저가 알려주는 HTML 요소에 대한 사건의 발생을 의미__

- 웹 페이지에 사용된 자바스크립트는 발생한 이벤트에 반응하여 특정 동작을 수행
- 클라이언트 측 자바스크립트를 비동기식 이벤트 중심(event-driven)의 프로그래밍 모델이라고 함

<br>

#### 이벤트 타입(event type)

__발생한 이벤트의 종류를 나타내는 문자열로 이벤트 명(event name)__ 이라고 함

- 키보드, 마우스, HTML DOM, Window 객체 등을 처리하는 이벤트가 폭넓게 제공됨

<br>

#### 이벤트 명세(event specification)

과거와는 달리 새로운 이벤트들이 빠르게 늘어남에 따라 이벤트를 위한 명세가 3가지로 나누어짐

- DOM Level3 이벤트 명세
- HTML5 관련 이벤트 명세
- 모바일 장치를 위한 이벤트 명세

<br><br>

>### 이벤트 리스너 (Event Listener)

<br>

__이벤트가 발생했을 때 그 처리를 담당하는 함수를 가리키며 이벤트 핸들러(Event Handler)라고도 함__

지정된 타입의 이벤트가 특정 요소에서 발생하면 웹 브라우저는 그 요소에 등록된 이벤트 리스너를 실행 시킴

<br>

#### 이벤트 리스터 등록

작성된 이벤트 리스너는 먼저 해당 객체나 요소에 등록되어야만 호출 가능

- 이벤트의 대상이 되는 객체나 요소에 프로퍼티로 등록
- 객체나 요소의 메소드에 이벤트 리스너를 전달

<br>

#### 객체나 요소에 프로퍼티로 등록하는 방법

- 자바스크립트 코드에서 프로퍼티로 등록 :
거의 모든 브라우저가 대부분의 이벤트 타입을 지원
(단점 : 이벤트 타입별로 오직 하나의 이벤트 리스너만을 등록할 수 있음)

~~~
window.onload = function(){
  var text = document.getElementById("text");

  text.innerHTML = "HTML 문서 로드"
}

// window.onload : HTML 문서가 로드될 때 실행
~~~

<br>

- HTML 태그에 속성으로 등록 : HTML 코드에 자바스크립트 코드가 추가됨으로써 가독성이 안좋아지며 유지보수가 힘들어짐

~~~
<p onclick="alert("alert 창 띄우기")">클릭</p>
~~~

<br><br>

#### 객체나 요소의 메소드에 이벤트 리스너를 전달하는 방법

- `addEventListener()`
거의 모든 브라우저에서 지원하는 이벤트 리스너 등록을 위한 메소드
(하나의 객체에 여러 개의 이벤트 리스너 등록 가능)

~~~
대상객체.addEventListener(이벤트명, 실행할 이벤트 리스너, 이벤트 전파방식)

1. 이벤트 명
이벤트 리스너를 등록할 이벤트 타입을 문자열로 전달

2. 실행할 이벤트 리스너
지정된 이벤트가 발생했을 때 실행할 이벤트 리스너 전달

3. 이벤트 전파 방식
false명 버블링(bubbling) 방식으로, true면 캡처링(capturing) 방식으로 이벤트 전파


var showBtn = document.getElementById("btn");

showBtn.addEventListener("click", showText); // 선택한 요소에 click 이벤트 리스너 등록
~~~

- `attachEvent()`
`addEventListener()` 메소드는 익스플로러8과 그 이전 버전, 오페라 6과 그 이전 버전에서는 지원하지 않으므로 `attachEvent()` 메소드와 `detachEvent()` 메소드를 사용해야함

<br><br>

#### 이벤트 리스너 삭제

- `removeEventListener()`
등록된 이벤트 리스너 삭제 가능

~~~
btn.removeEventListener("mouseover", mouseroverBtn);
~~~
