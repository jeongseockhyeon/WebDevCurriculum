# Quest 08. 웹 API의 기초

## Introduction

- 이번 퀘스트에서는 웹 API 서버의 기초를 알아보겠습니다.

## Topics

- HTTP Method
- node.js `http` module
  - `req`와 `res` 객체

## Resources

- [MDN - Content-Type Header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type)
- [MDN - HTTP Methods](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)
- [MDN - MIME Type](https://developer.mozilla.org/en-US/docs/Glossary/MIME_type)
- [Postman](https://chrome.google.com/webstore/detail/postman/fhbjgbiflinjbdggehcddcbncdddomop)
- [HTTP Node.js Manual & Documentation](https://nodejs.org/api/http.html)

## Checklist

- HTTP의 GET과 POST 메소드는 어떻게 다른가요?
  > GET:클라이언트에서 서버로 어떠힌 리소스로부터 정보를 요청하기 위해 사용되는 메서드이다.
  > POST:리소스를 생성/업데이트하기 위해 서버에 데이터를 보내는 데 사용된다.
  > GET 요청은 멱등이며, POST는 멱등이 아니다.(멱등:연산을 여러 번 적용하더라도 결과가 달라지지 않는 성질)
  - 다른 HTTP 메소드에는 무엇이 있나요?
    > HEAD:get메서드의 요청과 동일한 응답을 요구하지만, 응답 본문을 포함하지 않는다.
    > PUT:목적 리소스 모든 현재 표시를 요청 payload로 바꾼다.
    > DELETE:특정 리소스를 삭제한다.
    > CONNECT:목적 리소스로 식별되는 서버로의 터널을 맺는다.
    > TRACE:목적 리소스의 경로를 따라 메시지 loop-back테스트를 한다.
    > PATCH리소스의 부분만을 수정하는 데 쓰인다.
- HTTP 서버에 GET과 POST를 통해 데이터를 보내려면 어떻게 해야 하나요?
  > > GET은 URL에 요청하는 데이터를 보내기 때문에 HTTP 메시지에 body가 없고 보안이 취약하고, POST는 bod에 데이터를 담아 보내기 때문에 당연히 HTTP 메시지에 body가 존재하고 보안이 GET보다 우수하다.
  - HTTP 요청의 `Content-Type` 헤더는 무엇인가요?
    > Content-Type:HTTP 메시지에 담겨 보내는 데이터의 형식을 알려주는 헤더이다.
  - Postman에서 POST 요청을 보내는 여러 가지 방법(`form-data`, `x-www-form-urlencoded`, `raw`, `binary`) 각각은 어떤 용도를 가지고 있나요?
    > form-data:양식 데이터는 양식을 채울 때 입력 한 세부 정보와 같이 양식 내부에 래핑하는 데이터를 보내는데 사용된다. 이러한 세부 정보는 Key가 보내는 항목의 '이름'이고 value는 실제 값을 입력하여 key-value 쌍으로 작성하여 전송된다.
    > x-www-form-urlencoded:form-data와 x-www-form-urlencoded는 유사하다. 둘 다 거의 동일한 목적으로 사용되지만 본 방법은 url를 인코딩한다는 것이다. 인코딩 되면 전송되는 데이터가 다른 문자로 인코딩되어 공격을 받고 있어도 인식할 수 없다.
    > Raw:Raw는 post 메서드에서 본문을 보내는 동안 가장 많이 사용되는 부분 또는 옵션이다. postman의 관점에서 중요하다. Raw는 본문 메시지가 요청 본문을 나타내는 비트 스트림으로 표시됨을 의미한다. 이러한 비트는 문자열 서버로 해석된다.
    > Binary:Binary는 수동으로 입력할 수 없는 형식으로 데이터를 전송하도록 설계되었다. 컴퓨터의 모든 것이 바이너리로 변환되기 때문에 이미지, 파일 등과 같이 수동으로 작성할 수 없는 상황일 때 이러한 옵션을 사용한다.
- node.js의 `http` 모듈을 통해 HTTP 요청을 처리할 때,
  - `req`와 `res` 객체에는 어떤 정보가 담겨있을까요?
    > req:http에 보내는 요청, 파라미터,쿠키,ip,쿼리 스트링,프로토콜 등등에 정보를 담아서 보낸다.
    > res:http에게 받는 응답, 응답 코드,JSON 등등 담겨 있다.
  - GET과 POST에 대한 처리 형태가 달라지는 이유는 무엇인가요?
    > GET은 가져오는 것이고 POST는 서버의 값이나 상태를 바꾸기 위해서 사용하기 때문에 처리 형태가 달라진다.
- 만약 API 엔드포인트(URL)가 아주 많다고 한다면, HTTP POST 요청의 `Content-Type` 헤더에 따라 다른 방식으로 동작하는 서버를 어떻게 정리하면 좋을까요?
  > 클라이언트로부터 많은 요청이 오고, 이에 따른 resource update 발생 middleWare에서 parsing하는 부분을 더 효율적으로 구상한다. content-type을 json방식 혹은 x-www-url-encoded(url-encoded)방식으로 제공하는 두개의 method를 구성하는 등 지원하는 data 형식을 확인한다.
  - 그 밖에 서버가 요청들에 따라 공통적으로 처리하는 일에는 무엇이 있을까요? 이를 어떻게 정리하면 좋을까요?
    > 기본적으로 http module을 사용한다면 res인자에 server 응답 정보가 담겨져 온다. 이 res인자를 parsong하여, client가 어떠한 가공된 정보를 받아야 하는지 결정하고 구현하는 것이다.

## Quest

- 다음의 동작을 하는 서버를 만들어 보세요.
  - 브라우저의 주소창에 `http://localhost:8080`을 치면 `Hello World!`를 응답하여 브라우저에 출력합니다.
  - 서버의 `/foo` URL에 `bar` 변수로 임의의 문자열을 GET 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/foo` URL에 `bar` 키에 임의의 문자열 값을 갖는 JSON 객체를 POST 메소드로 보내면, `Hello, [문자열]`을 출력합니다.
  - 서버의 `/pic/upload` URL에 그림 파일을 POST 하면 서버에 보안상 적절한 방법으로 파일이 업로드 됩니다.
  - 서버의 `/pic/show` URL을 GET 하면 브라우저에 위에 업로드한 그림이 뜹니다.
  - 서버의 `/pic/download` URL을 GET 하면 브라우저에 위에 업로드한 그림이 `pic.jpg`라는 이름으로 다운로드 됩니다.
- expressJS와 같은 외부 프레임워크를 사용하지 않고, node.js의 기본 모듈만을 사용해서 만들어 보세요.
- 처리하는 요청의 종류에 따라 공통적으로 나타나는 코드를 정리해 보세요.

## Advanced

- 서버가 파일 업로드를 지원할 때 보안상 주의할 점에는 무엇이 있을까요?
