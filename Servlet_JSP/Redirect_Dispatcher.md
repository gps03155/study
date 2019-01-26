### Redirect vs Dispatcher
---

<br>

서블릿에서는 __특정 URL이나 페이지로 이동하게 하는 두 가지 방식을 제공__

Redirect와 Dispatcher의 차이점을 알고 사용해야함

둘 다 다른 웹 페이지로 이동하지만 행동 형태가 다름

<br><br>

>### __Redirect__

<br>

- Web Container는 Redirect 명령이 들어오면 __웹 브라우저에게 다른 페이지로 이동하라고 명령__ 을 내림
- 웹 브라우저는 __URL을 지시된 주소로 바꾸고 그 주소로 이동__
- 다른 웹 컨테이너에 있는 주소로 이동이 가능
- __새로운 페이지에서는 request와 response 객체가 새롭게 생성__

<br>

#### sendRedirect()
- 새로운 페이지로 완전히 이동하기 때문에 __기존 데이터를 하나도 사용할 수 없음__
- 서블릿에서 request영역에 공유한 속성 값에 접근할 수 없음

~~~
response.sendRedirect("join.jsp")
~~~

<br><br>

>### __Dispatcher__

<br>

- Web Container 차원에서 __페이지 이동만 있음__
- 실제로 웹 브라우저는 다른 페이지로 이동했음을 알 수 없음
- 웹 브라우저에서는 __최초에 호출한 URL이 표시되고 이동한 페이지의 URL 정보는 볼 수 없음__
- 동일한 컨테이너에 있는 페이지로만 이동 가능
- 현재 실행중인 페이지와 forward에 의해 호출될 페이지는 __request와 response 객체를 공유__

<br>

#### forward()
- forward()는 __클라이언트가 요청하면서 전송한 데이터를 그대로 유지__

~~~
RequestDispatcher dispatcher = request.getRequestDispatcher("join.jsp")

dispatcher.forward(request, response);
~~~

<br><br>

>### __Redirect와 Dispatcher 차이점__

<br>

redirect 방식 | dispatcher 방식 (forward)
--- | ---
응답시 클라이언트에게 요청할 url을 알려주어 다시 요청하는 방식 __url?test=xxx 처럼 GET 방식처럼 파라미터를 넘김__ (받을 때는 request.getParameter()) | __request의 attribute 객체를 실어나를 수 있음__ request.setAttribute("name")
URL 형식으로 경로 지정 (./test.jsp) | 동일한 webcontent의 JSP/Servlet에게만 전달 가능 (한 webcontent안에서의 jsp와 servlet만 찾아감) - /write_form.jsp
요청 URL이 변경되서 나옴 | 요청 URL이 변경되지 않음
