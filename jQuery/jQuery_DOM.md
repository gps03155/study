### jQuery DOM
---

<br>

_jQuery에는 요소 및 속성에 쉽게 액세스하고 조작할 수 있도록 하는 DOM 관련 메소드 제공_

~~~
DOM = 문서 객체 모델 (Document Object Model)

DOM은 HTML 및 XML 문서에 액세스하기 위한 표준을 정의

W3C DOM은 프로그램 및 스크립트가 문서의 내용, 구조 및 스타일을 동적으로 액세스하고 업데이트 할 수 있게 해주는 플랫폼 및 언어 중립적 인터페이스
~~~

<br>

>### Content

<br>

- `text()` - 선택한 요소의 텍스트 내용을 설정하거나 반환
- `html()` - 선택된 요소의 내용을 설정하거나 반환
- `val()` - form 필드의 값을 설정하거나 반환

<br>

#### Content 가져오기

~~~
1. text()
$("#test").text();

2. html()
$("#test").html();

3. val()
$("#test").val();
~~~

<br>

#### Content 설정

~~~
1. text()
$("#test").text("hello world"); // 태그 적용되지 않음

2. html()
$("#test").html("<b>hello world</b>"); // 태그 적용

3. val()
$("#test").val("hello world");
~~~

<br><br>

>### Attribute

<br>

- `attr()` - 속성 값 설정 / 변경하는데 사용

<br>

#### Attribute 가져오기

~~~
// 링크에서 href 속성 값 가져오기
$("#test").attr("href");
~~~

<br>

#### Attribute 설정

~~~
// 링크에서 href 속성의 값을 설정
$("#test").attr("href", "https://www.google.com");

여러 속성 동시에 설정
$("#test").attr({
  "href": "https://www.google.com",
  "title": "google homepage"
});
~~~

<br><br>

>### Element

<br>

#### Element 추가

- `append()` - 선택한 요소의 끝에 내용 삽입
- `prepend()` - 선택한 요소의 시작 부분에 내용 삽입
- `after()` - 선택한 요소 뒤에 내용 삽입
- `before()` - 선택한 요소 앞에 내용 삽입

<br>

~~~
1. append()
$("p").append("append text");
$("p").append(str1, str2, str3....); // 여러 요소 추가

2. prepend()
$("p").prepend("prepend text");
$("p").prepend(str1, str2, str3....); // 여러 요소 추가

3. after()
$("img").after("text after");
$("img").after(str1, str2, str3....); // 여러 요소 추가

4. before()
$("img").before("text before");
$("img").before(str1, str2, str3....); // 여러 요소 추가
~~~

<br>

#### Element 삭제

- `reover()` - 선택된 요소 및 자식 요소 제거
- `empty()` - 선택한 요소에서 자식 요소 제거

<br>

~~~
1. remove()
$("#div").remove();
$("p").remove(".test"); // class="test"인 모든 <p> 요소 삭제
$("p").remove(".test, .demo"); // class="test" or class="demo"인 모든 <p> 요소 삭제

2. empty()
$("#div").empty();
~~~

<br><br>

>### css

<br>

- `addClass()` - 선택한 요소에 하나 이상의 클래스 추가
- `removeClass()` - 선택한 요소에서 하나 이상의 클래스 제거
- `toggleClass()` - 선택한 요소에서 클래스 추가 / 제거 토글
- `css()` - 스타일 속성을 설정하거나 반환

<br>

~~~
1. addClass()
$("div").addClass("blue");

2. removeClass()
$("h1, h2, p").removeClass("blue");

3. toggleClass()
$("h1, h2, p").toggleClass("blue");

4. css()
// CSS 속성 반환 - css("propertyname");
$("p").css("background-color");

// CSS 속성 설정 - css("propertyname", "value");
$("p").css("background-color", "yellow");
~~~
