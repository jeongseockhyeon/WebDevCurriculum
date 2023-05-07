# Quest 17-F. 번들링과 빌드 시스템

## Introduction

- 이번 퀘스트에서는 현대적 웹 클라이언트 개발에 핵심적인 번들러와 빌드 시스템의 구조와 사용 방법에 대해 알아보겠습니다.

## Topics

- Webpack
- Bundling
  - Data URL
- Transpiling
  - Source Map
- Hot Module Replacement

## Resources

- [Webpack](https://webpack.js.org/)
- [Webpack 101: An introduction to Webpack](https://medium.com/hootsuite-engineering/webpack-101-an-introduction-to-webpack-3f59d21edeba)

## Checklist

- 여러 개로 나뉘어진 자바스크립트나 이미지, 컴포넌트 파일 등을 하나로 합치는 작업을 하는 것은 성능상에서 어떤 이점이 있을까요?

  > 1.  웹 서비스에서 렌더링 및 소요시간 감소
  > 2.  정적 자산에 대한 유효성 검사 소요사건 감소

  - 이미지를 Data URL로 바꾸어 번들링하는 것은 어떤 장점과 단점이 있을까요?
    > 장점: image를 URL data로 변환할 경우 base64로 인코딩된 형식이며, 이를 임베드하여 image/jpeg 파일을 불러올 수 있게 된다.
    > 이 과정자체가 간단하고 복잡하지 않고, 사용자가 문서 내(text editor 등)에 직접 인라인으로 임베드할 수 있다.

  > 단점:VanillaJS에서는 filesystem(fileReader)에서 관련 method를 지원하여 자동으로 인코딩 해주지만, 직접 할 경우 특정 스킴(data : ~)을 누락하여 오류가 발생할 수 있다.
  > 브라우저의 경우 URL 데이터의 최대 길이가 제한된다.
  > 또한 base64로 인코딩하면서 발생하는 오류는 직접 파악하고 해결해야 하며(오류에 대한 디버깅을 하지 않음), 직접 인라인 코딩을 구현하는 경우엔 복잡해진다.

- Source Map이란 무엇인가요? Source Map을 생성하는 것은 어떤 장점이 있을까요?
  > Source Map이란 빌드한 파일과 원본 리소스를 서로 연결하여 디버깅 간 편의성을 제공해주는 도구이다.
  > Webpack을 통한 번들링(대부분 빌드와 번들링은 동일한 개념으로 취급)을 하면서 오류가 발생할 경우, 빌드를 완료한 후 오류를 감지한다(동적감지).
  > Source Map을 활용하면 원본 리소스와 연결이 되어, 오류가 발생한 파일 및 라인을 감지해낼 수 있다(정적감지).
- Webpack의 필수적인 설정은 어떤 식으로 이루어져 있을까요?

  > entry:webapack이 번들을 시작하는 지점이자 경로이다. entry 객체를 통해 모듈을 로딩하고 하나의 파일로 묶는다.
  > output:entry 객체에 정의된 번들 항목(경로)을 묶은 후, 최종 결과물을 반환할 위치이다.
  > loader:Webpack이 기존 번들할 수 있는 속성(Javascript, JSON)뿐만 아니라, HTML/CSS/Image 등 까지 번들할 수 있도록 관련 기능을 지원해준다. 파일 해석에 관한 추가적인 기능을 제공한다.
  > plugin:Webpack의 기본적인 동작 외 추가적인 기능을 제공한다.결과물의 형태를 바꿔주는 기능을 제공하는데, 번들 최적화/환경 변수 주입 등의 작업을 Plugin을 통해 수행할 수 있다.

  - Webpack의 플러그인과 모듈은 어떤 역할들을 하나요?
    > 기존 브라우저에서 모듈을 완벽히 지원하지 못하여 이를 보완하기 위해 Webpack에서 제공하는 기능이다.
    > 기본적으로 모듈시스템에 대한 호환성을 넓히고, 지원해준 개념으로 생각하면 되는데, 모듈시스템 모두 번들링할 수 있도록 지원하는 기능을 제공한다.
    > commonJS, ES6 등의 모듈시스템에 대해 지원해줄 수 있다.

- Webpack을 이용하여 HMR(Hot Module Replacement) 기능을 설정하려면 어떻게 해야 하나요?
  > webpack.config.js의 hot 옵션 true 지정한다.

## Quest

- 직전 퀘스트의 소스만 남기고, Vue의 Boilerplating 기능을 쓰지 않고 Webpack 관련한 설정을 원점에서 다시 시작해 보세요.
  - 필요한 번들링과 Source Map, HMR 등의 기능이 모두 잘 작동해야 합니다.

## Advanced

- Webpack 이전과 이후에는 어떤 번들러가 있었을까요? 각각의 장단점은 무엇일까요?
