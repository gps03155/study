### XMLHttpRequest
---

<br>

_Ajax에서 XMLHttpRequest 객체는 웹 브라우저가 서버와 데이터를 교환할 때 사용_
(웹 브라우저가 백그라운드에서 서버와 통신할 수 있도록 함)

<br>

>### XMLHttpRequest 객체의 생성

<br>

__XMLHttpRequest 객체를 생성하는 방법은 브라우저의 종류에 따라 나뉘어짐__

- XMLHttpRequest 객체
  - 익스플로러 7 이상, chrome, firefox, safari, opera
~~~
var 변수이름 = new XMLHttpRequest();
~~~
- ActiveXObject 객체
  - 익스플로러 구형 버전 (5, 6)
~~~
var 변수이름 = new ActiveXObject("Microsoft.XMLHTTP");
~~~

<br>

모든 웹 브라우저에서 XMLHttpRequest 인스턴스를 제대로 생성하기 위해서는 아래와 같이 작성

~~~
var httpRequest;

function createRequest(){
  if(window.XMLHttpRequest){
    // 익스플로러 7 이상, chrome, firefox, safari, opera
  }
  else {
    // 익스플로러 6 이하
    return new ActivXObject("Microsoft.XMLHTTP");
  }
}
~~~

<br><br>

>### 서버와 통신

<br>

#### 서버에 요청(request)하기

Ajax에서는 XMLHttpRequest 객체를 사용하여 서버와 데이터 교환

- 서버에 요청을 보내기 위해서는 XMLHttpRequest 인스턴스 생성
- XMLHttpRequest 인스턴스의 `open()` 메소드와 `send()` 메소드를 사용하여 요청을 보냄

<br>

##### open()
서버로 보낼 Ajax 요청의 형식 설정
`open(전달 방식, URL 주소, 동기여부)`

- 전달 방식 : GET / POST 방식 중 하나 선택
- URL 주소 : 요청을 처리할 서버의 파일 주소 전달
- 동기 여부 : 요청을 동기식으로 전달할지 비동기식으로 전달할지 결정

<br>

##### send()
작성된 Ajax 요청을 서버로 전달
(전달 방식에 따라 인수를 가질수도 안가질수도 있음)

~~~
send();      // GET
send(문자열); // POST
~~~

<br><br>

#### GET 방식과 POST 방식

__Ajax에서는 주로 GET 방식보다 POST 방식을 사용하여 요청 전송__

##### GET 방식

- 주소에 데이터(data)를 추가하여 전달하는 방식
- HTTP 요청은 브라우저에 의해 캐시되어(cached) 저장
- 보통 쿼리 문자열(query string)에 포함되어 전송되므로 길이의 제한이 있음
- 보안상 취약점이 존재하므로 중요한 데이터는 POST 방식을 사용하여 요청하는 것이 좋음

~~~
// GET 방식으로 요청을 보내면서 데이터를 동시에 전달함
// 서버로 전송하고자 하는 데이터는 URI에 포함되어 전송
httpRequest.open("GET", "/examples/request_ajax.php?city=seoul&zipcode=06141", true);
httpRequest.send();

// XMLHttpRequest 객체의 현재 상태와 서버상의 문서 존재 유무 확인
if(httpRequest.readySate == XMLHttpRequest.DONE && httpRequest.status == 200){
  ...
}

readyState => XMLHttpRequest.DONE (서버에 요청한 데이터의 처리가 완료되어 응답할 준비 완료)
status => 200 (요청한 문서가 서버상에 존재)
~~~

<br>

##### POST 방식

- 데이터(data)를 별도로 첨부하여 전달하는 방식
- HTTP요청은 브라우저에 의해 캐시되지 않으므로 브라우저 히스토리에도 남지 않음
- HTTP 요청에 의한 데이터는 쿼리 문자열과 별도로 전송
- 데이터의 길이에 대한 제한이 없으며 GET 방식보다 보안성이 높음

~~~
// POST 방식의 요청은 데이터를 Http 헤더에 포함시켜 전송
// sendRequestHeader() 메소드를 이용하여 먼저 헤더 작성 후 send() 메소드로 데이터 전송
httpRequest.open("POST", /examples/request_ajax.php", true);
httpRequest.setRequestHeader("Content-Type", "application/x-www-form-urlencoded");
httpRequest.send("city=seoul&zipcode=06141");
~~~

<br>

##### 비동기식(Asynchronous) 요청

__서버에 비동기식 요청을 보내기 위해서 open() 메소드의 세번쨰 인수로 true 전달__

_서버로 비동기식 요청을 보내면 자바스크립트는 서버로부터의 응답을 기다리면서 동시에 다른 일을 할 수 있게 됨_

- open() 메소드의 세번째 인수로 false를 전달하면 서버에 동기식 요청을 보내게 됨
- 자바스크립트는 서버로부터 응답이 도착할 때까지 대기
- 사용자는 대기하는 동안 다른 어떤 작업도 할 수 없음

<br><br>

#### 서버로부터의 응답(response) 확인

서버로부터의 응답을 확인하기 위해 사용하는 XMLHttpRequest 객체의 프로퍼티 3가지

- readyState 프로퍼티
- status 프로퍼티
- onreadystatechange 프로퍼티

<br>

##### readyState 프로퍼티

__XMLHttpRequest 객체의 현재 상태를 나타냄__

readyState 프로퍼티의 값은 객체의 현재 상태에 따라 변화

- UNSENT (숫자 0) : XMLHttpRequest 객체 생성
- OPENED (숫자 1) : open() 메소드가 성공적으로 실행
- HEADERS_RECEIVED (숫자 2) : 모든 요청에 대한 응답 도착
- LOADING (숫자 3) : 요청한 데이터 처리중
- DONE (숫자 4) : 요청한 데이터의 처리가 완료되어 응답할 준비가 완료

<br>

##### status 프로퍼티

__서버의 문서 상태__

- 200 : 서버에 문서가 존재
- 404 : 서버에 문서가 존재하지 않음

<br>

##### onreadystatechange 프로퍼티

__XMLHttpRequest 객체의 readyState 프로퍼티 값이 변할 때마다 자동으로 호출되는 함수를 설정__

서버에서 응답이 도착할 때까지 readyState 프로퍼티 값의 변화에 따라 총 5번 호출
(서버에 요청한 데이터가 존재하고 서버로부터 응답이 도착하는 순간을 특정할 수 있음)
