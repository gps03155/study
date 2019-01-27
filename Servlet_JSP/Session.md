### Session
---

<br>

>### Session

<br>

__쿠키 : 웹 브라우저에 사용자의 상태를 유지하기 위한 정보 저장__

__세션 : 웹 서버 쪽의 컨테이너에 상태를 유지하기 위한 정보 저장__

세션은 쿠키와 다르게 사용자의 정보가 서버에 저장됨

세션을 클라이언트마다 개별적으로 유지하기 위해 __HttpSession__ 객체가 생성될 때 요청을 보내온 클라이언트 정보, 요청시간 정보 등을 조합한 세션ID가 부여되며 이 세션 ID가 쿠키 기술로 저장

<br>

- __사용자의 정보를 유지__ 하기 위해 javax.servlet.http 패키지의 __HttpSession__ 인터페이스를 구현해서 사용
- 사용자의 정보를 유지하기 위해서는 __쿠키를 사용하는 것보다 세션을 사용__ 한 웹 브라우저와 웹 서버의 상태 유지가 훨씬 안정적이고 보안상의 문제 해결 가능

<br><br>

>### Session 사용 시기

<br>

- __인증 또는 로그인 정보를 유지__ 하거나 웹 애플리케이션 이용에 필요한 로그인한 사용자의 정보를 안전하게 서버에 보관할 때 사용
- 세션 ID가 클라이언트 측의 쿠키에 저장되므로 악의적인 해커가 __XSS 기법을 이용해 세션ID를 탈취 (하이재킹)__ 가능
- 탈취한 세션 ID를 이용해 해커가 __해당 사이트에 부정하게 로그인하거나 권한을 획득__ 할 수 있어 안전하다고 보기 힘듦

__보안을 위해 사용자 IP와 사용환경을 체크하거나 세션의 유효기간을 설정__

<br><br>

>### Session 속성

<br>

#### getSession()

__객체 생성__

- __HttpServletRequest__ 객체의 __getSession()__ 메소드를 이용하여 객체 생성
- __클라이언트가 가지고 있는 세션 ID와 동일한 세션 객체를 찾아서 주소값 반환__
- 세션을 생성할 때 세션이 존재하지 않으면 매개변수 create의 값이 __true, false__ 인지에 따라 다르게 동작 - getSession(boolean create)

~~~
HttpSession session = request.getSession()

1. true
세션 객체가 존재하지 않을 경우 새로운 HttpSession 객체 생성 후 반환
HttpSession session = request.getSession(true)

2. false
세션 객체가 존재하지 않을 경우 새로운 HttpSession 객체를 생성하지 않고 null 반환
HttpSession session = request.getSession(false)
~~~

<br>

#### setAttribute()

__세션 속성 설정__

- __세션의 속성 값은 객체 형태만 올 수 있음__
- session 객체는 웹 브라우저와 매핑되므로 해당 웹 브라우저를 닫지 않는 한 __같은 창에서 열려진 페이지는 모두 같은 session 객체 공유__
- session 객체의 __setAttribute()__ 메소드를 사용해서 세션의 속성을 지정하게 되면 계속 상태를 유지하는 기능 사용 가능

~~~
session.setAttribute("id", "value")
~~~

<br>

#### getAttribute()

__세션 속성 사용__

- getAttribute() 메소드는 리턴 타입이 Object 타입이므로 사용시 __실제 할당된 객체 타입으로 형변환 (Casting)__ 해야함

~~~
String id = (String) session.getAttribute("id")
~~~

<br>

#### removeAttibute()

__세션 속성 삭제__

~~~
session.removeAttribute("id")
~~~

<br>

#### invalidate()

__세션 모든 속성 삭제__

~~~
session.invalidate()
~~~
