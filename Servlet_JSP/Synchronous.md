### Synchronous vs Asynchronous
---

<br>

Synchronouse(동기)와 Asynchronous(비동기)를 알아보기에 앞서 Blocking과 Non-Blocking에 대한 개념을 아는 것도 중요함

Blocking과 Non-Blocking은 프로그램의 실행 순서 관점을 보면 좀 더 쉽게 이해 가능

__공유객체는 동기방식으로 처리해야함__ (하나의 객체를 여러 스레드가 사용하는 것을 방지 - 한번에 하나씩)

Synchronous와 Asynchronous는 결과물을 돌려받는 시점에 초점을 두면 이해가 쉬움

<br>

>### __Blocking__

<br>

- 동기를 처리하기 위해 사용
- __System Call이 끝날때까지 프로그램은 대기해야하고 System Call이 완료되면 return__
- Wait Queue에 들어감

(예 : c 언어의 scanf()는 사용자가 입력하기 전까지 대기한 상태)

<br><br>

>### __Non-Blocking__

<br>

- __System Call이 완료되지 않아도 대기하지 않고 return__
- Wait Queue에 들어가지 않음

<br>

### Blocking vs Non-Blockin 차이점

- 프로그램이 바로 실행할 수 있는가
  - Blocking : 요청에 대한 응답이 올때까지 대기
  - Non-Blocking : 요청을 보낸 후 할일을 하다가 응답이 오면 수신 (요청이 올때까지 대기하지 않음)

<br><br>

>### __Synchronous (동기화)__

<br>

- __System Call이 끝날때까지 기다리고 결과물을 가져옴__

<br><br>

>### __Asynchronous__

<br>

- __System Call이 완료되지 않아도 나중에 완료가 되면 그때 결과물을 가져옴__
- 주로 Callback 함수를 통해 결과물을 가져옴

<br>

### Synchronous vs Asynchronous 차이점

- 결과물을 가져오는 시점이 다름
  - Synchronous : 요청 후 대기하다 응답이 오면 결과물을 받음
  - Asynchronous : 요청 후 다른 일을 하다 응답이 오면 결과물을 받음 (대기하지 않음)

<br>

>### __Non-Blocking vs Asynchronous 차이점__

<br>

- __System Call이 즉시 Return될 때 데이터의 포함 유무__
  - Asynchronous : 요청의 처리 완료와 관계없이 응답 (이후 운영체제에서 응답할 준비가 되면 응답)
  - Non-Blocking : 요청에 처리할 수 있으면 바로 응답하고 아니면 Error 반환

<br><br>

>### __Blocking vs Synchronous 차이점__

<br>

- Wait Queue 유무
  - Synchronous : System Call의 return을 기다리는 동안 Wait Wueue에 머물수도 머물지 않을수도 있음
  - Blocking : System Call의 return을 기다리는 동안 필수로 Wait Queue에 머뭄
