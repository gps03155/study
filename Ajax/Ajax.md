### Ajax
---

<br>

_Ajax는 웹 페이지 전체를 다시 로딩하지 않고도 웹 페이지의 일부분만을 갱신할 수 있게 해줌 (백그라운드 영역에서 서버와 통신하여 그 결과를 웹 페이지의 일부분에만 표시)_

<br>

>### Ajax (Asynchronous Javascript And XML)란?

<br>

__빠르게 동작하는 동적인 웹 페이지를 만들기 위한 개발 기법__

- __웹 페이지 전체를 다시 로딩하지 않고도 웹 페이지의 일부분만을 갱신할 수 있음__
- 백그라운드 영역에서 서버와 통신하여 그 결과를 웹 페이지의 일부분에만 표시
- 서버와 다양한 형태의 데이터를 주고 받을 수 있음
  - JSON
  - XML
  - HTML
  - 텍스트 파일 등

#### Ajax의 장점

- 웹 페이지 전체를 다시 로딩하지 않고도 웹 페이지의 일부분만을 갱신할 수 있음
- 웹 페이지가 로드된 후에 서버로 데이터 요청을 보낼 수 있음
- 웹 페이지가 로드된 후에 서버로부터 데이터를 받을 수 있음
- 백그라운드 영역에서 서버로 데이터를 보낼 수 있음

<br>

#### Ajax의 한계

- Ajax는 클라이언트가 서버에 데이터를 요청하는 클라이언트 풀링 방식을 사용하므로 서버 푸시 방식의 실시간 서비스는 만들 수 없음
- Ajax로는 바이너리 데이터르 보내거나 받을 수 없음
- Ajax 스크립트가 포함된 서버가 아닌 다른 서버로 Ajax 요청을 보낼 수 없음
- 클라이언트의 PC로 Ajax 요청을 보낼 수 없음

~~~
클라이언트 풀링 방식 (Client Pooling)
사용자가 직접 원하는 정보를 서버에게 요청하여 얻는 방식

서버 푸시 방식 (Server Push)
사용자가 요청하지 않아도 서버가 알아서 자동으로 특정 정보를 제공하는 것을 의미
~~~

<br>

#### Ajax 프레임워크

Ajax를 이용하여 개발을 쉽게 할 수 있도록 미리 여러 가지 기능을 포함해 놓은 개발 환경

- Prototype
- script.aculo.us
- dojo
- jQuery

<br><br>

>### Ajax 동작 원리

<br>

#### Ajax 구성 요소

_Ajax는 기존에 사용되던 여러 기술을 함꼐 사용하여 웹 페이지의 일부분만을 갱신할 수 있도록 해주는 개발 기법_

- 웹 페이지의 표현을 위한 HTML과 CSS
- 데이터에 접근하거나 화면 구성을 동적으로 조작하기 위해 사용되는 DOM 모델
- 데이터의 교환을 위한 JSON이나 XML
- 웹 서버와의 비동기식 통신을 위한 XMLHttpRequest 객체
- 사용자의 작업 흐름을 제어하는데 사용되는 자바스크립트

<br>

#### Ajax 동작 원리

__Ajax를 이용한 웹 응용 프로그램은 자바스크립트 코드를 통해 웹 서버와 통신__
(사용자의 동작에는 영향을 주지 않으면서도 백그라운드에서 지속해서 서버와 통신)

1. 사용자에 의한 요청 이벤트 발생
2. 요청 이벤트가 발생하면 이벤트 핸들러에 의해 자바스크립트가 호출
3. 자바스크립트는 XMLHttpRequest 객체를 사용하여 서버로 요청 전송
(웹 브라우저는 요청을 보내고 나서 서버의 응답을 기다릴 필요 없이 다른 작업 처리 가능)
4. 서버는 전달받은 XMLHttpRequest 객체를 가지고 Ajax 요청을 처리
5. 서버는 처리한 결과를 HTML, XML, JSON 형태의 데이터로 웹 브라우저에 전달
(새로운 페이지를 전부 보내는 것이 아니라 필요한 데이터만을 전달)
6. 서버로부터 전달받은 데이터를 가지고 웹 페이지의 일부분만을 갱신하는 자바스크립트 호출
7. 웹 페이지의 일부분만이 다시 로딩되어 표시
