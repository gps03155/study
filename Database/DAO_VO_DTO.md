### DAO vs DTO vs VO
---

<br>

>### DAO

<br>

__데이터를 처리하는 클래스__

<br>

- Data Access Object의 약자료 __DB의 data에 접근하기 위한 객체__
- DB 접근을 하기 위한 로직과 비즈니스 로직을 분리하기 위해 사용
- DAO의 경우 DB와 연결할 Connection까지 설정되어 있는 경우가 많음
- MyBatis 등을 사용할 경우 커넥션 풀까지 제공되고 있기 때문에 DAO를 별도로 만드는 경우는 드뭄

<br><br>

>### DTO

<br>

__인스턴스 개념 : 데이터를 처리하고 전송할 수 있는 클래스 (getter/setter)__

<br>

- Data Transfer Object의 약자로 __계층간 데이터 교환을 위한 자바빈즈를 의미__
- 계층간 의미는 __Controller, View, Business Layer, Persistent Layer__ 등을 의미하며 각 계층간 데이터 교환을 위한 객체를 의미
- DTO는 __로직을 가지지 않는 순수한 데이터 객체이고 getter, setter 메소드만 가진 클래스를 의미__

<br><br>

>### VO

<br>

__리터럴 값 개념 : 데이터만 저장된 클래스 (getter)__

<br>

- Value Object의 약자로 __DTO와 혼용해서 쓰임__
- VO는 값 오브젝트로써 __값을 위해 쓰임__
- 자바는 값 타입을 표현하기 위해 불변 클래스를 만들어서 사용하는데 불변이라는 것은 __readOnly__ 특징을 가짐
- __중간에 값을 바꿀 수 없고 새로 만들어야 한다는 특징 존재__
(getter 기능만이 존재)

<br><br>

>### DTO vs VO

<br>

#### 공통점

- 넣어진 데이터를 getter를 통해 사용

<br>

#### 차이점

- __DTO__
  - 가변의 성격을 가진 클래스 (setter)

<br>

- __VO__
  - 불변의 성격을 가진 클래스 (getter만 사용)
