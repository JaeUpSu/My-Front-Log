<img src="../Image/graphql.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `GraphQL 알아보자`

<br>

* **정의**
* **기능**
* **설치**
* **사용**

<br>

> 정의

```
API용 오픈 소스 데이터 쿼리 및 조작 언어
기존 데이터로 이러한 쿼리를 실행하기 위한 런타임

2012년 Facebook에서 개발했으며 2015년에 공개
GraphQL은 REST에 대한 효율적이고 강력한 대안을 제공하며 
복잡하고 관계형이며 계층적인 데이터 세트를 처리할 때 
상당한 이점을 제공

GraphQL을 사용하면 
필요한 것을 정확히 요청할 수 있으므로 
기존 REST API에 비해 데이터를 과도하게 가져오거나 
적게 가져오지 않음

또한 단일 요청으로 여러 소스의 데이터를 집계 가능
```
<br>

<br>


> 기능

- `강력한 타이핑`
```
API 를 예측 가능하고 쉽게 사용 가능
```
- `클라이언트 지정 쿼리`
```
클라이언트는 필요한 데이터를 정확히 지정하므로 
네트워크를 통해 전송해야 하는 
데이터의 양을 줄일 수 있음
```
- `계층적`
```
쿼리 구조는 중첩된 데이터 요구 사항을 
관리하기 훨씬 쉽게 만드는 데이터 구조와 일치
```
- `Introspective`
```
사용 가능한 스키마에 대한 정보를 제공하는 API 기능
도구를 통해 GraphQL API를 탐색
```
<BR>

```
클라이언트(프론트엔드)와 
데이터 소스(백엔드) 사이의 중간 계층 역할

REST API와 같이 고정된 구조를 가진 
여러 엔드포인트를 갖는 대신 

GraphQL은 단일 엔드포인트만 노출하고 
클라이언트는 요청에 필요한 데이터를 지정
이 데이터 구조는 클라이언트에서 보낸 쿼리에서 정의
```
<br>

> 설치
```
npm install apollo-server graphql
```

<br>

> 사용

`스키마 정의`
```
const { gql } = require('apollo-server');

const typeDefs = gql`
  type Book {
    title: String
    author: String
  }

  type Query {
    books: [Book]
  }
`;
```

`리졸버 정의`
```
const resolvers = {
  Query: {
    books: () => [
      {
        title: "Harry Potter and the Chamber of Secrets",
        author: "J.K. Rowling",
      },
      {
        title: "Jurassic Park",
        author: "Michael Crichton",
      },
    ],
  },
};
```

`ApolloServer 객체 생성`
```
const { ApolloServer } = require('apollo-server');

const server = new ApolloServer({ typeDefs, resolvers });

server.listen().then(({ url }) => {
  console.log(`🚀 Server ready at ${url}`);
});
```

`쿼리 보내기`
```
query {
  books {
    title
    author
  }
}
```

<br>

> HTTP 메서드

`GraphQL과 함께 사용되는 두 가지 기본 HTTP 메서드`
```

GET / POST

- GraphQL의 읽기 작업인 쿼리 실행에 GET 메서드를 사용 가능

- 쿼리와 변형(GraphQL의 쓰기 작업)은 일반적으로 POST 요청을 통해 전송
POST 요청을 통해 구독 작업을 보낼 수도 있지만 
실시간 데이터를 위해 WebSocket 연결로 업그레이드
```
