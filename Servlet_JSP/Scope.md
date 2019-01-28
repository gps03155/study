### Scope
---

<br>

>### 객체 범위 종류

<br>

웹 애플리케이션에서는 4개의 객체 범위가 존재
(__page, reqeust, session, application__)

#### page → request → session → application 순으로 탐색

<br>

- __애트리뷰트명은 좁은 범위 영역부터 넓은 범위의 영역으로 탐색__
- 탐색이 된다면 더이상 큰 범위로 탐색을 진행하지 않음

<br><br>

>### page

<br>

__하나의 JSP 페이지 내에서만 객체를 공유하는 영역__ (JSP only)

<br>

- 한번의 브라우저 요청이 오면 하나의 JSP 페이지가 호출
- JSP 파일에는 __pageContext__ 가 내장되어 있으며 __page 영역에서만 유효__
- JSP 파일의 __<% %>__ 안에 변수를 사용하면 이 변수는 해당 JSP 파일 내에서만 유효

<br>

~~~
1. 데이터 저장
<%
  pageContext.setAttribute("id", value)
%>

2. 데이터 가져오기
${pageScope.id}
~~~

<br><br>

>### request

<br>

__요청을 받아서 응답하기까지 객체가 유효한 영역__

<br>

- __forward__ 또는 include를 사용하면 request 기본 객체가 공유되어서 request 영역이 됨
- Servlet에서 JSP로 객체를 보낼 때 주로 사용하는 방법

<br>

~~~
1. 데이터 저장
request.setAttribute("id", value")

2. 데이터 가져오기
requestScope.id
~~~

<br><br>

>### session

<br>

__같은 브라우저 내에서 요청되는 페이지들은 같은 객체를 공유__

<br>

- __하나의 브라우저 당 1개의 session 객체__ 가 생성
- 세션이 종료되면 반환
- __request.getSession()__ 메소드를 호출하여 세션 영역에서 유효한 객체를 얻을 수 있음

<br>

~~~
1. 데이터 저장
HttpSession session = request.getSession()

session.setAttribute("id", value);

2. 데이터 가져오기
${sessionScope.id}
~~~

<br><br>

>### application

<br>

__같은 애플리케이션 내에서 요청되는 페이지들은 같은 객체를 공유__

<br>

- 하나의 애플리케이션당 1개의 application 객체 생성
- 애플리케이션이 종료되면 반환
- __request.getServletContext()__ 메소드를 호출하여 애플리케이션 영역에서 유효한 객체를 얻을 수 있음

<br>

~~~
1. 데이터 저장
ServletContext context = request.getServletContext()

context.setAttribute("id", values)

2. 데이터 가져오기
${applicationScope.id}
~~~
