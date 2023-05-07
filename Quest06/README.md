# Quest 06. 인터넷의 이해

## Introduction

- 이번 퀘스트에서는 인터넷이 어떻게 동작하며, 서버와 클라이언트, 웹 브라우저 등의 역할은 무엇인지 알아보겠습니다.

## Topics

- 서버와 클라이언트, 그리고 웹 브라우저
- 인터넷을 구성하는 여러 가지 프로토콜
  - IP
  - TCP
  - HTTP
- DNS

## Resources

- [OSI 모형](https://ko.wikipedia.org/wiki/OSI_%EB%AA%A8%ED%98%95)
- [IP](https://ko.wikipedia.org/wiki/%EC%9D%B8%ED%84%B0%EB%84%B7_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Online service Traceroute](http://ping.eu/traceroute/)
- [TCP](https://ko.wikipedia.org/wiki/%EC%A0%84%EC%86%A1_%EC%A0%9C%EC%96%B4_%ED%94%84%EB%A1%9C%ED%86%A0%EC%BD%9C)
  - [Wireshark](https://www.wireshark.org/download.html)
- [HTTP](https://ko.wikipedia.org/wiki/HTTP)
  - Chrome developer tool, Network tab
- [DNS](https://ko.wikipedia.org/wiki/%EB%8F%84%EB%A9%94%EC%9D%B8_%EB%84%A4%EC%9E%84_%EC%8B%9C%EC%8A%A4%ED%85%9C)
  - [Web-based Dig](http://networking.ringofsaturn.com/Tools/dig.php)

## Checklist

- 인터넷은 어떻게 동작하나요? Internet Protocol Suite의 레이어 모델에 입각하여 설명해 보세요.
  > 1.  PC가 인터넷에 접근할 때 인터넷 영역에서의 수많은 라우팅을 관리하는 Hob(Default Gateway)이 필요하며, 최종적으로 인터넷 사이트에 해당하는 라우터에 접근한다
  > 2.  보통 상대의 목적지 IP 주소는 특정 값으로 정해지지만, 인터넷의 경우엔 0.0.0.0/0으로 특정지어지지 않는다.
  > 3.  라우팅 경로 정보가 정해져 있는 정적라우팅과는 달리, 네트워크 상황에 따라 정보를 빠르게 확보할 수 있는 경로를 중심으로 패킷을 전송하는 라우팅이다.
  > 4.  데이터 정보에 포함된 목적지 주소가 인터넷처럼 광범위하거나, 정적 라우팅을 통한 탐색이 불가능할 경우 동적 라우팅(보통 지역 통신사 등)을 통해 데이터 전달을 진행한다.
  - 근거리에서 서로 떨어진 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?
    > 근거리에 놓여진 두 기기의 네트워크 대역은 보통 정적 라우팅을 통해 연결하며, 라우팅테이블에 저장된 두 기기의 IP와 Port 정보를 통해 데이터 전달이 이루어진다.
    > 와이파이를 통해 연결한다면 무선 고유기를 통한 라우팅을 진행할 것이고, 블루투스를 통해 연결한다면 BLE stack 프로토콜을 기반으로 통신을 진행할 것이다.
  - 근거리에 있는 여러 대의 전자기기가 서로 통신하는 프로토콜은 어떻게 동작할까요?
    > 근거리에 있는 여러 대의 전자기기는 LAN을 통해서 통신을 진행하게 된다.
  - 아주 멀리 떨어져 있는 두 전자기기가 유선/무선으로 서로 통신하는 프로토콜은 어떻게 동작할까요?
    > 사용하는 프로토콜은 두 기기간 거리보단, 두 기기가 네트워크를 어떤 형태를 통해 연결하였으며 어떤 통신규약을 채용하고 어떤 통신규약을 채용하고 있는지에 영향을 받는다.
    > 보통 멀리 떨어져 있는 기기의 경우엔 근거리 대역의 네트워크가 없어 라우팅 테이블 작성이 어려우므로, 인터넷과 같이 Hob(지역 통신사)를 통한 데이터 전달이 이루어진다.
  - 두 전자기기가 신뢰성을 가지고 통신할 수 있도록 하기 위한 프로토콜은 어떻게 동작할까요?
    > 웹과 사용자간의 대표적인 통신규약인 HTTP는, SSL인증을 적용한 HTTPS 프로토콜을 사용한 것이 가장 대표적인 보안적용의 예이다.
    > HTTP프로토콜을 통한 데이터통신 과정에 SSL/TLS 암호화 방식(양방향 암호화)를 적용하여 상대적으로 안전한 데이터 전달이 가능하도록 한 방식이다
  - HTTP는 어떻게 동작할까요?
    > 개발자가 구성한 알고리즘 및 문서구성(HTML)에 따라 데이터 및 헤더에 데이터를 저장하고, request/response를 기반으로 웹사이트 동작이 이루어진다.
- 우리가 브라우저의 주소 창에 www.knowre.com 을 쳤을 때, 어떤 과정을 통해 서버의 IP 주소를 알게 될까요?

## Quest

- tracert(Windows가 아닌 경우 traceroute) 명령을 통해 www.google.com 까지 가는 경로를 찾아 보세요.
  - 어떤 IP주소들이 있나요?
    > 220.72.105.254/112.188.47.241/.../108.170.235.5/172.217.161.196 약 15개의 ip가 확인 되었다.
  - 그 IP주소들은 어디에 위치해 있나요?
    > 처음부터 6번까지는 한국을 위치헸다가 이후부터는 미국 구글 쪽에 위치한 ip들로 확인되었다.
- Wireshark를 통해 www.google.com 으로 요청을 날렸을 떄 어떤 TCP 패킷이 오가는지 확인해 보세요
  - TCP 패킷을 주고받는 과정은 어떻게 되나요?
    > 3-Way handshake
    >
    > 1.  클라이언트는 SYN(a) 패킷을 보내고, 응답을 기다리는 SYN_SENT 상태가 된다
    > 2.  서버는 요청을 수락했다는 의미로 SYN(b)와 ACK(a + 1)이 담긴 패킷을 보내고, SYN_RECEIVED 상태가 된다.
    > 3.  클라이언트는 서버로부터 SYN(b)와 ACK(a + 1) 패킷을 받고, ACK(b + 1)를 서버로 보내면 연결이 성립되어 두 호스트는 ESTABLISHED 상태가 된다,
  - 각각의 패킷에 어떤 정보들이 담겨 있나요?
    > HTTP 응답 정보들이 담겨있다.
- telnet 명령을 통해 http://www.google.com/ URL에 HTTP 요청을 날려 보세요.
  - 어떤 헤더들이 있나요?
    > HTTP/1.0 400 Bad Request
    > Content-Type: text/html; charset=UTF-8
    > Referrer-Policy: no-referrer
    > Content-Length: 1555
    > Date: Sun, 07 May 2023 13:23:43 GMT
  - 그 헤더들은 어떤 역할을 하나요?
    > HTTP 연결 상태 확인
    > 콘텐츠 정보
    > 콘텐츠 크기
    > 날짜 및 시간

## Advanced

- HTTP의 최신 버전인 HTTP/3는 어떤 식으로 구성되어 있을까요?
- TCP/IP 외에 전세계적인 네트워크를 구성하기 위한 다른 방식도 제안된 바 있을까요?
