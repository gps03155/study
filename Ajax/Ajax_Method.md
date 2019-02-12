### Ajax Methos
---

<br>

_Ajax를 이용하여 개발을 손쉽게 할 수 있도록 미리 여러가지 기능을 포함해 놓은 개발 환경을 Ajax 프레임워크라고 함_
(현재 가장 널리 사용되고 있는 Ajax 프레임워크는 jQuery)

>### $.ajax()

<br>

__HTTP 요청을 만드는 직관적인 방법을 제공__
(모든 jQuery Ajax 메소드의 핵심이 되는 메소드)

~~~
$.ajax([option]);
~~~

- URL 주소 : 클라이언트가 HTTP 요청을 보낼 서버의 주소
- option : HTTP 요청을 구성하는 키와 값의 쌍으로 구성되는 헤더의 집합

~~~
$.ajax({
  url: "/examples/request_ajax.php", // 클라이언트가 요청을 보낼 서버의 URL 주소
  data: {name: "홍길동"},             // HTTP 요청과 함께 서버로 보낼 데이터
  type: "GET",                        // HTTP 요청 방식 (GET, POST)
  dataType: "json"                    // 서버에서 보내줄 데이터의 타입
});
~~~

<br><br>

>### $.get()

<br>

__서버에 GET 방식의 HTTP 요청을 보낼 수 있음__

~~~
$.get(URL주소, [콜백함수]);
~~~

- URL 주소 : 클라이언트가 HTTP 요청을 보낼 서버의 주소
- 콜백 함수 : HTTP 요청이 성공했을 때 실행할 함수

~~~
$(function(){
  $("#requestBtn").on("click", function(){
    // GET 방식으로 서버에 HTTP 요청을 보냄
    $.get("/examples/jquery_ajax_data.txt", function(data, status){
        // 전송받은 데이터와 전송 성공 여부 보여줌
        $("#text").html(data + status);
      });
    });
});
~~~

<br><br>

>### $.post()

<br>

__서버에 POST 방식의 HTTP 요청을 보낼 수 있음__

~~~
$.post(URL 주소, [데이터], [콜백함수]);
~~~

- URL 주소 : 클라이언트가 HTTP 요청을 보낼 서버의 주소
- 데이터 : HTTP 요청과 함께 서버로 보낼 데이터를 전달
- 콜백 함수 : HTTP 요청이 성공했을 때 실행할 함수 정의

~~~
$(function(){
  $("#requestBtn").on("click", function(){
    // POST 방식으로 서버에 HTTP 요청을 보냄
    // 서버가 필요한 정보를 같이 보냄
    $.post("/examples/request_ajax.php", {name:"이순신", grade:"A+", function(data, status){
        // 전송받은 데이터와 전송 성공 여부 보여줌
        $("#text").html(data + status);
      });
    });
});
~~~

<br><br>

>### load()

<br>

__서버에서 데이터를 읽어 들인 후에 해당 HTML 코드를 선택한 요소에 배치__
(선택자를 URL 주소와 함께 전송하면 읽어들인 HTML 코드 중에서 선택자와 일치하는 요소만을 배치)

~~~
$(function(){
  $("#request").on("click", function(){
      // URL 주소에 존재하는 HTML 코드를 읽은 후에 id가 "list"인 요소에 배치
      $("#list").load("/examples/jquery.html");
    });
});
~~~

- load() 메소드의 인수로 URL 주소와 함께 선택자를 전달할 때는 하나의 문자열로 전송
- URL 주소와 선택자는 띄어쓰기로 구분

~~~
// test.txt를 읽어 들여 id가 box인 요소 안에 배치
$("#box").load("test.txt");
~~~

<br><br>

메소드 | 설명
--- | ---
$.ajax() | 비동기식 Ajax를 이용하여 HTTP 요청을 전송
$.get | 전달받은 주소로 GET 방식의 HTTP 요청을 전송
$.post | 전달받은 주소로 POST 방식의 HTTP 요청을 전송
$.getScript | 웹 페이지에 스크립트를 추가
$.getJSON | 전달받은 주소로 GET 방식의 HTTP 요청을 전송하여 응답으로 JSON 파일을 전송받음
load() | 서버에서 데이터를 읽은 후 읽어들인 HTML 코드를 선택한 요소에 배치
