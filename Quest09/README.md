# Quest 09. 서버와 클라이언트의 대화

## Introduction

- 이번 퀘스트에서는 서버와 클라이언트의 연동, 그리고 웹 API의 설계 방법론 중 하나인 REST에 대해 알아보겠습니다.

## Topics

- expressJS, fastify
- AJAX, `XMLHttpRequest`, `fetch()`
- REST, CRUD
- CORS

## Resources

- [Express Framework](http://expressjs.com/)
- [Fastify Framework](https://www.fastify.io/)
- [MDN - Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API)
- [MDN - XMLHttpRequest](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest)
- [REST API Tutorial](https://restfulapi.net/)
- [CRUD](https://en.wikipedia.org/wiki/Create,_read,_update_and_delete)
- [MDN - CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS)

## Checklist

- 비동기 프로그래밍이란 무엇인가요?
  > 비동기 프로그램이이란 특정 코드의 처리가 완료되기 전, 처리하는 도중에도 아래로 계속 내려가며 수행을 하는 것이다.
  - 콜백을 통해 비동기적 작업을 할 때의 불편한 점은 무엇인가요? 콜백지옥이란 무엇인가요?
    > 함수의 인자를 전달받을 때 변수가 아닌, 함수를 전달받는 경우 가독성이 떨어진다. 이러한 상황이 계속 중첩될 경우 복잡한 구조를 콜백지옥이라고 한다. 콜백지옥은 가독성도 떨어지고 실수 위험도 커지기 때문에 위험하다.
  - 자바스크립트의 Promise는 어떤 객체이고 어떤 일을 하나요?
    > promise: 프로미스가 생성된 시점에는 알려지지 않았을 수도 있는 값을 위한 대리자로, 비동기 연산이 종료된 이후에 결과 값과 실패 사유를 처리하지 위한 처리기를 연결할 수 있다. 프로미스를 사용하면 비동기 메서드에서 마치 동기 메서드처럼 값을 반환할 수 있다. 다만 최종 결과를 반환할 수 있다. 다만 최종 결과를 반환하는 것이 아니고, 미래의 어떤 시점에 결과를 제공하겠다는 '약속'(프로미스)을 반환한다.
  - 자바스크립트의 `async`와 `await` 키워드는 어떤 역할을 하며 그 정체는 무엇일까요?
    > asybc와 await는 자바스크립트의 비동기 처리 패턴 중 가장 최근에 나온 문법으로 기존의 비동기 처리 방식인 콜백 함수와 프로미스의 단점을 보완하였다
    > async:funtion 앞에 async을 붙여줌으로써, 함수내에서 await 키워드를 사용할 수 있게 된다.
    > await:promis 비동기 처리가 완료될 때까지 코드 살행을 일시 중지하고 wait 한다라는 뜻, async 함수 내에서 비동기 함수를 호출하고, 반환된 promise를 awiait 키워드로 처리한다.
- 브라우저 내 스크립트에서 외부 리소스를 가져오려면 어떻게 해야 할까요?
  > http 프로토콜에서 req 인자에 외부 resource, data를 전달할 수 있다.
  - 브라우저의 `XMLHttpRequest` 객체는 무엇이고 어떻게 동작하나요?
    > 서버와 상호작용을 할 수 있는 객체이다. 데이터를 받아올 수 있는 객체이며, 해당 사이트 혹은 get/post method를 통해 전달받는 resource들을 XMLHttpRequest를 통해 얻을 수 있다.
    > HTTP와 함께 FTP같은 다른 프로토콜에서도 동작이 가능하며, 별도의 상태코드가 존재한다.
    > 0 : uninitialized, request 요청 전
    > 1 : loading, client와 server 연결됨(event triggered)
    > 2 : loaded, server가 request를 받음
    > 3 : interactive, request를 처리함
    > 4 : complete, response 대기
  - `fetch` API는 무엇이고 어떻게 동작하나요?
    > 데이터 확보 및 생성 등을 위해 사용하는 도구 중 하나이다.
    > fetch는 서버와의 상호작용이 성공적으로 완료되면 res인자를 반환한다.
- REST는 무엇인가요?
  > web application 이나 microservice architecture에서 각 component들을 연결하는 가장 일방적인 method 및 API
  - REST API는 어떤 목적을 달성하기 위해 나왔고 어떤 장점을 가지고 있나요?
    > 균일한 인터페이스(멱등성):요청에 상관없이 동일한 resource에 대한 모든 API요청은 동일하게 보여져야 하며, client가 필요로 하는 모든 정보를 포함해야 한다.
    > client/server decoupling : client와 server는 서로 완전히 독립적이어야 하고, resource의 URI를 제외하고 어떠한 방식으로도 서로 상호작용은 할 수 없다.
    > Stateless : server는 client 요청과 관련한 데이터를 저장할 수 없으며, 이에 따라 client request에서 처리가 필요한 모든 정보가 담겨져 있어야 한다
    > caching : resource는 client/server에서 caching할 수 있어야 하며, server 응답에는 caching 허용 여부에 대한 정보가 포함되어 있어야 한다.->resource caching이 가능하다면 clinet/server의 구성 요소 확장성이 증가한다.
  - RESTful한 API 설계의 단점은 무엇인가요?
    > use strict 모드에서만 설계할 수 있을 만큼 method가 제한적이고, 모든 조건을 만족하는 API설계가 쉽지 않다.
- CORS란 무엇인가요? 이러한 기능이 왜 필요할까요? CORS는 어떻게 구현될까요?
  > Cross-Origin Resource Sharing(교차 출처 resource 공유)/CORS는 request을 발생한 자원의 출처가 다를 경우, application이 모든 자원에 접근할 수 있도록 권한을 부여하는 체제이다.
  > server 동작을 일으키는(POST 등)HTTP method의 header에 CORS를 명기한 사전전달을 진행하며, server허가가 이루어지면 CORS가 가능해진다.

## Quest

- 이번 퀘스트는 Midterm에 해당하는 과제입니다. 분량이 제법 많으니 한 번 기능별로 세부 일정을 정해 보고, 과제 완수 후에 그 일정이 얼마나 지켜졌는지 스스로 한 번 돌아보세요.
  - 이번 퀘스트부터는 skeleton을 제공하지 않습니다!
- Quest 05에서 만든 메모장 시스템을 서버와 연동하는 어플리케이션으로 만들어 보겠습니다.
  - 클라이언트는 `fetch` API를 통해 서버와 통신합니다.
  - 서버는 8000번 포트에 REST API를 엔드포인트로 제공하여, 클라이언트의 요청에 응답합니다.
  - 클라이언트로부터 온 새 파일 저장, 삭제, 다른 이름으로 저장 등의 요청을 받아 서버의 로컬 파일시스템을 통해 저장되어야 합니다.
    - 서버에 어떤 식으로 저장하는 것이 좋을까요?
  - API 서버 외에, 클라이언트를 띄우기 위한 서버가 3000번 포트로 따로 떠서 API 서버와 서로 통신할 수 있어야 합니다.
  - Express나 Fastify 등의 프레임워크를 사용해도 무방합니다.
- 클라이언트 프로젝트와 서버 프로젝트 모두 `npm i`만으로 디펜던시를 설치하고 바로 실행될 수 있게 제출되어야 합니다.
- 이번 퀘스트부터는 앞의 퀘스트의 결과물에 의존적인 경우가 많습니다. 제출 폴더를 직접 만들어 제출해 보세요!

## Advanced

- `fetch` API는 구현할 수 없지만 `XMLHttpRequest`로는 구현할 수 있는 기능이 있을까요?
- REST 이전에는 HTTP API에 어떤 패러다임들이 있었을까요? REST의 대안으로는 어떤 것들이 제시되고 있을까요?
