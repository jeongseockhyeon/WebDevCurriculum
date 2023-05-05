# Quest 03. 자바스크립트와 DOM

## Introduction

- 자바스크립트는 현재 웹 생태계의 근간인 프로그래밍 언어입니다. 이번 퀘스트에서는 자바스크립트의 기본적인 문법과, 자바스크립트를 통해 브라우저의 실제 DOM 노드를 조작하는 법에 대하여 알아볼 예정입니다.

## Topics

- 자바스크립트의 역사
- 기본 자바스크립트 문법
- DOM API
  - `document` 객체
  - `document.getElementById()`, `document.querySelector()`, `document.querySelectorAll()` 함수들
  - 기타 DOM 조작을 위한 함수와 속성들
- 변수의 스코프
  - `var`, `let`, `const`

## Resources

- [자바스크립트 첫걸음](https://developer.mozilla.org/ko/docs/Learn/JavaScript/First_steps)
- [자바스크립트 구성요소](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Building_blocks)
- [Just JavaScript](https://justjavascript.com/)

## Checklist

- 자바스크립트는 버전별로 어떻게 변화하고 발전해 왔을까요?
  > ES1 ~ ES3 : 대부분 브라우져에서 지원/클로져/ES3에서 tre/catch문법 추가
  > ES5: 배열 forEach,map,fiter,reduce,some 메소드 추가/객체 Object에 대한 getter/setter추가/bind 메소드 추가/JSON추가/strict moce 추가/es5-shim 사용 시 하위 버전에서 특정 기능 지원
  > ES6: let,const 키워드 추가/arrow 문법 지원/iterator,generator추가/module import,export 추가/callback hell을 해결할 Promise 추가/MS에서도 최대한 ECMAScript를 따르는 브라우저 IE Edge 발표
  > ES7:제곱연산자 추가/Array.includse 추가
  > ES8:async,await 추가/이후 나오는 표준은 ES.Next라함
  - 자바스크립트의 버전들을 가리키는 ES5, ES6, ES2016, ES2017 등은 무엇을 이야기할까요?
    > 1990년대 Netscape는 Javascript를, MS사의 IE에서는 JSscript를 사용했고 두 스크립트는 제각각이었기에 표준이 필요했다. 그래서 개발된 것이 ECMA(European Computer Maufactures Association)으로 ES(ECMAScript)는 자바스크립트 언어의 표준이다
  - 자바스크립트의 표준은 어떻게 제정될까요?
    > 자바스크립트의 발전 방향을 결정하고 새로운 기능의 제안을 검토하며, 최신 기술들을 추진하는 방향으로 제정한다.
- 자바스크립트의 문법은 다른 언어들과 비교해 어떤 특징이 있을까요?
  > 자바스크립트는 동적인 언어이고, 프로토타입을 기반으로한 객체지향 언어이며 자바스크립트는 동기적인 특성을 가졌고 작성 순서대로 실행하는 특징을 가지고 있다. 또한 추가적인 환경 설정 필요 없이 브자우저에서 동작함
  - 자바스크립트에서 반복문을 돌리는 방법은 어떤 것들이 있을까요?
    > for,while,do-while
- 자바스크립트를 통해 DOM 객체에 CSS Class를 주거나 없애려면 어떻게 해야 하나요?
  > 할당:classList.add()
  > 제거:classList.remove()
  - IE9나 그 이전의 옛날 브라우저들에서는 어떻게 해야 하나요?
    > IE9에서는 지원되지 않는 않으므로, polyfill(자바스크립트를 오래된 브라우저에서 사용가능 하게 하는 기능)을 이용
- 자바스크립트의 변수가 유효한 범위는 어떻게 결정되나요?
  > 유효한 범위는 함수 내부 혹은 외부에서 선언하는지에 따라 결정된다. 지역 변수는 함수 내부에서 선언, 전역 변수는 함수 외부에서 선언되는 변수이다.
  - `var`과 `let`으로 변수를 정의하는 방법들은 어떻게 다르게 동작하나요?
    > var은 중복 선언 가능하여 변수의 보호가 불가능 하다
    > let은 중복 선언이 불가능 하지만 초기화하여 다른 값을 재할당 할 수 있다.
- 자바스크립트의 익명 함수는 무엇인가요?
  > 익명 함수는 변수에 함수의 코드를 저장하는 대신 함수명을 사용하지 않는다. 대신 변수명을 마치 함수명처럼 사용해서 함수를 호출하거나 변수값을 이동시키는데 사용할 수 있다.
  - 자바스크립트의 Arrow function은 무엇일까요?
    > arrow function은 function 키워드 대신 화살표(=>)를 사용하여 보다 간략한 방법으로 함수를 선언할 수 있다.
    > 사용하면 안되는 경우: 콜백 함수로 사용하기 편리하지만 메소드 정의하는 경우,prototype에 메소드를 할당하는 경우,addEventListener함수의 콜백 함수 등에는 사용할 수 없다.

## Quest

- (Quest 03-1) 초보 프로그래머의 영원한 친구, 별찍기 프로그램입니다.
  - [이 그림](jsStars.png)과 같이, 입력한 숫자만큼 삼각형 모양으로 콘솔에 별을 그리는 퀘스트 입니다.
    - 줄 수를 입력받고 그 줄 수만큼 별을 그리면 됩니다. 위의 그림은 5를 입력받았을 때의 결과입니다.
  - `if`와 `for`와 `function`을 다양하게 써서 프로그래밍 하면 더 좋은 코드가 나올 수 있을까요?
  - 입력은 `prompt()` 함수를 통해 받을 수 있습니다.
  - 출력은 `console.log()` 함수를 통해 할 수 있습니다.
- (Quest 03-2) skeleton 디렉토리에 주어진 HTML을 조작하는 스크립트를 완성해 보세요.
  - 첫째 줄에 있는 사각형의 박스들을 클릭할 때마다 배경색이 노란색↔흰색으로 토글되어야 합니다.
  - 둘째 줄에 있는 사각형의 박스들을 클릭할 때마다 `enabled`라는 이름의 CSS Class가 클릭된 DOM 노드에 추가되거나 제거되어야 합니다.
- 구현에는 여러 가지 방법이 있으나, 다른 곳은 건드리지 않고 TODO 부분만 고치는 방향으로 하시는 것을 권장해 드립니다.

## Advanced

- Quest 03-1의 코드를 더 구조화하고, 중복을 제거하고, 각각의 코드 블록이 한 가지 일을 전문적으로 잘하게 하려면 어떻게 해야 할까요?
- Quest 03-2의 스켈레톤 코드에서 `let` 대신 `var`로 바뀐다면 어떤 식으로 구현할 수 있을까요?
