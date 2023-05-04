# Quest 02. CSS의 기초와 응용

## Introduction

- CSS는 Cascading StyleSheet의 약자입니다. 웹브라우저에 표시되는 HTML 문서의 스타일을 지정하는 (거의) 유일하지만 다루기 쉽지 않은 언어입니다. 이번 퀘스트를 통해 CSS의 기초적인 레이아웃 작성법을 알아볼 예정입니다.

## Topics

- CSS의 기초 문법과 적용 방법
  - Inline, `<style>`, `<link rel="stylesheet" href="...">`
- CSS 규칙의 우선순위
- 박스 모델과 레이아웃 요소
  - 박스 모델: `width`, `height`, `margin`, `padding`, `border`, `box-sizing`
  - `position`, `left`, `top`, `display`
  - CSS Flexbox와 Grid
- CSS 표준의 역사
- 브라우저별 Developer tools

## Resources

- [MDN - CSS](https://developer.mozilla.org/ko/docs/Web/CSS)
- [Centering in CSS: A Complete Guide](https://css-tricks.com/centering-css-complete-guide/)
- [A complete guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [그리드 레이아웃과 다른 레이아웃 방법과의 관계](https://developer.mozilla.org/ko/docs/Web/CSS/CSS_Grid_Layout/%EA%B7%B8%EB%A6%AC%EB%93%9C_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83%EA%B3%BC_%EB%8B%A4%EB%A5%B8_%EB%A0%88%EC%9D%B4%EC%95%84%EC%9B%83_%EB%B0%A9%EB%B2%95%EA%B3%BC%EC%9D%98_%EA%B4%80%EA%B3%84)

## Checklist

- CSS를 HTML에 적용하는 세 가지 방법은 무엇일까요?
  > 인라인 스타일 시트:HTML 태그의 style 속성에 css 코드를 넣는 방법이다.
  > 내부 스타일 시트:HTML 문서 안의 <style></style>안에 css 코드를 넣는 방법이다.
  > 외부 스타일 시트:별도의 css 파일을 만들고 HTML 문서와 연결하는 방법이다.
  - 세 가지 방법 각각의 장단점은 무엇일까요?
    > 인라인 스타일 시트:해당 태그가 선택자 되고, css코드에는 속성과 값이 들어간다. 꾸미는 데 한계가 있으며, 재사용이 불가능하다.
    > 내부 스타일 시트:HTML 문서 안의 여러 요소를 한번에 꾸밀 수 있다. 하지만 다른 HTML 문서에는 적용할 수 없다.
    > 외부 스타일 시트:여러 HTML 문서에 사용할 수 있다. style.css를 적용시키고 싶은 문서에 <link> 태그 연결만 해주면 된다.
- CSS 규칙의 우선순위는 어떻게 결정될까요?

  > 1. 적용 방법에 따른 우선순위

  > > 1. 인라인 스타일 시트
  > > 2. 내부/ 외부 스타일 시트 -> <head> 태그 안에 위치에 따라 결정
  > > 3. 웹 브라우저 기본 스타일

  > 2.  적용 범위에 따른 우선순위

  > > 1. !important -> 어떤 스타일보다 가장 우선으로 적용되는 스타일
  > > 2. 인라인 스타일 -> 1000
  > > 3. id -> 100
  > > 4. 클래스 -> 10
  > > 5. 태그 -> 1

- CSS의 박스모델은 무엇일까요? 박스가 화면에서 차지하는 크기는 어떻게 결정될까요?
  > 웹페이지에 배치하는 모든 HTML 엘리먼트는 3개의 층을 가진 사각형 구조의 형태를 띠고 있다.
  > 가장 외곽의 층을 margin 영역으로 보통 주변에 위치한 다른 엘리먼트와의 상하 좌우 간격을 두기 위해서 쓰인다. 그 바로 아래 층을 border 영역이라고 부른다. 이 영역은 경계선을 그리기 위해서 쓰이며, 다른 영역과 달리 두께 뿐만 아니라 색상과 모양까지 지정할 수 있다. 그 아래 층은 padding 영역이라고 불리는데, 컨텐츠와 경계선 사이의 간격을 지정하기 위해서 쓰인다. 마직막 영역은 content 영역으로, 컨텐츠의 width와 height를 지정해 줄 수 있다.
- `float` 속성은 왜 좋지 않을까요?
  > 모든 자식 요소에 float 속성을 적용하면, 부모 요소는 해당 자식 요소가 존재하지 않는 것으로 판단하여, 부모 요소가 높이를 인식하지 못하는 문제가 발생함
- Flexbox(Flexible box)와 CSS Grid의 차이와 장단점은 무엇일까요?
  > Flex는 1차원으로 수평,수직 영역 중 하나의 방향으로만 레이아웃을 나눌 수 있다. 반면에 Grid는 2차원으로 수평 수직을 동시에 영역을 나눌 수 있다.
- CSS의 비슷한 요소들을 어떤 식으로 정리할 수 있을까요?
  > 그룹화, 클래스 선택자로 그룹을 만들어서 정리

## Quest

- Quest 01에서 만들었던 HTML을 바탕으로, [이 그림](screen.png)의 레이아웃과 CSS를 최대한 비슷하게 흉내내 보세요. 꼭 완벽히 정확할 필요는 없으나 align 등의 속성은 일치해야 합니다.
- **주의사항: 되도록이면 원래 페이지의 CSS를 참고하지 말고 아무것도 없는 백지에서 시작해 보도록 노력해 보세요!**

## Advanced

- 왜 CSS는 어려울까요?
- CSS의 어려움을 극복하기 위해 어떤 방법들이 제시되고 나왔을까요?
- CSS가 브라우저에 의해 해석되고 적용되기까지 내부적으로 어떤 과정을 거칠까요?
- 웹 폰트의 경우에는 브라우저 엔진 별로 어떤 과정을 통해 렌더링 될까요?
