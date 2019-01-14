### Hibernate vs MyBatis
---

<br>

~~~
우리나라는 대부분 MyBatis를 사용
비즈니스가 매우 복잡하고 안정성을 중요시하는 서비스일 경우 JPA보다 SQL을 작성하는 것이 좋을 것이라는 의견 존재
SQL을 쓰던 기존 애플리케이션을 JPA로 바꾸는 일이 쉽지 않아 우리나라에서 Hibernate가 뜨지 못하고 있음

JPA는 통계 쿼리처럼 복잡한 SQL을 수행하기 힘들기 때문에 비즈니스에 따라 MyBatis를 사용할지 Hibernate를 사용할지 선택해야함
~~~

<br><br>

>### __JDBC (Java Database Connectivity)__

<br>

- DB에 접근할 수 있도록 Java에서 제공하는 API
- 모든 Java의 Data Access 기술의 근간
- 모든 Persistence Framework는 내부적으로 JDBC API 이용
- __JDBC는 데이터베이스에서 자료를 쿼리하거나 업데이트하는 방법 제공__

<br><br>

>### __JPA (Java Persistent API)__

<br>

- 자바 ORM 기술에 대한 API 표준 명세로 Java에서 제공하는 API
- ORM을 사용하기 위한 표준 인터페이스를 모아둔 것
- 사용자가 원하는 JPA 구현체를 선택해서 사용할 수 있음

<br>

- JPA 구성요소
  - javax.persistance 패키지로 정의된 API 그 자체
  - JPQL (Java Persisstence Query Language)
  - 객체/관제 메타데이터

<br><br>

>### __Hibernate__

<br>

- JPA의 구현체 중 하나
- SQL을 직접 사용하지 않는다고 해서 JDBC API를 사용하지 않는것은 아님
Hibernate가 지원하는 메서드 내부에서는 JDBC API가 동작하고 있음
- HQL (Hibernate Query Language)라 불리는 매우 강력한 쿼리 언어 포함

<br>

~~~
장점
1. 생산성
2. 유지보수
3. 특정 벤더에 종속적이지 않음

단점
1. 성능
2. 세밀함
3. 러닝커브
~~~

<br>

- 장점
  - 객체지향적으로 데이터를 관리할 수 있기 때문에 비즈니스 로직에 집중할 수 있으며 객체지향 개발이 가능
  - 테이블 생성, 변경, 관리가 쉬움
  - 로직을 쿼리에 집중하기 보다는 객체 자체에 집중할 수 있음
  - 빠른 개발 가능

<br>

- 단점
  - 잘 이해하고 사용하지 않으면 데이터 손실 (Persistence Context)
  - 성능상 문제 존재 가능성

<br><br>

>### __MyBatis__

<br>

- 개발자가 지정한 SQL, 저장 프로시저, 몇가지 고급 매핑을 지원하는 SQL Mapper
- JDBC로 처리하는 상당 부분의 코드와 파라미터 설정 및 결과 매핑을 대신 해줌

<br>

- 장점
  - SQL에 대한 모든 컨트롤을 하고자 할때 적합
  - SQL 쿼리들이 매우 잘 최적화되어 있을 때 유용

<br>

- 단점
  - 애플리케이션과 데이터베이스 간의 섥에 대한 모든 조작을 하고자 할때 적합하지 않음
