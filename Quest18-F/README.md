# Quest 18-F. 프로그레시브 웹앱

## Introduction

- 이번 퀘스트에서는 2021년 현재 웹 프론트엔드의 많은 최신 기술 중 프로그레시브 웹앱에 관해 알아보겠습니다.

## Topics

- Progressive Web App(PWA)
- Service Worker
- Cache & CacheStorage API
- Web Manifest

## Resources

- [MDN - Progressive web apps (PWAs)](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [MDN - Progressive web app Introduction](https://developer.mozilla.org/ko/docs/Web/Progressive_web_apps/Introduction)
- [MDN - Service Worker API](https://developer.mozilla.org/ko/docs/Web/API/Service_Worker_API)
- [web.dev - Progressive Web Apps](https://web.dev/progressive-web-apps/)

## Checklist

- 웹 어플리케이션을 프로그레시브 웹앱 형태로 만들면 어떤 이점을 가질까요?
  > 웹은 인터넷, 사이트 방문을 통해 사용자가 쉽게 방문할 수 있다는 장점이 있다. 또한 링크를 통해서도 접근이 가능하기 때문에, 검색 및 노출 측면에서 용이하다.
  > 앱은 설치가 가능하며 오프라인을 통한 이용이 가능하다. 브라우저마다 제한사항 및 지원기능이 다른 반면 앱은 운영체제와의 통합이 유리하여 모바일 환경에서의 제약이 거의 존재하지 않는다. UX가 더 부드럽고 확장성 측면에서 유리하며, 전체적으로 설치와 동작측면에서 용이하다.
- 서비스 워커란 무엇인가요? 웹 워커와의 차이는 무엇인가요?

  > 서비스 워커
  > pwa를 구현하기 위해 사용하는 기능,API 중 하나이다.
  > 어플리케이션, 브라우저, 네트워크 사이에서 프록시 서버처럼 동작한다.
  > 네트워크 환경에서 해당 네트워크 요청을 다루거나(intercept), server 자원을 동기화하거나 푸쉬알림을 구현할 수 있게 된다.
  > Javscript 웹에서 메인 스레드와 별도로 동작하기 때문에 DOM access가 존재하지 않고, 동작 범위가 앱 전체에 적용된다.
  > 보안적인 이유로 HTTPS환경에서만 작동하는 등 제약 사항이 있다.

  > 웹 워커
  > 특정 Javscript 파일에 대해 PWA 동작을 적용하는 객체이다.
  > PWA를 구현하는 목적 보다는, 앱의 메인 스레드와 분리된 스레드에서 작업을 분리하여 기능개선에 도움을 주는 목적으로 사용한다.

> 즉 서비스워커는 pwa의 구현 자체가 목적, 웹 워커는 pwa의 기능 개선이 목적인 차이를 둔다.

- PWA의 성능을 높이기 위한 방법론에는 어떤 것들이 있고, 어떤 식으로 적용할 수 있을까요?
  > 서비스 워커를 사용한 캐싱(별도 스레드에서 데이터 교환)을 진행하면 로딩시간 등을 절약할 수 있다.
  > 앱 업데이트가 있을 경우 변경된 컨텐츠만 업데이트 진행(DOM개념), 네이티브 앱에서는 이러한 DOM개념이 존재하지 않는다(변경된 전체 앱을 다운로드).
  > 성능적인 관점 말고도 시스템 알림 등을 통해 사용자 리텐션 비율 등 재사용, 전환율 등을 높일 수 있다.

## Quest

- 텍스트 에디터 프로그램을 PWA 형태로 만들어 보세요.
  - 필요한 에셋을 적절히 캐싱하되, 버전업이 되었을 때 캐싱을 해제할 수 있는 형태가 되어야 합니다.
  - 해당 PWA를 데스크탑에 인스톨 가능하도록 만들어 보세요.
  - 오프라인인 경우에는 임시저장 기능을 만들어, 온라인인 경우를 감지하여 자동으로 서버에 반영되도록 만들어 보세요.

## Advanced

- 본 퀘스트의 주제로 고려되었으나 분량상 선정되지 않은 주제들은 다음과 같습니다. 시간날 때 한 번 찾아 보세요!
  - Search Engine Optimization(SEO)
  - CSS-in-JS와 Styled Component
  - Server-Side Rendering(SSR)
