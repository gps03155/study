### WebApplication
---

<br>

>### __웹 애플리케이션이란?__

<br>

- 톰캣과 같은 서버를 서블릿 컨테이너라 지칭함
- __서블릿 컨테이너가 담아서 관리하는 것__
- 서블릿 컨테이너는 웹 애플리케이션이 Servlet/JSP에 따라서 동작하는 것을 보장해야함

<br><br>

>### __웹 애플리케이션의 구성 요소__

<br>

Java에서의 웹 애플리케이션은 다음과 같은 파일들로 구성

<br>

- HTML, Image, CSS, JavaScript
- JSP
- Servlet
- Java Class, Java Archarive File (.jar)
- web.xml

<br>

구성 요소 중 위치해야 할 디렉토리가 정해진 요소 존재

<br>

- WEB-INF/classes
  - Servlet
  - Java Clase

<br>

- WEB-INF/lib
  - Java Archarive File (.jar)

<br>

- WEB-INF
  - web.xml

<br><br>

>### __웹 애플리케이션 디렉토리__

<br>

- 톰캣에서 웹 애플리케이션의 디폴트 위치는 CATALINA_HOME/webapps
- 새로운 웹 애플리케이션을 추가하고자 한다면 CATALINA_HOME/webapps 바로 아래 서브 디렉토리를 만들고 아래의 폴더를 만들어야 함

<br>

### WEB-INF

- 웹 애플리케이션 배치 정의자, __web.xml__ 이 존재
- WEB-INF 디렉토리 안에 있는 파일은 웹 브라우절르 통해 직접 접근 가능

<br>

### WEB-INF/classes

- 서블릿을 포함한 자바 클래스 파일이 위치

<br>

### WEB-INF/lib

- Java Archarive File (.jar) 파일이 위치

<br>

똑같은 바이트 코드가 WEB-INF/classes과 WEB-INF/lib 안의 Java Archarive File 안에 동시에 있을 수 있다는 점에 유의해야함

이런 경우, 톰캣 클래스 로더는 먼저 검색하는  WEB-INF/classes를 뒤져서 클래스를 찾아 메모리에 로딩

해당하는 클래스를 찾으면 WEB-INF/lib에 있는 클래스는 무시

<br>

~~~
톰캣 클래스 로더

톰캣의 클래스 로더는 환경변수 CLASSPATH를 참조하지 않음
아래의 순서대로 클래스를 찾음

1. 자바 코어 라이브러리
2. 웹 애플리케이션 WEB-INF/classes
3. 웹 애플리케이션 WEB-INF/lib
4. CATALINA_HOME/lib
~~~

<br><br>

>### __배치 정의자 (Deployment Descriptor) : web.xml__

<br>

- 웹 애플리케이션에서는 배치 정의자라고 불리는 web.xml파일이 가장 중요
- WEB-INF 디렉토리에 위치
- web.xml은 웹 애플리케이션의 모든 설정 정보를 담고 있음

<br>

### 배치 정의자로 할 수 있는 주요 설정 항목

- 서블릿컨텍스트 초기화 파라미터
- 필터
- 리스터
- Servlet 정의
- Servlet 초기화 파라미터
- Servlet 매핑
- session 설정
- welcome 파일 리스트
- 에러 페이지

<br>

### web.xml 내에서의 Servlet Mapping

~~~
<servlet>
  <servlet-name>서블릿클래스명</servlet-name>
  <servlet-class>패키지명.서블릿클래스명</servlet-class>
</servlet>

<servlet-mapping>
  <servlet-name>서블릿클래스명</servlet-name>
  <url-pattern>/서블릿을 나타낼 수 있는 단어</url-pattern>
</servlet-mapping>
~~~

<br><br>

>### __Packing__

<br>

웹 애플리케이션은 jar 툴로 하나의 파일로 만들 수 있으며 이러한 파일은 다양한 서블릿 컨테이너에서 작동할 수 있음

개발이 완료 되었다면 웹 애플리케이션을 bundle화하여 다른 서블릿 컨테이너에 배포를 할 수 있음

배포를 하기 위해 웹 애플리케이션의 root 디렉토리에서 확장자가 __war__ 인 파일을 만들어야 함

생성된 .war 파일은 다른 톰캣서버나 다른 벤더의 서블릿 컨테이너의 디폴트 웹 애플리케이션 폴더에 복사만 하면 해당 서블릿 컨테이너가 자동으로 애플리케이션을 배치하고 로드함
