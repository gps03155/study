### JavaScript
---

<br>

>### 자바스크립트(JavaScript)란?

<br>

__자바 스크립트(JavaScript)는 객체(object) 기반의 스크립트 언어__

_HTML로는 웹의 내용을 작성하고, CSS로는 웹을 디자인하며, 자바스크립트로는 웹의 동작을 구현할 수 있음_

- 자바스크립트는 주로 웹 브라우저에서 사용되나 Node.js와 같은 프레임워크를 사용하면 서버측 프로그래밍에서도 사용할 수 있음
- 대부분의 웹 브라우저에는 자바스크립트 인터프리터가 내장되어 있음

<br>

#### 웹 프로그래밍에서 할 수 있는 일

- HTML의 __내용__ 변경 가능
- HTML의 __속성__ 변경 가능
- HTML의 __스타일__ 변경 가능

<br><br>

>### 자바스크립트의 특징

<br>

- 자바스크립트는 객에 기반의 스크립트 언어
- 자바스크립트는 동적이며 타입을 명시할 필요가 없는 인터프리터 언어 (컴파일 작업을 거치지 않고 소스 코드를 바로 실행할 수 있는 언어)
- 자바스크립트는 객체지향형 프로그래밍과 함수형 프로그래밍을 모두 표현

<br><br>

>### 자바스크립트 출력

<br>

자바스크립트는 여럽 방법을 통해 결과물을 HTML 페이지에 출력할 수 있음

- `window.alert()` 메소드
- HTML DOM 요소를 이용한 `innerHTML` 프로퍼티
- `document.write()` 메소드
- `console.log()` 메소드

<br>

#### window.alert()

 __브라우저와는 별도의 대화 상자를 띄워 사용자에게 데이터를 전달__

- 자바스크립트에서 가장 간단하게 데이터를 출력할 수 있는 방법
- window 객체의 모든 메소드나 프로퍼티르 사용할 때는 window라는 접두사 생략 가능

~~~
<script>
  alert("alert 창 띄우기");
</script>
~~~

<br>

#### HTML DOM 요소를 이용한 innerHTML 프로퍼티

__HTML 요소의 내용(content)이나 속성(attribute) 값 등을 손쉽게 변경__

- document 객체의 `getElementById()`나 `getElementsByTagName()` 등의 메소드를 이용

~~~
<script>
  var str = document.getElementById("text");

  str.innerHTML = "문장 변경";
</script>
~~~

<br>

#### document.write()

__웹 페이지가 로딩될 때 실행되면 웹 페이지에 가장 먼저 데이터를 출력__

- 대부분 테스트나 디버깅을 위해 사용
- 웹 페이지의 모든 내용이 로딩된 후 `document.write()` 메소드가 실행되면 웹 페이지 내에 먼저 로딩된 모든 데이터를 지우고 자신의 데이터 출력
- 테스트 이외의 용도로 사용할 때는 주의해서 사용해야함

~~~
<script>
  document.write(4 * 5);
</script>

<button onclick="document.write(4*5)">버튼</button>
~~~

<br>

#### console.log()

__웹 브라우저의 콘솔을 통해 데이터 출력__

- F12를 누른 후 콘솔 화면에 내용 출력
- 콘솔 화면을 통한 데이터의 출력은 좀 더 자세한 사항까지 출력되므로 디버깅하는데 많은 도움을 줌

~~~
<script>
  console.log(4*5);
</script>
~~~

<br><br>

>### 자바스크립트를 적용하는 방법

<br>

- 내부 자바스크립트 코드로 적용
- 외부 자바스크립트 파일로 적용

<br>

#### 내부 자바스크립트 코드

__<script> 태그를 사용하여 HTML 문서 안에 삽입__

- HTML 문서의 `<head>` 태그나 `<body>` 태그에 위치할 수 있지만 `<head>`에 위치하는 것이 좋음

~~~
<script>
  document.getElementById("text").innerHTML = "내부 코드";
</script>
~~~

<br>

#### 외부 자바스크립트 파일

__외부 파일로 생성하여 삽입__

- 외부에 작성된 자바스크립트 파일은 .js 확장자를 사용하여 저장
- 자바스크립트 파일을 적용하고 싶은 웹 페이지에 <script> 태그를 사용해 외부 자바스크립트 파일을 포함하면 됨
- 웹 내용을 담당하는 HTML 코드로부터 웹 동작을 구현하는 자바스크립트 코드 분리 가능
- HTML 코드와 자바스크립트 코드를 읽기도 편해지며 유지보수 용이
- 웹 브라우저가 미리 읽어 올 수 있어 웹 페이지의 로딩 속도 빨라짐

~~~
<head>
  <script src="examples/example.js">
  </script>
</head>
~~~
