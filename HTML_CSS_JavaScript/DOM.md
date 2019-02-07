### DOM
---

<br>

>### 문서 객체 모델(DOM) 이란?

<br>

문서 객체 모델(DOM, Document Object Model)은 __XML이나 HTML 문서에 접근하기 위한 일종의 인터페이스__

문서 내의 모든 요소를 정의하고 각각의 요소에 접근하는 방법 제공

DOM은 W3C의 표준 객체 모델이며 계층 구조로 표현

<br>

#### DOM의 종류

W3C DOM 표준은 세가지 모델로 구분

- Core DOM : 모든 문서 타입을 위한 DOM 모델
- HTML DOM : HTML 문서를 위한 DOM 모델
- XML DOM : XML 문서를 위한 DOM 모델

~~~
1. HTML DOM
HTML 문서를 조작하고 접근하는 표준화된 방법을 정의
모든 HTML 요소는 HTML DOM을 통해 접근 가능

2. XML DOM
XML 문서에 접근하여 그 문서를 다루는 표준화된 방법을 정의
모든 XML 요소는 XML DOM을 통해 접근 가능
~~~

<br><br>

>#### Document 객체

<br>

__Document 객체는 웹 페이지 그 자체를 의미하며 웹 페이지에 존재하는 HTML 요소에 접근하고자 할 때는 반드시 Document 객체부터 시작해야함__

<br>

#### Document 메소드
Document 객체는 HTML 요소와 관련된 작업을 도와주는 다양한 메소드 제공

- HTML 요소의 선택
- HTML 요소의 생성
- HTML 이벤트 핸들러 추가
- HTML 객체의 선택

<br>

- HTML 요소 선택

메소드 | 설명
--- | ---
__document.getElementsByTagName(태그이름)__ | 해당 태그 이름의 요소를 모두 선택함
__document.getElementById(아이디)__ | 해당 아이디의 요소를 선택함
__document.getElementsByClassName(클래스이름)__ | 해당 클래스에 속한 요소를 모두 선택함
__document.getElementByName(name속성값)__ | 해당 name 속성값을 가지는 요소를 모두 선택함
__document.querySelectorAll(선택자)__ | 해당 선택자로 선택되는 요소를 모두 선택함

<br>

- HTML 요소 생성

메소드 | 설명
--- | ---
__document.createElement(HTML요소)__ | 지정된 HTML 요소를 생성함
__document.write(텍스트)__ | HTML 출력 스트림을 통해 텍스트를 출력함

<br>

- HTML 이벤트 핸들러 추가

메소드 | 설명
--- | ---
__document.getElementById(아이디).onclick = function(){실행할 코드}__ | 마우스 클릭 이벤트와 연결될 이벤트 핸들러 코드를 추가함

<br><br>

>### DOM 요소

<br>

HTML 요소를 다루기 위해서는 해당 요소를 선택해야함

- HTML 태그 이름(tag name) : `getElementsByTagName()`
~~~
var selectedItem = document.getElementsByTagName("li");
~~~

<br>

- ID : `getElementById()`
id를 이용항 선택은 해당 아이디를 가지고 있는 요소 중에서 첫번째 요소 단 하나만을 선택(여러 요소를 선택하고 싶을 때는 태그 이름이나 클래스와 같은 방법 사용)
~~~
var selectedItem = document.getElementById("id");
~~~

<br>

- class : `getElementsByClassName()`
~~~
var selectedItem = document.getElementsByClassName("class name");
~~~

<br>

- name 속성(attribute) : `getElementByName()`
~~~
var selectedItem = document.getElementsByName("name");
~~~

<br>

- CSS 선택자(selector) : `querySelectorAll()`
CSS 선택자(id, class, 속성, 속성 값 등)을 이용하여 HTML 요소를 선택
~~~
var selectedItem = document.querySeletorAll("li.odd");
~~~

<br>

- HTML 객체 집합 (object collection)
HTML DOM에서 제공하는 객체 집합(object collection)을 이용하여 HTML 요소 선택
~~~
var title = document.title; // title 요소 선택
~~~
