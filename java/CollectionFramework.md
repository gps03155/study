<<<<<<< HEAD
### Collection Framework
---

- __Collection이란__?
사전적 의미로 데이터를 수집해서 저장하는 것을 의미
Java Collection은 객체를 수집해서 저장하는 역할
Java Collection Framework는 인터페이스를 통해서 다양한 Collection Class를 이용할 수 있도록 함
(List, Set, Map)

<br><br>

>### __자료구조__

~~~
자료가 어떤식으로 모여있는가
어떤 특징을 가지고 있는가

3가지 정도로 모여있음
추상데이터 타입 - adt (전산에 있는 자료를 추상화) : 연산
자바에서는 인터페이스라고 불림 : 메서드

자료구조 쓰는 이유
복잡도를 줄이기 위해서 (시간, 메모리양)

제일 좋은 자료구조
검색 시 증가 추이가 적은 것 (log n) - Tree
~~~

<br><br>

>### __List__

__순서, 중복이 있는 데이터__
객체를 일렬로 늘어놓은 구조를 가짐 (배열)
객체를 인덱스로 관리하기 때문에 객체를 저장하면 자동으로 인덱스가 부여되고 인덱스로 객체를 검색, 삭제할 수 있는 기능을 제공
<br>
구현 클래스 : ArrayList, LinkedList, Vector
~~~
부모 클래스 참조
List list = new ArrayList()
            new LinkedList()
            new Vector()
~~~

<br>

  - ArrayList
  일반 배열과 ArrayList는 인덱스로 객체를 관리한다는 점에서는 유사
  배열은 생성할 때 크기가 고정되고 크기를 변경할 수 없지만 ArrayList는 저장 용량을 초과한 객체들이 들어오면 자동적으로 크기가 늘어남
  내부가 배열로 되어있음
  임의의 위치에 삽입, 삭제에는 비효율적 (순서가 아닐 경우)
  미리 버퍼를 잡아두고 순서대로 추가, 삽입하는 경우 적절 (DB)

  <br>

  - LinkedList
  ArrayList와 사용 방법은 똑같지만 내부 구조는 다름
  LinkedList는 인접 참조를 링크해서 체인처럼 관리
  특정 인덱스의 객체를 제거하면 앞뒤 링크만 변경되고 나머지 링크는 변경되지 않음
  (중간에서 하나 삭제를 하더라도 앞뒤의 노드만 연결해주면 됨)
  중간에 삽입, 삭제가 일어나는 경우 적합
  (임의의 위치에 삽입, 삭제가 일어나는 경우)
  노드 객체 : 변수 2개 (데이터, reference)
  queue 인터페이스 구현함
  ~~~
  Class Node <T> {
    Node next; // 참조
    T t; // 데이터
  }
  ~~~

  <br>

  - Vector
  ArrayList와 동일한 내부 구조를 가짐
  Vector는 동기화된 메소드로 구성되어 있기 때문에 멀티 스레드 사용시 용이
  (멀티 스레드 환경에서 안전하게 객체를 추가, 삭제 가능)

  <br>

- List 인터페이스 차이
연산이 어떻게 일어나는지 따져봐야함
ArryaList와 Vector는 구조가 같음
Collection 인터페이스 상속 - iterator() : List, Set

<br><br>

>### __Set__

__저장 순서가 유지되지 않고 객체를 중복해서 저장할 수 없음__
(순서, 중복이 없는 데이터)
수학의 집합에 비유
__순서와 상관없고 중복이 허용되지 않음__
집합 - 집합 연산 지원 (여러 대상의 모임이며 순서가 없고 중복된 값이 없음)
인덱스로 객체를 검색해서 가져오는 메소드가 없음
전체 객체를 대상으로 한번씩 반복해서 가져오는 반복자(Iterator)를 제공
iterator 쓸 때 순서가 보장되지 않을 수 있음
<br>
구현 클래스 : HashSet, LinkedHashSet, TreeSet

<br>

  - HashSet
  Set의 성격대로 순서 상관없이 저장되고 중복 저장되지 않음
  hashCode()와 equals() 메서드를 통해 true가 나오면 동일한 객체로 판단하고 중복 저장을 하지 않음

<br><br>

>### __Map__

키(Key)와 값(Value)으로 구성된 객체를 저장하는 구조
키는 중복 저장될 수 없지만 값은 중복 저장할 수 있음
키 값이 중복되어 저장된다면 먼저 저장된 값이 덮어쓰여짐
키와 값의 매핑이 중요함
<br>
구현 클래스 : HashMap, HashTable, LinkedHashMap, Properties, TreeMap

<br>

  - HashMap
  키로 사용할 객체는 hashCode(), equals() 메서드를 재정의해서 동등 객체가 될 조건을 정해야함
  주로 키는 String 타입으로 많이 사용

  <br>

  - HashTable
  HashMap과 동일한 내부구조를 가짐
  동기화(Synchronized)된 메서드로 구성되어 있기 때문에 멀티스레드 환경에서 용이
  (하나의 스레드가 실행을 완료해야만 다른 스레드 실행 가능)

  <br>

  - Properties
  HashTable의 하위 클래스이기 때문에 HashTable의 모든 특징을 그대로 가짐
  Properties는 키와 값을 String 타입으로 제한한 컬렉션
  애플리케이션의 옵션 정보, 데이터베이스 연결 정보, 다국어 정보가 저장된 .properties 파일을 읽을 때 주로 사용

<br><br>

>### __java version 1.4 전후로 나눠짐 (후 : Collection Framework)__
=======
### Collection Framework
---

