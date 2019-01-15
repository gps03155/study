### Join
---

<br>

>### __조인 (Join)__

<br>

- __하나 이상의 테이블로부터 연관된 데이터를 검색해 오는 방법__

<br>

- __Primary Key (PK)와 Foreign Key (FK) 값의 연관에 의해 Join이 성립__

(논리적인 값들의 연관으로만 성립 가능)

<br>

- __Join의 기본 유형__
  - __Equi Join__ : = (equal) 연산자를 사용하는 조인
  - __Inner Join__ : 조인 조건을 만족하는 행에 대해서만 결과값이 나오는 조인
  - __Outter Join__ : 조인 조건을 만족하지 않아도 출력이 가능해야 하는 결과를 얻고자 할 때 사용

<br><br>

>### __Equi Join__

<br>

- 컬럼에 있는 값들이 정확히 일치하는 경우에 __=__ 연산자를 사용해서 조인
- 일반적으로 PK-FK 관계에 의하여 Join이 성립
- Where절 혹은 on 절을 이용
- 액세스 효율을 향상시키고 좀 더 명확히 하기 위해 칼럼 이름 앞에 테이블 이름을 밝힘
- 같은 이름의 칼럼이 조인 대상 테이블에 존재하면 반드시 컬럼 이름 앞에 테이블 이름을 밝혀주어야 함
- Join을 위한 테이블이 n개라고 하면 join을 위한 __최소한의 = 조건은 n-1__

<br>

~~~
select 테이블명.컬럼명, 테이블명.컬럼명 ...
from 테이블1, 테이블2
where 테이블1.컬럼1 = 테이블2.컬럼2

select employees.emp_no, titles.emp_no, titles.title
from employees, titles
where employees.emp_no = titles.emp_no;
~~~

<br>

Equi Join을 사용했을 경우 테이블이 Join하면서 Join 조건에 사용했던 컬럼이 2개 생김
__테이블1.컬럼, 테이블2.컬럼__ 이 생기게 됨

<br><br>

>### __Cartesian Join__

<br>

- Join에 대한 조건이 생략되거나 잘못 기술되어 한 테이블에 있는 모든 행들이 다른 테이블에 있는 모든 행들과 Join이 되어서 얻어진 경우

- Cartesian Product를 얻지 않기 위해서 반드시 where절을 써줘야함


<br><br>

>### __Natural Join__

<br>

- __두 테이블 공통 칼럼이 있는 경우 별다른 조인 조건 없이 공통 칼럼처럼 묵시적으로 조인이 되는 유형__

<br>

~~~
select emp_no, title
from employees natural join titles
~~~

<br>

### Join ~ Using

- Natural Join의 문제점

조인하고자 하는 두 테이블에 같은 이름의 칼럼이 많을 때 __특정한 칼럼으로만 조인하고 싶다면 using 절__ 을 사용해서 기술

(같은 이름의 컬럼이 두 테이블에 존재해야함)

<br>

~~~
select employees.emp_no, titles.title
from employees join titles using(emp_no)
~~~

<br>

### Join ~ On

- __공통된 이름의 칼럼이 없는 경우__ 가장 보편적으로 사용할 수 있는 유형

- Where 정레 일반 조건만 쓸 수 있게 하고 조인 조건은 on에 두어 보다 의미를 명확히 하고 알아보기 쉬움

<br>

~~~
select employees.emp_no, titles.title
from employees join titles on (employees.emp_no = titles.emp_no)
~~~

<br><br>

>### __Outer Join__

<br>

- 조인하는 여러 테이블에서 한 쪽에는 데이터가 있고 한 쪽에는 데이터가 없는 경우, 데이터가 있는 쪽 테이블의 내용을 전부 출력하는 방법

<br>

- __조인 조건에 만족하지 않아도 해당 행을 출력하고 싶을 때 사용__

<br>

- __Left Outer Join, Right Outer Join, Full Outer Join__

<br>

### Left Outer Join

조인문의 __왼쪽에 있는 테이블의 모든 결과__ 를 가져온 후 오른쪽 테이블을 매칭하고, 매칭되는 데이터가 없는 경우 NULL을 표시함

<br>

~~~
select *
from employee left outer join department on employee.departmentid = department.departmentid
~~~

<br>

### Right Outer Join

조인문의 __오른쪽에 있는 테이블의 모든 결과__ 를 가져온 후 왼쪽의 테이블의 데이터를 매칭하고, 매칭되는 데이터가 없는 경우 NULL을 표시함

<br>

~~~
select *
from employee right outer join department on employee.departmentid = department.departmentid
~~~

<br>

### Full Outer Join

__Left Outer Join과 Right Outer Join을 합친 것__

양쪽 모두 조건이 일치하지 않는 것들까지 모두 결합하여 출력

<br>

~~~
select *
from employee full outer join department on employee.departmentid = department.departmentid


MySQL에서는 Full Outer Join 키워드가 안되므로 밑의 방법으로 사용

select *
from employee left outer join department on employee.departmentid = department.departmentid
union
select *
from employee right outer join department on employee.department = department.departmentid
~~~

<br>

MySQL에서는 __UNION__ 명령어 사용

<br><br>

>### __Self Join__

<br>

- __테이블에서 자기 자신을 조인__

<br>

~~~
select e1.emp_no, e1.ename, e2.emp_no, e2.ename, e2.job
from emp e1 join emp e2 on e1.job = e2.job
~~~
