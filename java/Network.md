### Network
---
- 네트워크란?
__유/무선으로 연결되어 있는 Device들의 집합__
대문자 Internet은 TCP/IP 규약대로 통신하는 인터넷

<br>

  - Packet
  네트워크 케이블을 타고 이동하는 데이터를 Packekt이라고 함
  데이터의 기본 전송 단위
  (데이터가 한 묶음씩 이동하는 기준)

  <br>

  - IP
  컴퓨터의 주소
  데이터가 찾아가야할 목적지 주소

  <br>

  - Port
  컴퓨터 내부에 네트워크 통신을 하는 애플리케이션 중 어떤 애플리케이션에게 데이터ㅡㄹ 전송해야하는지를 구분하기 위해 Port 지정
  0~65535 사이의 값을 사용
  (기존에 사용하고 있는 port를 사용하면 충돌이 일어나므로 사용하지 않는 값으로 사용해야 함)
  IP와 어플리케이션 주소인 Port 2개를 합쳐야 애플리케이션 목적지 주소가 됨

  <br>

  - 통신 프로토콜
  컴퓨터 간의 네트워크 통신을 하기 위해 서로 약속된 동일한 언어
  __네트워킹 통신을 위해 쌍방간에 약속된 언어__

  <br>

  - Socket
  통신을 위해 2개 컴퓨터 간 가상으로 연결된 통신선을 구분하는 가상망을 가르키는 용어
  JAVA 애플리케이션에서는 소켓을 이용하여 데이터를 송수신
  tcp/ip 헤더를 만들 수 있는 메서드 제공

 <br>

- TCP 연결용 클래스
  - ServerSocket
  - Socket

  <br>

- UDP 연결용 클래스
  - DatagramSocket
  - DatagramPacket

  <br>

- URL 연결관련
  - URL
  - URLConnection

  <br><br><br>

>### __OSI 7계층__

<br>

개방형 시스템 상호연결(Open System Intercon-nection : OSI) 모델로서 시스템 상호 연결에 있어 개방 모델을 뜻한다.
호환성의 결여를 막기 위해 ISO에서 OSI 참조 모델을 제시함

- 1. 물리계층 (Physical)
물리적 매체를 통해 Bit 흐름을 전송하기 위해 요구되는 기능들을 조정
케이블, 연결 장치 등과 같은 기본적인 물리적 연결기의 전기적 명세를 정하고 네트워크의 두 노드를 물리적으로 연결시켜 주는 신호방식을 다룸

<br>

- 2. 데이터링크 계층 (Data Link)
오류없이 한 장치에서 다른 장치로 Frame(Bit의 모음)을 전달하는 역할
스위치같은 장비의 경우 MAC 주소를 이용하여 정확한 장치로 정보 전달
3계츠에서 정보를 받아 주소와 제어 정보를 시작(header)과 끝(tail)에 추가

<br>

- 3. 네트워크 계층 (Network)
다중 네트워크 링크에서 패킷을 발신지로부터 목적지로 전달할 책임을 가짐
2계층은 노드대노드 전달을 감독하는 것이고 3계층은 각 패킷이 시작 시점에서 최족 목적지까지 성공적이고 효과적으로 전달되도록하며 대표적인 프로토콜은 IP

<br>

- 4. 전송 계층 (Transport)
전체 메시지를 발신지 대 목적지(종단 대 종단)간 제어와 에러를 관리
패킷들의 전송이 유효한지 확인하고 실패한 패킷은 다시 보내는 등 신뢰성 있는 통신을 보장하며 머리말에는 세그먼트(Segment)가 포함

<br>

- 5. 세션 계층 (Session)
통신 세션을 구성하는 계층으로 포트 연결이라고 할 수 있음
통신장치 간의 상호작용을 설정하고 유지하며 동기화
사용자간의 포트연결(세션)이 유효한지 확인하고 설정

<br>

- 6. 표현 계층 (Presentation)
운영체계의 한 부분으로 입력 또는 출력되는 데이터를 하나의 표현 형태로 변환
필요한 번역을 수행하여 두 장치가 일관되게 전송 데이터를 서로 이해할 수 있도록 함

<br>

- 7. 응용계층 (Application)
사용자가 네트워크에 접근할 수 있도록 해주는 계층
사용자 인터페이스, 전자우편, 데이터베이스 관리 등 서비스 제공

<br><br>

>### __TCP__

TCP/IP 프로토콜에 포함된 프로토콜 (OSI 7계층의 전송 계층에 해당)
데이터를 전송하기 전에 먼저 상대편과 연결을 한 후에 데이터를 전송하고 전송되었는지 확인 후 실패하면 재전송

<br><br>

>### __UDP__

연결하지 않고 데이터를 전송하고 전송되었는지 확인하지 않음
데이터를 보낸 순서대로 수신한다는 보장이 없음



<br><br>

>### __Client / Server__

<br>

~~~
server = 서비스를 제공하는 컴퓨터
client = 서비스를 사용하는 컴퓨터

서버가 서비스를 제공하기 위해서는 서버 프로그램이 있어야 하고
클라이언트가 서비스를 제공받기 위해서는 서버 프로그램과 연결할 수 있는 클라이언트 프로그램이 있어야 함
~~~

<br>

- Server
다수의 클라이언트에게 서비스 제공
클라이언트로부터 요청받은 작업을 처리하여 결과를 제공
(파일 서버, 메일 서버, 어플리케이션 서버 등)
네트워크를 구성할 때 전용 서버를 두는 것을 서버기반모델(server-based model)이라 하고 별도의 전용 서버 없이 각 클라이언트가 서버역할을 동시에 수행하는 것을 P2P 모델(peer-to-peer)이라 한다.
