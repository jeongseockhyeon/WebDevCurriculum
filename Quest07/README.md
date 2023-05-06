# Quest 07. node.js의 기초

## Introduction

- 이번 퀘스트에서는 node.js의 기본적인 구조와 개념에 대해 알아 보겠습니다.

## Topics

- node.js
- npm
- CommonJS와 ES Modules

## Resources

- [About node.js](https://nodejs.org/ko/about/)
- [Node.js의 아키텍쳐](https://edu.goorm.io/learn/lecture/557/%ED%95%9C-%EB%88%88%EC%97%90-%EB%81%9D%EB%82%B4%EB%8A%94-node-js/lesson/174356/node-js%EC%9D%98-%EC%95%84%ED%82%A4%ED%85%8D%EC%B3%90)
- [npm](https://docs.npmjs.com/about-npm)
- [npm CLI commands](https://docs.npmjs.com/cli/v7/commands)
- [npm - package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json)
- [How NodeJS Require works!](https://www.thirdrocktechkno.com/blog/how-nodejs-require-works)
- [MDN - JavaScript Modules](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Modules)
- [ES modules: A cartoon deep-dive](https://hacks.mozilla.org/2018/03/es-modules-a-cartoon-deep-dive/)
- [require vs import](https://www.geeksforgeeks.org/difference-between-node-js-require-and-es6-import-and-export/)

## Checklist

- node.js는 무엇인가요? node.js의 내부는 어떻게 구성되어 있을까요?
  > node.js는 비동기 이벤트 주도 자바스크립트런타임으로써 확장성 있는 네트워크 애플리케이션을 만들 수 있도록 설계된 소프트웨어 플랫폼이다.
  > non-blocking I/O 및 단일 스레드 동작을 통해 효율적인 네트워킹을 가능하게 하며, 이에 따라 기존 cient 기반의 javascript 특징을 server 영역까지 확장할 수 있게 되었다.(non-blocking:호출 직후 프로그램으로 부터 제어가 돌아옴으로서 시스템 호출 종료를 기다리지 않고 다음 처리로 넘어갈 수 있다.)
  > node.js의 가장 강력한 특징은 싱글 스레드/비동기 패턴이다. 이 특징은 전통적인 웹 프레임워크에 비해 훨씬 간단하고 효율적인 방식으로, 다수의 requset 처리가 가능하고 빠른 응답을 구현할 수 있게 되었다.
- npm이 무엇인가요? `package.json` 파일은 어떤 필드들로 구성되어 있나요?
  > npm:node package manager, 즉 노드 패키지를 관리하는 명령어이다.
  > 'name'과 'version' 필드로 구성되어 있다.
  > name:말 그대로 이 패키지의 이름을 나타낸다. 이름에는 규칙이 있다.
  > must be lowercase, 소문자로 작성되어야 한다.
  > must be one word, 한 단어로 작성되어야 한다.
  > may contain hyphens and underscore, -이나 \_를 포함할 수 있다.
  > version:x.x.x의 형태로 작성된다. [major].[minor].[patch]의 형태를 따른다.
- npx는 어떤 명령인가요? npm 패키지를 `-g` 옵션을 통해 글로벌로 저장하는 것과 그렇지 않은 것은 어떻게 다른가요?
  > npx:node package execution, 노드패키지의 실행에 중점을 둔 명령어이다.
  > npm의 영구적인 설치, 관리 등의 부가적인 절차없이 원하는 패키지를 npm 레지스트리에 접근시켜 실행만 할 수 있도록 설치하는 일종의 실행도구이다.말그대로 실행목적의 실행도구이기 때문에, 빠른 실행결과를 보고자 할때 별도의 패키지 업데이트나 관리할 필요없이 손쉬운 실행이 가능하다
  > '-g'를 통해 글로벌로 저장하며느 말 그대로 pc내부에서의 프로젝트 전역적으로 참조할 수 있다. 그렇지 않게 저장할 경우 지역적으로 설치되어 해당 프로젝트 내부에서만 사용할 수 있다.
- 자바스크립트 코드에서 다른 파일의 코드를 부르는 시도들은 지금까지 어떤 것이 있었을까요? CommonJS 대신 ES Modules가 등장한 이유는 무엇일까요?

  > CommonJS
  > require을 통해 다른 파일을 불러오고, module.exports.component 을 통해 파일을 export하는 방식이다.
  > ES6 module
  > 최근 script 언어의 표준화를 위해 자바스크립트를 기반으로 진행되는 ECMA Script에서, 해당 표준에 정의되어 있는 module화 방식을 의미한다.
  > import와 export이용한다.

  > CommonJS 대신 ES Modules이 등장한 이유:
  >
  > 1. commonJS는 동기적으로 모듈을 로드하므로, 브라우저 환경에서 사용할 경우 성능 문제가 발생할 수 있지만 반면에 ES Modules는 비동기적으로 모듈을 로드하므로, 브라우저 환경에서도 성능 문제가 발생하지 않는다.
  > 2. CommonJS는 모듈 로드 시점이 애매하지만 ES Modules는 모듈 로드 시점이 명확하므로, ES Modules는 모듈 로드 시점이 명확하므로, 모듈 간 의존성 관리가 쉽습니다.
  > 3. CommonJS는 Node.js에서 사용되는 모듈 시스템으로 , 브라우저와의 호환성이 좋지 않지만 ES Modules는 ECMAScript 표준으로, 브라웢와의 호환성이 좋다.

- ES Modules는 기존의 `require()`와 동작상에 어떤 차이가 있을까요? CommonJS는 할 수 있으나 ES Modules가 할 수 없는 일에는 어떤 것이 있을까요?
  > commonJS처럼 스크립트를 바로 실행하지 않고 import, export구문을 찾아 스크립트를 파싱한다. 파싱단계에서 import,export에러를 감지할 수 있다.
- node.js에서 ES Modules를 사용하려면 어떻게 해야 할까요? ES Modules 기반의 코드에서 CommonJS 기반의 패키지를 불러오려면 어떻게 해야 할까요? 그 반대는 어떻게 될까요?
  > 13.2버전 이하에서는 Banel이라는 도구 사용, 이후부터는 ES모듈 사용가능 -> package.json파일에 type항목을 module로 설정하며 된다.
  > default import로 가능, CJS.method()와 같이 .을 찍어서 이용가능하다.

## Quest

- 스켈레톤 코드에는 다음과 같은 네 개의 패키지가 있으며, 용도는 다음과 같습니다:
  - `cjs-package`: CommonJS 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `esm-package`: ES Modules 기반의 패키지입니다. 다른 코드가 이 패키지의 함수와 내용을 참조하게 됩니다.
  - `cjs-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, CommonJS 기반의 프로젝트입니다.
  - `esm-my-project`: `cjs-package`와 `esm-package`에 모두 의존하는, ES Modules 기반의 프로젝트입니다.
- 각각의 패키지의 `package.json`과 `index.js` 또는 `index.mjs` 파일을 수정하여, 각각의 `*-my-project`들이 `*-package`에 노출된 함수와 클래스를 활용할 수 있도록 만들어 보세요.

## Advanced

- node.js 외의 자바스크립트 런타임에는 어떤 것이 있을까요?
