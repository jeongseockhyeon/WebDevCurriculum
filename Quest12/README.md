# Quest 12. 보안의 기초

## Introduction

- 이번 퀘스트에서는 가장 기초적인 웹 서비스 보안에 대해 알아보겠습니다.

## Topics

- XSS, CSRF, SQL Injection
- HTTPS, TLS

## Resources

- [The Basics of Web Application Security](https://martinfowler.com/articles/web-security-basics.html)
- [Website Security 101](https://spyrestudios.com/web-security-101/)
- [Web Security Fundamentals](https://www.shopify.com.ng/partners/blog/web-security-2018)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [Wikipedia - TLS](https://en.wikipedia.org/wiki/Transport_Layer_Security)

## Checklist

- 입력 데이터의 Validation을 웹 프론트엔드에서 했더라도 서버에서 또 해야 할까요? 그 이유는 무엇일까요?

  > validation은 데이터의 유효성/신뢰도/위변조여부 등 매우 넣은 범위를 포괄하며, 이는 경중에 따라 client-server side에서 처리하도록 분할 수 있다.
  > client level에서 전달되는 data들은 데이터 위변조가 쉽고 그만큼 보안적으로 취약하다. 사용자 혹은 이에 준하는 중요한 데이터들이 server에 안전하게 보관되기 위해선 client level의 validation보다 더 안전하고 신뢰할 수 있는 validation이 진행되어야 한다.

  - 서버로부터 받은 HTML 내용을 그대로 검증 없이 프론트엔드에 innerHTML 등을 통해 적용하면 어떤 문제점이 있을까요?
    >
  - XSS(Cross-site scripting)이란 어떤 공격기법일까요?
    > XSS:웹 리소스에 악성 스크립트를 삽입해 이용자의 웹 브라우저에서 해당 스크립트를 실행하여 정보를 탈취하고 악의적인 기능을 수행하는 공격을 말한다.
  - CSRF(Cross-site request forgery)이란 어떤 공격기법일까요?
    > XSS와 같은 정보탈취 등의 악의적 기능을 수행하는 공격으로 공격자가 임의 사용자 권한으로 웹브라우저에 악의적인 공격 요청을 보내어 수행하는 공격이다.
  - SQL Injection이란 어떤 공격기법일까요?
    > SQL을 통한 감염, 악의적으로 SQL query를 조작하여 데이터베이스를 도용하거나 무단으로 조회하는 공격이다.

- 대부분의 최신 브라우저에서는 HTTP 대신 HTTPS가 권장됩니다. 이유가 무엇일까요?

  > HTTPS는 HTTP프로토콜에 SSL을 적용하여 안전성이 황보된 통신규약을 말하며 데이터통신 과정에 SSL/TLS 암호화 방식을 적용하여 상대적으로 안전한 데이터 전달이 가능하도록 한다.

  - HTTPS와 TLS는 어떤 식으로 동작하나요? HTTPS는 어떤 역사를 가지고 있나요?
    > 1. 웹 브라우저가 server에 접속하면, server는 인증서를 제공한다
    > 2. 브라우저는 제공한 인증서가 공인CA에서 제공한 것인지 확인하고, 유효성 확인 후 제공받은 공개key를 이용하여 인증서를 복호화한다.
    > 3. 인증서를 복호화한다는 것은 server가 비공개 key로 암호화한 것을 풀었다는 것, 즉 server로부터 client 인증을 증명받았다는 의미이다.
    > 4. 이후 진행할 session을 위해 client 측에서는 pre master secret을 생성 및 공개 key로 암호화, server는 이를 자신의 secret key로 복호화하고 인증과정을 마친다.
    > 5. 서로에 대한 신원을 인증하고 암호화하기 위한 과정을 SSL handshake라 하며, 인증이 완료된 이후에는 서로 공유하는 대칭키(master secret key)로 통신한다.
    > 6. 통신이 완전히 종료된 이후엔 대칭키는 폐지한다.

  > HTTP에 접목한 SSL/TLS 기술은 역사가 오래된 기술이다.
  > 네트워크 통신 보안을 제공하기 위하여 설계된 암호 규약인 SSL/TLS는 1995년 처음 발표되어 공개되었고, SSL 규약은 1995년 2.0버전을 시작으로 공개되었다.
  > SSL 자체는 이후 1999년 국제 인터넷 표준화 기구(IETF)에서 표준 규약으로 정의하면서, TLS로 명칭이 바뀌었고 최근에는 SSL과 TLS 모두 혼용하고 있다.

  - HTTPS의 서비스 과정에서 인증서는 어떤 역할을 할까요? 인증서는 어떤 체계로 되어 있을까요?
    > 인증서는 클라이언트와 서버간의 통신을 제 3자가 보증해주는 전자화된 문서이다.
    > 이용했을 이점으로는
    > 통신 내용이 공격자에게 노출되는 것을 막을 수 있다.
    > 클라이언트가 접속하려는 서버가 신뢰 할 수 있는 서버인지를 판단할 수 있다.
    > 통신 내용의 악의적인 변경을 방지할 수 있다.

## Quest

- 메모장의 서버와 클라이언트에 대해, 로컬에서 발행한 인증서를 통해 HTTPS 서비스를 해 보세요.

## Advanced

- TLS의 인증서에 쓰이는 암호화 알고리즘은 어떤 종류가 있을까요?
- HTTP/3은 기존 버전과 어떻게 다를까요? HTTP의 버전 3이 나오게 된 이유는 무엇일까요?