- __Collection이란__?
사전적 의미로 데이터를 수집해서 저장하는 것을 의미
Java Collection은 객체를 수집해서 저장하는 역할
Java Collection Framework는 인터페이스를 통해서 다양한 Collection Class를 이용할 수 있도록 함
(List, Set, Map)

<br><br>

>### __자료구조__

~~~
자료가 어떤식으로 모여있는가
어떤 특징을 가지고 있는가

3가지 정도로 모여있음
추상데이터 타입 - adt (전산에 있는 자료를 추상화) : 연산
자바에서는 인터페이스라고 불림 : 메서드

자료구조 쓰는 이유
복잡도를 줄이기 위해서 (시간, 메모리양)

제일 좋은 자료구조
검색 시 증가 추이가 적은 것 (log n) - Tree
~~~

<br><br>

>### __List__

__순서, 중복이 있는 데이터__
객체를 일렬로 늘어놓은 구조를 가짐 (배열)
객체를 인덱스로 관리하기 때문에 객체를 저장하면 자동으로 인덱스가 부여되고 인덱스로 객체를 검색, 삭제할 수 있는 기능을 제공
<br>
구현 클래스 : ArrayList, LinkedList, Vector
~~~
부모 클래스 참조
List list = new ArrayList()
            new LinkedList()
            new Vector()
~~~

<br>

  - ArrayList
  일반 배열과 ArrayList는 인덱스로 객체를 관리한다는 점에서는 유사
  배열은 생성할 때 크기가 고정되고 크기를 변경할 수 없지만 ArrayList는 저장 용량을 초과한 객체들이 들어오면 자동적으로 크기가 늘어남
  내부가 배열로 되어있음
  임의의 위치에 삽입, 삭제에는 비효율적 (순서가 아닐 경우)
  미리 버퍼를 잡아두고 순서대로 추가, 삽입하는 경우 적절 (DB)

  <br>

  - LinkedList
  ArrayList와 사용 방법은 똑같지만 내부 구조는 다름
  LinkedList는 인접 참조를 링크해서 체인처럼 관리
  특정 인덱스의 객체를 제거하면 앞뒤 링크만 변경되고 나머지 링크는 변경되지 않음
  (중간에서 하나 삭제를 하더라도 앞뒤의 노드만 연결해주면 됨)
  중간에 삽입, 삭제가 일어나는 경우 적합
  (임의의 위치에 삽입, 삭제가 일어나는 경우)
  노드 객체 : 변수 2개 (데이터, reference)
  queue 인터페이스 구현함
  ~~~
  Class Node <T> {
    Node next; // 참조
    T t; // 데이터
  }
  ~~~

  <br>

  - Vector
  ArrayList와 동일한 내부 구조를 가짐
  Vector는 동기화된 메소드로 구성되어 있기 때문에 멀티 스레드 사용시 용이
  (멀티 스레드 환경에서 안전하게 객체를 추가, 삭제 가능)

  <br>

- List 인터페이스 차이
연산이 어떻게 일어나는지 따져봐야함
ArryaList와 Vector는 구조가 같음
Collection 인터페이스 상속 - iterator() : List, Set

<br><br>

>### __Set__

__저장 순서가 유지되지 않고 객체를 중복해서 저장할 수 없음__
(순서, 중복이 없는 데이터)
수학의 집합에 비유
__순서와 상관없고 중복이 허용되지 않음__
집합 - 집합 연산 지원 (여러 대상의 모임이며 순서가 없고 중복된 값이 없음)
인덱스로 객체를 검색해서 가져오는 메소드가 없음
전체 객체를 대상으로 한번씩 반복해서 가져오는 반복자(Iterator)를 제공
iterator 쓸 때 순서가 보장되지 않을 수 있음
<br>
구현 클래스 : HashSet, LinkedHashSet, TreeSet

<br>

  - HashSet
  Set의 성격대로 순서 상관없이 저장되고 중복 저장되지 않음
  hashCode()와 equals() 메서드를 통해 true가 나오면 동일한 객체로 판단하고 중복 저장을 하지 않음

<br><br>

>### __Map__

키(Key)와 값(Value)으로 구성된 객체를 저장하는 구조
키는 중복 저장될 수 없지만 값은 중복 저장할 수 있음
키 값이 중복되어 저장된다면 먼저 저장된 값이 덮어쓰여짐
키와 값의 매핑이 중요함
<br>
구현 클래스 : HashMap, HashTable, LinkedHashMap, Properties, TreeMap

<br>

  - HashMap
  키로 사용할 객체는 hashCode(), equals() 메서드를 재정의해서 동등 객체가 될 조건을 정해야함
  주로 키는 String 타입으로 많이 사용

  <br>

  - HashTable
  HashMap과 동일한 내부구조를 가짐
  동기화(Synchronized)된 메서드로 구성되어 있기 때문에 멀티스레드 환경에서 용이
  (하나의 스레드가 실행을 완료해야만 다른 스레드 실행 가능)

  <br>

  - Properties
  HashTable의 하위 클래스이기 때문에 HashTable의 모든 특징을 그대로 가짐
  Properties는 키와 값을 String 타입으로 제한한 컬렉션
  애플리케이션의 옵션 정보, 데이터베이스 연결 정보, 다국어 정보가 저장된 .properties 파일을 읽을 때 주로 사용

<br><br>

>### __java version 1.4 전후로 나눠짐 (후 : Collection Framework)__
>>>>>>> 3175f3de7790f097a4067c55d2a8915e3256107c
