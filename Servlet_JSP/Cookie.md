### Cookie
---

<br>

>### Cookie

<br>

__쿠키는 서버가 클라이언트에 저장하는 정보__ 로써 클라이언트와 연결이 끊어져도 클라이언트에 저장된 정보가 유지되어 서버에 재방문할 때 요청정보의 헤더 안에 포함되어 서버로 전달

<br>

#### 언제 사용하는가?

- 이전에 방문한 적이 있는 웹서버에 다시 방문했을 때 몇번째 방문인지
- 비로인자가 쇼핑몰에서 주문할 때까지 장바구니에 선택한 상품 정보들을 유지
- 포탈 사이트에서 클라이언트가 특별히 관심있어하는 항목에 대한 정보 유지
- 자동 로그인을 허용할 경우

<br><br>

>### 쿠키 생성 및 사용

<br>

__쿠키는 이름, 값, 유효기간, 도메인, 경로__ 등으로 이루어져 있으며 쿠키의 이름과 값이 가장 중요한 요소임

<br>

- 쿠키 생성

~~~
Cookie cookie = new Cookie("key", "value")

cookie.setMaxAge(24 * 60 * 60) // 시, 분 초 - 쿠키의 유효시간
cookie.setPath("/") // 쿠키의 유효한 디렉토리 설정

response.addCookie(cookie) // 클라이언트 응답에 쿠키 추가
~~~

<br>

- 쿠키에 저장된 정보 읽기

~~~
Cookie[] cookies = request.getCookies()  // request로부터 쿠키 가져오기

for(Cookie cookie : cookies){
  cookie.getName() // 쿠키의 이름을 가져옴
  cookie.getValue() // 쿠키의 값을 가져옴
}
~~~

<br>

- 설정된 쿠키 모두 삭제

~~~
Cookie[] cookies = request.getCookies() // request로부터 쿠키 가져오기

for(Cookie cookie : cookies){
  cookie.setMaxAge(0) // 쿠키의 유효시간 만료 - 특정 쿠키를 더 이상 사용하지 못하게 함

  response.addCookie(cookie) // 해당 쿠키를 response에 추가
}
~~~

<br><br>

>### Cookie의 사용 순서

<br>

JSP에서 쿠키를 사용하려면 javax.servlet.http 패키지에 있는 cookie 클래스의 객체를 생성해야함 (쿠키에는 각각의 웹 브라우저를 판별할 수 있는 정보가 포함)

- 쿠키는 웹 서버가 웹 브라우저의 요청에 응답할 때 __response 객체에 실려서 사용자의 웹 브라우저에 저장__

- 웹 브라우저에 저장된 쿠키는 사용자가 다시 웹 서버에 요청을 할 때 request 객체에 실려서 다시 웹 서버에 전달 (웹 서버는 전달된 쿠키의 값을 읽어서 같은 웹 브라우저로부터 온 요청인지를 판별)

- 웹 서버는 각각의 웹 브라우저와의 상태를 지속시킬 수 있음
