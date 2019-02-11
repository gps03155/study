### JQuery
---

<br>

_jQuery의 목적은 웹 사이트에서 JavaScript를 훨씬 쉽게 사용하도록 만드는 것_

<br>

>### jQuery란?

<br>

__웹 사이트에서 JavaScript를 훨씬 쉽게 사용하도록 만드는 것__

- JavaScript 라이브러리
- 여러 줄의 JavaScript 코드를 필요로 하는 일반적인 작업을 수행하며 한 줄의 코드로 호출할 수 있는 메소드로 래핑
- AJAX 호출 및 DOM 조작과 같은 JavaScript의 복잡한 작업을 간소화

<br>

#### jQuery 라이브러리 기능

- HTML / DOM 조작
- CSS 조작
- HTML 이벤트 메소드
- 효과 및 애니메이션
- AJAX

<br><br>

>### jQuery 사용

<br>

#### jQuery 버전

- 개발 버전 (uncompressed) - 테스트 및 개발용 (압축되지 않고 읽을 수 있는 코드)
- 릴리즈 버전 (compressed)

~~~
1. jquery 파일 직접 다운로드

<head>
  <script src="jquery-3.3.1.js"></script>
</head>

2. jQuery CDN
jQuery를 직접 다운로드하지 않고 CDN (Content Delivery Network)에서 포함

// Google CDN
<head>
  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
</head>

// Microsoft CDN
<head>
  <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.3.1.min.js"></script>
</head>
~~~

<br><br>

>### jQuery 구문

<br>

__jQuery를 사용하면 HTML 요소를 선택하고 해당 요소에 작업을 수행할 수 있음__

- `$(selector)`
jQuery는 CSS 구문을 사용하여 요소를 선택

~~~
$(this).hide() - 현재 요소를 숨김
$("p").hide() - 모든 <p> 요소를 숨김
$(".test").hide() - class = "test"인 모든 요소를 숨김
$("#test").hide() - id = "test"인 요소를 숨김
~~~

- $(document).ready()
HTML이 완전히 로드되고 실행할 수 있도록 함 (window.onload와 유사한 기능)
~~~
$(document).ready(function(){
    // jQuery 구문 작성
});

$(function(){
  // jQuery 구문 작성
});
~~~

<br><br>

>### jQuery Selector

<br>

__jQuery 셀렉터를 사용하면 HTML 요소를 선택하고 조작할 수 있음__

_jQuery의 모든 선택자는 달러 기호와 괄호로 시작 : $()_

- 이름, id, class, 유형, 속성, 속성 값 등을 기반으로 HTML 요소를 찾거나 선택
- __기존의 CSS 셀렉터를 기반__ 으로 하며 사용자 정의 셀렉터 존재

<br>

#### 요소 선택기

__태그 이름을 기반으로 요소 선택__

~~~
// 페이지의 모든 <p> 요소 선택

$("p")
~~~

<br>

#### id 셀렉터

__HTML 태그의 id 속성을 사용하여 특정 요소를 찾음__

- id는 페이지 내에서 고유해야하므로 단일 고유 요소를 찾으려는 경우 사용
- 특정 id를 가진 요소를 찾으려면 HTML 요소의 id 다음에 #문자 사용

~~~
// id가 test인 요소를 찾음

$("#test")
~~~

<br>

#### .class 셀렉터

__특정 클래스가 있는 요소를 찾음__

- 특정 클래스가 있는 요소를 찾으려면 마침표를 쓰고 클래스 이름 입력

~~~
// class가 test인 요소를 찾음

$(".test")
~~~
