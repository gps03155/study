## Java 8 : Stream
---

_Java8에서 새롭게 추가된 기능 - java.util.stream_

`배열 또는 Collection 인스턴스 함수에 여러 개를 조합해서 원하는 결과를 필터링하고 가공된 결과 도출`


- ### Stream 정의
  - 자바 8에 추가된 API로 자료구조들을 선언적으로 다루는 역할을 함
  - 함수형 인터페이스를 사용하여 병렬식 처리 가능
  - lambda를 사용하여 코드의 양을 줄이고 간결하게 표현 가능

<br><br>

- ### Stream 사용 순서
1. stream 인스턴스 생성
2. filtering, mapping, grouping 등 원하는 결과 만들기

`전체 -> mapping -> filtering / grouping -> 결과`

<br><br>

- ### Grouping
  - List 형식으로 되어있는 데이터를 java에서 그룹화 시킬 경우
  - SQL에서 `group by`와 유사
  - `List<Object, List<Object>>`의 타입으로 리턴

<br><br>

ex) 부서를 부서 번호로 그룹화
```
List<HashMap> deptList = deptMapper.selectList();

// [{dept_no : 1, dept_name : 기획부}, {dept_no : 2, dept_name : 영업부}.....]

---
stream을 이용한 Grouping
---

List<Long, List<HashMap>> deptGrouping = deptList.stream().collect(Collectors.groupingby(m->m.get(dept_no)));

// [1=[{dept_no : 1, dept_name : 기획부}], 2=[{dept_no : 2, dept_name : 영업부}]....]
```

stream을 이용하여 grouping을 하면 `for`문을 실행한 것과 동일
(내부적으로 반복문을 돔)

이러한 성질을 이용하면 __성능시 문제가 될 수 있는 중첩 for문 제거 가능__

```
List<HashMap> employeeList = empMapper.selectList();

// [{emp_no : 1, emp_name : kim, dept_no : 1}, {emp_no : 2, emp_name : park, dept_no : 2}...]

List<HashMap> deptList = deptMapper.selectList();

// [{dept_no : 1, dept_name : 기획부}, {dept_no : 2, dept_name : 영업부}...]

---
중첩 for
--

for(HashMap empMap : employeeList){
  for(HashMap deptMap : deptList){
    if(empMap.get("dept_no").equals(deptMap.get("dept_no"))){
      System.out.println("same dept");
    }
  }
}
```

해당 코드의 문제점은 같은 부서를 비교하기 위해 __중첩 `for`__ 문을 사용함으로써 `N*M` 반복

데이터가 적을 경우에는 문제가 없을 수 있으나 __대량의 데이터가 들어갈 경우 성능적인 문제 발생__

- ### Stream을 이용한 중첩 for 제거
```
List<HashMap> employeeList = empMapper.selectList();

// [{emp_no : 1, emp_name : kim, dept_no : 1}, {emp_no : 2, emp_name : park, dept_no : 2} .... ]

List<HashMap> deptList = deptMapper.selectList();

// [{dept_no : 1, dept_name : 기획부}, {dept_no : 2, dept_name : 영업부} .... ]

---
stream을 사용한 grouping
---

List<Long, List<HashMap>> empGrouping = employeeList.stream().collect(Collectors.groupingby(m->m.get("dept_no")));

// [1=[{emp_no : 1, emp_name : kim, dept_no : 1}], 2=[{emp_no : 2, emp_name : park, dept_no : 2}...]]

for(HashMap deptMap : deptList){
  if(empGrouping.containsKey(deptMap.get("dept_no"))){
    System.out.println("same dept");
  }
}
```

`stream`을 사용하여 기존에 `for`문이 2번 중첩되어 있던 부분을 `for`문 1번으로 실행되도록 변경

`stream`은 내부적으로 반복하기 때문에 `for`문을 줄여도 같은 결과 도출 가능

- Grouping 순서 유지
기본적으로 `stream().collect(Collectors.groupingby())`는 순서를 유지하지 않은채 그룹화
기존의 순서를 유지하면서 그룹화 하고 싶을 경우 파라미터를 추가해야함

```
List<Long, List<HashMap>> empGrouping = employeeList.stream().collect(Collectors.groupingby(m->m.get("dept_no"), LinkedList::new, Collectors.toList()));

// 기존의 employeeList의 순서에 맞게 dept_no로 그룹화
```

<br><br>

- ### 정리
  - java의 `stream`은 `grouping`뿐만 아니라 `filter`등 여러 내장 함수를 가지고 있음
  - 성능과 관련된 중요한 기능을 `stream`에 담았기 때문에 사용하는 것을 추천
  - 람다식을 사용하여 한줄로 코드를 작성할 수 있기 때문에 __가독성이 좋아짐__
