### JSTL/EL
---

<br>

JSP 파일에 자바형식의 코드를 사용하면 불편함 점이 발생하게 되는데 EL (Expression Language)과 JSTL (Jsp Standard Tag Library)를 사용하여 코드를 간결하게 정리할 수 있음

__EL의 개념은 표현 언어를 이해하고 속성 값들을 편리하게 출력하기 위해 제공된 언어이며 JSTL은 표준 액션 태그로 처리하기 힘든 부분을 담당함__

<br><br>

>### EL (Expression Language)

<br>

- 사용 목적

__<%= %>, out.println()__ 과 같은 자바 코드를 더 이상 사용하지 않고 좀 더 간편하게 출력을 지원하기 위한 도구
(배열이나 컬렉션에서도 사용되고 Java Beans의 프로퍼티에서도 사용)

<br>

- 문법

Attribute 형식에서는 `${value}`
로 쓰고 Parameter 형식에서는 ``${param.value}`` 형식으로 사용
(값을 찾을 때 Attribute는 작은 Scope에서 큰 Scope로 찾음)

~~~
Attribute란?
메소드를 통해 저장되고 관리되는 데이터

1. Page / Request에서 사용될때
setAttribute("key", value) - 값을 넣음
getAttribute("key") - 값을 가져옴
removeAttribute("key") - 값을 지움

2. Session에섯 사용될때
set / get / remove - 동일
invalidate() - 값을 전부 지움
~~~

- paramValues나 headerValues 사용법
Values 옆에 점을 찍는 방법과 대괄호로 묶어 사용하는 2가지 방법 존재

~~~
${paramValues.boadDto[0]}   - 인덱스 0부터 시작
${paramVlues["boadDto"][1]} - 인덱스 1부터 시작
~~~

<br><br>

>### JSTL (Jsp Standard Tag Library)

<br>

- JSP는 자신만의 태그를 추가할 수 있는 기능 제공
- 연산이나 조건문의 반복분인 if문, for문, DB를 편하게 처리할 수 있음

<br>

### 태그 종류

__<%@ taglib prefix="c" uri="http://java.sum.com/jsp/jstl/core"%>__ 와 같은 형식으로 사용
(isELIgnored="false"를 추가하면 EL을 사용할 수 있음)

#### Core (prefix : c)

- 일반 프로그래밍에서 제공하는 것과 유사한 변수 선언
- 실행 흐름의 제어 기능을 제공
- 페이지 이동 기술 제공
- URI : http://java.sun.com/jsp/jstl/core

<br>

#### Formatting (prefix : fmt)

- 숫자, 날짜, 시간을 포매팅하는 기능을 제공
- 국제화, 다국어 지원 기능 제공
- URI : https://java.sun.com/jsp/jstl/fmt

<br>

#### DataBase (prefix : sql)

- DB의 데이터를 입력 / 수정 / 삭제 / 조회하는 기능을 제공
- URI : http://java.com/jsp/jstl/sql

<br>

#### XML (prefix : x)

- XML 문서를 처리할 때 필요한 기능 제공
- URI : http://java.sun.com/jsp/jstl/xml

<br>

#### Function (prefix : fn)

- 문자열을 제공하는 함수 제공
- URI : http://java.sum.com/jsp/jstl/functions

<br><br>

>### JSTL 태그 사용법

<br>

#### <c:set>

__변수를 선언하는 태그__
~~~
<c:set var="변수이름" value="값" />
~~~
- __${변수이름}으로 사용가능__
- 다른 영역에 저장하고 싶다면 `scope="session"` 추가
- 내부적으로 자바 변수로 선언되는게 아니라 page 데이터 영역의 애트리뷰트로 선언되기 때문에 __<%= 변수이름 %>__ 형태로 출력 불가

<br>

#### <c:remove>

__변수를 제거하는 태그__
~~~
<c:remove var="변수이름" /> - 모든 scope에서 제거
<c:remove var="변수이름" scope="request" /> - 해당 scope에서 제거
~~~
- 해당 이름의 변수가 사라짐
- 모든 scope에서 해당 이름을 가진 변수를 다 제거
- 특정 영역의 변수만 제고하고 싶다면 `scopr="value"` 추가

<br>

#### <c:out>

__변수 내용을 출력할 때 사용되는 태그__
~~~
<c:set var="param" value="value" />
<c:out value="${param}" escapeXml="true" />
~~~
- EL로도 출력할 수 있지만 태그가 포함된 변수를 escapeXml 항목을 true/false로 지정해서 태그를 포함해서 출력할지 적용해서 출력할지 결정할 수 있음

<br>

#### <c:if test="true/false">

__Java에서의 if문과 같음__ (test안의 내용이 true/false에 따라 내용을 출력하거나 출력하지 않음)
~~~
<c:if test="${empty value}">
  값이 비어있을 경우 처리할 로직
</c:if>
~~~
- test 부분에 EL 작성 가능

<br>

#### <c:choose>

__Java에서의 Switch문__
~~~
<c:choose>
  <c:when test="${value == 1}">
    조건에 해당할 경우의 로직
  </c:when>
  <c:otherwise>
    조건에 해당하지 않을 경우의 로직
  </c:otherwise>
</c:choose>
~~~
- switch문의 특성처럼 처음 일치하는 것만 출

<br>

#### <c:forEach>

__For문과 유사__
~~~
<c:forEach var="임시변수명" begin="1" end="10" step="1">
  ${임시변수명}
</c:forEach>

<c:forEach items=${배열이름} var="배열요소를 저장할 임시변수명">
  ${배열 요소를 저장할 임시변수 이름}
</c:forEach>
~~~

<br>

#### <c:forTokens>

__문자열에 포함된 토큰을 분리해서 각각의 토큰에 대해 반복 처리를 수행하도록 만드는 기능__
~~~
<c:forTokens items="aaa bbb ccc" var="temp" delims=" ">
  ${temp}
</c:forTokens>

<c:forTokens items="aaa!bbb&ccc" var="temp" delims="!&">
  ${temp}
</c:forTokens>
~~~
- 구분자를 여러개 넣으면 여러개 분리 가능 (하나만 가능한 것이 아님)

<br>

#### 날짜와 관련된 태그
~~~
<fmt:formatDate value="<%= new Date() $>" type="both"/>
~~~
- 날짜와 시간을 모두 출력
- type에 date, time 둘 중 하나를 쓰면 하나만 나오게 됨

<br>

#### 숫자와 관련된 태그

~~~
<fmt:formatNumber value="12345678" groupingUsed="true"/>
<fmt:formatNumber value="3.141592" pattern="#.##"/>
~~~
- 세자리마다 끊어서 쉼표 출력
- 지정한 자리까지 소수점 출력 가능
