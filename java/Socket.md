### Socket
---
~~~
1. 소켓 생성 (소켓 열기)
2. 소켓을 통한 송/수신
3. 소켓 소멸 (소켓 닫기)
~~~

<br><br>

>### __소켓의 유형__

<br>

- SOCK_STREAM
  - TCP 통신 소켓
  - __stream 방식의 연결지향 소켓 (전화와 비슷한 연결)__
  - 양방향 통신
  - 바이트를 주고 받을 수 있는 가변 길이 stream
  - 전달된 모든 데이터는 에러 없이 원격지에 도달
  - 전달된 순서대로 수신됨
  - 먼저 연결 후 데이터 전송
  - 데이터를 보내는 입장에서는 안정적
  (데이터가 올바르게 전송되었는지 확인할 수 있음)

<br>

- SOCK_DATAGRAM
  - UDP 통신 소켓
  - __datagram 방식의 비연결성 소켓 (편지와 비슷한 비연결)__
  - 양방향 통신
  - 고정길이의 메시지를 사용
  - 신뢰성이 없음
  - 전달된 순서대로 수신되지 않음
  - 데이터가 잘 보내졌는지 확인할 수 없음

<br><br>

>### __소켓의 유형__

<br>

- TCP
  - ServerSocket
  연결을 기다리는 소켓
  accept()만 해주는 소켓
  연결 후 다른 소켓과도 연결을 시켜줌

  <br>

  - Socket
  데이터를 전송하는 소켓
  send(), receive()로 데이터 통신

<br>

- UDP
  - DatagramSocket
  패킷이 가다가 사라지면 receive()를 하면 block 상태가 됨
  (수신 여부를 확인할 수 없음)

<br><br>

>### __Port__

<br>

~~~
데이터 통신을 위해 목적지 주소에는 IP 주소뿐만 아니라 Port 번호로 포함
그래야 최종 목적지의 해당 Process(프로그램)의 Socket까지 데이터 전달 가능
~~~

<br>

- 하나의 컴퓨터에는 여러 개의 프로그램이 각각의 소켓을 사용하여 데이터 통신을 하고 있기 때문에 TCP에서는 __각 소켓을 구분__ 할 필요가 생김
- 해당되는 소켓을 찾아주기 위해서는 Socket Address (Port)를 가지고 있어야함
- 프로세스를 구분함 (프로세스끼리 데이터를 교환함)

TCP Network|Address|Data
---|---|---|
|Address = IP + Port|

<br>

- 포트의 종류
기본적으로 8080 사용
포트의 중복은 불가능
같은 UDP 포트와 TCP 포트는 중복하여 사용 가능

<br>

  - 1 - 255 : 잘 알려진 인터넷 서비스 포트 (Well-Known Port) 255 : root 권한
  해킹 때문에 root 권한만 사용할 수 있음
  - 256 - 1023 : 그 밖의 인터넷 서비스
  - 1024 - 4999 : 시스템 예약 (에러는 안나지만 사용하지 않는게 좋음)
  - 5000 - 65535 : 사용자 사용

<br><br>

>### __InetAddress 클래스__

<br>

__인터넷 주소에 관한 정보를 다룸 (IP 정보)__

<br>

- InetAddress
  - __IP Address__
  - 자바에서 인터넷 주소에 관한 정보를 다루는 클래스
  - IP 주소를 표현하고 제어하는 기능을 제공
  - 생성자 없음
  - static 메소드로 정보를 받아오는 형식으로 사용

<br>

- 주요 함수

getAddress() | 주소를 나타내는 4개의 바이트 배열을 리턴
---|---|
getHostAddress()|주소 정보를 나타내는 String 리턴
getHostName()|컴퓨터 이름을 나타내는 String 리턴

~~~
String hostname = inetAddress.getHostName(); // 컴퓨터 이름
String hostaddress = inetAddress.getHostAddress(); // IP 주소	         
~~~

<br>

- static 메소드

getLocalHost()|현재 컴퓨터의 InetAddress객체를 리턴
---|---|
getByName(Strng hostName)|hostName으로 지정된 컴퓨터의 InetAddress객체를 리턴
getAllbyName(String hostName)|hostName으로 지정된 모든 컴퓨터의 InetAddress객체 배열로 리턴

~~~
InetAddress[] inetAddress = InetAddress.getAllByName(input);

for(int i=0;i<inetAddress.length;i++) {
	System.out.println(input + " : " + inetAddress[i].getHostAddress()); // 도메인의 ip 주소 출력
}
~~~

<br>

- InetSocketAddress
SocketAddress (IP + Port)
= InetAddress + port

<br><br>

- 소켓 통신 문자열 읽기
~~~
InputStream is = socket.getInputStream();
BufferedReader br = new BufferedReader(new InputStreamReader(is, "utf-8"));

OutputStream os = socket.getOutputStream();
PrintWriter pw = new PrintWriter(os, true); // true 적어야 자동 flush()
~~~

<br><br>

- 소켓 통신 바이트 읽기

~~~
// 4. IOStream 받아오기
InputStream is = socket.getInputStream();
OutputStream os = socket.getOutputStream();

while (true) {
  // 5. Data 읽기
  byte[] buffer = new byte[256];
  int readByteCount = is.read(buffer); // Blocking - return : 읽은 byte Size

  if (readByteCount == -1) { // 다 읽으면 상대편에서 소켓 끊음
    // 정상종료 : remote socket close()
    // 메소드를 통해 정상적으로 소켓을 닫은 경우
    System.out.println("[server] Closed By Client!!!!");
    break;
  }

  String data = new String(buffer, 0, readByteCount, "UTF-8"); // buffer -> String : 0번째부터 size 까지
  System.out.println("[server] Received : " + data);

  // 6. 데이터 쓰기
  os.write(data.getBytes("UTF-8"));
}
~~~
