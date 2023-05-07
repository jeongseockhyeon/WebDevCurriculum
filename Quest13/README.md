# Quest 13. 웹 API의 응용과 GraphQL

## Introduction

- 이번 퀘스트에서는 차세대 웹 API의 대세로 각광받고 있는 GraphQL에 대해 알아보겠습니다.

## Topics

- GraphQL
  - Schema
  - Resolver
  - DataLoader
- Apollo

## Resources

- [GraphQL](https://graphql.org/)
- [GraphQL.js](http://graphql.org/graphql-js/)
- [DataLoader](https://github.com/facebook/dataloader)
- [Apollo](https://www.apollographql.com/)

## Checklist

- GraphQL API는 무엇인가요? REST의 어떤 단점을 보완해 주나요?
  > GraphQL은 API용 쿼리 언어이자 해당 쿼리를 처리하는 런타임입니다.
  > GraphQL은 REST가 가지는 치명적인 단점인 여러 개의 엔드포인트를 단일 엔드포인트화 하여 한 번의 엔드포인트 접근으로 원하는 data를 얻을 수 있도록 한다. (엔드 포인트가 여러개 일시 필요없는 정보까지 얻는 overfetching 혹은 부족한 정보를 얻게 되는 underfetching을 겪게 된다)
- GraphQL 스키마는 어떤 역할을 하며 어떤 식으로 정의되나요?
  > GraphQL에서 스키마는 넓게는 데이터모델링을 하는 작업, 좁게는 원하는 데이터를 얻기 위한 쿼리문을 정의하는 작업이다. 이때 데이터 모델링은 GraphQL 상에서 data를 불러오기 위한 type(형태, 속성 등)을 정의하는 것, 이를 위해 데이터벵스에 해당 데이터를 구성해주는 과정이다.
  > type을 이용하여 정의한다
- GraphQL 리졸버는 어떤 역할을 하며 어떤 식으로 정의되나요?
  > GraphQL에서 설계한 쿼리를 사용하여 data를 얻기 위해 실질적으로 사용하는 data 확보도구이다.
  - GraphQL 리졸버의 성능 향상을 위한 DataLoader는 무엇이고 어떻게 쓰나요?
    > N+1문제, 여러 데이터를 얻기 위해 과도하게 query 반복이 이루어지지 않도록 최적화된 데이터 조회/접근을 해주는 기능을 일컫는다.
    > Batch:여러 데이터들을 조회하기 위한 각각의 요청들을 하나로 모은 후, 단일 요청으로 보내고 해당 결과값들을 확보한다.
    > Cashe:요청항목 중 기존에 요청과 중복되는 것이 있다면, 이를 Caching하여(미리 기억에 저장하고 있다가, 중복 요청이 생기면 특정) 접근한다
    > 위와 같은 방법으로 Database에서 DataLoader가 요청을 한 곳으로 모으고, 이 요청을 fetch하는 과정으로 접근이 이루어진다.
- 클라이언트 상에서 GraphQL 요청을 보내려면 어떻게 해야 할까요?
  > 기본적으로 GraphQL에서 정의한 쿼리문, 이를 통해 데이터를 확보하는 작업은 모두 백엔드에서 정적으로 이루어진다.
  > 하지만 필요에 따라 동적으로 변수를 추가하거나 확보하는 작업이 필요하다면, client 측에서도 요청을 보내고 변수를 얻을 수 있다.
  - Apollo 프레임워크(서버/클라이언트)의 장점은 무엇일까요?
    > GraphQL과 함계 사용할 수 있는 호환성이 매우 높고, 이를 통해 효율적으로 data를 확보할 수 있다.
  - Apollo Client를 쓰지 않고 Vanilla JavaScript로 GraphQL 요청을 보내려면 어떻게 해야 할까요?
    > fetch,axios과 같은 데이터 전달 module 및 REST API(GET/POST method) 등 data를 확보할 수 있는 별도의 모듈을 사용해야 한다.
- GraphQL 기반의 API를 만들 때 에러처리와 HTTP 상태코드 등은 어떻게 하는게 좋을까요?
  > server 접속 및 모든 요청처리 성공( status code - 200)
  > GraphQL server / apollo server initialization 실패처리
  > REST API 실패처리
  > resolver가 정의되어있지 않는 변수/객체를 반환하는 오류

## Quest

- 메모장의 서버와 클라이언트 부분을 GraphQL API로 수정해 보세요.

## Advanced

- GraphQL이 아직 제대로 수행하지 못하거나 불가능한 요구사항에는 어떤 것이 있을까요?
- GraphQL의 경쟁자에는 어떤 것이 있을까요?
