### I/O Stream
---

- __Stream이란__
Stream은 '__데이터 입출력 처리의 중간자 역할__'을 수행하여 입출력 관련된 곳이면 어디서든 동작
외부에서 들어오는 데이터를 입력(input)받고 출력(output)하는 '터널'과 같은 중간자 역할 을 수행
단방향으로 데이터를 송수신하기 때문에 Input과 Output을 구분하여 사용
크게 문자 단위 Stream과 Byte 단위의 Stream으로 분류
  - 파일
  - 키보드, 모니터
  - 메모리
  - 네트워크

~~~
1. 목표로 하는 데이터를 정한다.
2. 데이터에 맞는 Stream을 생성한다.
3. Stream 클래스의 멤버 메소드를 이용하여 쉽게 데이터를 핸들한다.
   (기록,읽기, 전송, 수신)
~~~

<br><br>

>### __I/O 클래스 이름과 의미__

- Stream으로 끝나는 클래스
byte 단위로 입출력을 수행하는 클래스
- Reader / Writer로 끝나는 클래스
char 단위로 입출력을 수행하는 클래스
- File로 시작하는 클래스
하드 디스크의 파일을 사용하는 클래스
- Data로 시작하는 클래스
자바의 원시 자료형을 출력하기 위한 클래스
- Buffered로 시작하는 클래스
시스템의 buffer를 사용하는 클래스

<br><br>

>### __InputStream / OutputStream (byte 출력)__

- InputStream
read()
해당 입력 스트림에서 더 이상 읽어들일 바이트가 없으면 -1 반환

- OutputStrem
write()


입력 스트림 | 출력 스트림 | 입출력 대상
--- | --- | --- | --- |
FileInputStream|FileOutputStream|파일
ByteArrayInputStream|ByteArrayOutputStream|메모리
PipedInputStream|PipedOutputStream|프로세스
AudioInputStream|AudioOutputStream|오디오 장치


<br><br>

>### __Reader / Writer (문자 입출력)__

자바에서 스트림은 기본적으로 바이트 단위로 데이터를 전송
char형은 2바이트형이므로 1바이트씩 전송되는 바이트 기반 스트림으로는 원활한 처리가 힘든 경우가 있음

- Reader
- Writer

입력 스트림|출력 스트림|입출력 대상
---|---|---|
FileReader|FileWriter|파일
CharArrayReader|CharArrayWriter|메모리
PipedReader|PipredWriter|프로세스
StringReader|StringWriter|문자열

<br><br>

>### __보조 스트림 (Byte)__

자바에서 제공하는 보조 스트림은 실제로 데이터를 주고 받을 수는 없지만, 다른 스틺의 기능을 향상시키거나 새로운 기능을 추가해주는 스트림

입력 스트림|출력 스트림|설명
--- | --- | ---|
FilterInputStream|FilterOutputStream|필터를 이용한 입출력
BufferedInputStream|BufferedOutputStream|버퍼를 이용한 입출력
DataInputStream|DataOutputStream|입출력 스트림으로부터 자바의 기본 타입으로 데이터를 읽어올 수 있게 함
ObjectInputStream|ObjectOutputStream|데이터를 객체 단위로 읽거나 읽어들인 객체를 역직렬화 시킴
SequenceInputStream|X|두 개의 입력 스트림을 논리적으로 연결함
PushbackInputStream|X|다른 입력 스트림에 버퍼를 이용하여 push back이나 unread와 같은 기능을 추가함
X|PrintStream|다른 출력 스트림에 버퍼를 이용하여 다양한 데이터를 출력하기 위한 기능을 추가함

<br><br>

>### __보조 스트림 (Char)__

입력 스트림 | 출력 스트림 | 설명
---|---|---|
FilterReader | FilterWriter | 필터를 이용한 입출력
BufferedReader|BufferredWriter|버퍼를 이용한 입출력
PushbackReader|X|다른 입력 스트림에 버퍼를 이용하여 push back이나 unread와 같은 기능을 추가함
X|PrintWriter|다른 출력 스트림에 버퍼를 이용하여 다양한 데이터를 출력하기 위한 기능을 추가함
