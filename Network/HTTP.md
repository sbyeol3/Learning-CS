# HTTP Protocol (Hyper Text Transfer Protocol)

- 인터넷에서 데이터를 주고 받을 수 있는 애플리케이션 계층 프로토콜
- 웹 브라우저와 서버 간에 데이터를 주고 받는 프로토콜로 HTTP를 사용

## 특징

- stateless : 각각의 데이터 요청이 독립적으로 관리
  - 서버는 별도의 추가 정보를 관리하지 않아도 됨
  - 쿠키와 세션 이용
- TCP/IP 통신 위에서 동작, 포트번호 80
- 클라이언트-서버 구조
- 확장성 : 새로운 헤더의 시멘틱에 대한 합의가 있다면 언제든지 새로운 기능을 추가할 수 있음

## HTTP request 구성

- 시작줄 : 메소드, 주소, HTTP 버전
- 헤더 : 요청에 대한 정보
- 본문 : 요청할 때 함께 보내는 데이터

## HTTP response 구성

- 시작줄 : 버전, 상태코드, 상태메시지
- 헤더 : 응답에 대한 정보
- 본문 : 요청받은 데이터

## HTTP 버전

### 1.0 vs 1.1

- 1.0에서는 요청을 보낼 때마다 TCP connection을 새로 생성
- 계속 생성하는 것이 비효율적이므로 `persistent connection`이라는 개념을 1.1에 추가하게 됨
- 또한 HTTP pipelining 이라는 개념도 추가됨
- 여전히 보낸 순서에 따라 응답을 받게 되므로 앞 순서에서 latency가 길어지면 뒤에서도 같이 길어진다는 단점이 존재 => Head Of Line Blocking

### 1.x vs 2.0

- 멀티플렉싱 개념의 도입 => 동시에 여러 리소스를 받아올 수 있게 됨
  - 먼저 처리된 요청은 먼저 받는다! 앞에서 보낸 요청 처리가 blocking 하지 않는다.
- 데이터를 전송할 때 바이너리로 인코딩하여 전송 (1은 plain text)
- 1버전에서는 메시지라는 단위로 구분되어 있었으나 2는 스트림의 구조로 변화
- 기존의 헤더를 압축하여 성능 향상

# 네이버를 접속하기까지

> www.naver.com 을 주소창에 검색하면 일어나는 과정 정리

1. 랩탑에 무선 와이파이를 연결한다. DCHP 구동이 시작된다.
2. 해당 LAN에서 DHCP 서버의 IP 주소를 알기 위해 브로드캐스팅한다.
3. DHCP 서버는 IP 주소를 동적으로 할당하고, first hop 라우터의 IP 주소 & DNS 서버의 주소를 갖고 응답한다.
4. 클라이언트는 IP 주소를 받고 DHCP 서버에게 다시 ACK을 응답한다.
5. 네이버에 HTTP 요청을 보내기 전에 네이버 IP 주소를 알아야 한다.
6. DNS가 구동되어 DNS 쿼리를 보내기 전에 First Hop Router의 MAC 주소를 알아야 한다.
7. ARP 프로토콜에 의해 First Hop Router의 MAC 주소를 알게 된다.
8. 클라이언트는 First Hop Router를 통해 DNS 쿼리를 보낸다.
9.  DNS 서버가 있는 곳까지 도달하기 위해 RIP, OSPF, IS-IS, BGP 프로토콜을 사용한다.
10. DNS 쿼리가 DNS 서버에 도달하여 네이버의 IP 주소가 들어있는 응답 메세지를 보낸다.
11. 클라이언트가 네이버에 HTTP 요청을 보내고자 네이버 웹 서버와 TCP 소켓을 연다.
12. 클라이언트는 네이버 웹 서버에 TCP 연결을 맺기 위해 segment를 보낸다.
13. 네이버 웹 서버는 연결을 맺겠다는 ACK을 보낸다.
14. 클라이언트와 네이버 웹 서버 간 TCP 연결이 생성된다.
15. TCP 소켓을 통해 HTTP 요청메세지가 보내진다.
16. 웹 서버는 HTTP 응답 메세지를 보낸다.

### 참고자료
- [복세편살 블로그 : HTTP 2의 탄생 배경과 특징](https://americanopeople.tistory.com/115)
- [와탭 블로그 : HTTP/2 알아보기](https://www.whatap.io/ko/blog/38/)
- [HTTP2 전체적인 동작방식](https://b.luavis.kr/http2/http2-overall-operation)