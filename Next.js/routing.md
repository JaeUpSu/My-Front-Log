<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `라우팅을 알아보자`

<br>


* **정의**
* **종류**
* **사용법**

<br>

> 정의

```
웹 애플리케이션에서 사용자 요청에 따라 
적절한 페이지나 컴포넌트로 이동하는 과정

사용자가 특정 URL을 요청하면 
해당 URL에 맞는 내용을 보여주기 위해 
라우팅이 필요
```

<br>
<br>

> 종류

<br>


&nbsp;&nbsp;`CSR`
```
클라이언트 측 라우팅

*브라우저에서 이루어지며, 
JavaScript를 사용하여 페이지 전환을 처리

주로 싱글 페이지 애플리케이션(SPA)에서 사용

초기 페이지 로딩 이후에는 
서버로부터 데이터를 받아와 
동적으로 페이지를 업데이트 가능
```


&nbsp;&nbsp;`언제 사용하면 돼?`
```
클라이언트 측 라우팅

일반적인 페이지 전환 시에는 
CSR을 사용하는 것이 최적

* 정적 컨텐츠를 가진 페이지
* 적은 양의 동적 데이터를 가진 페이지
* 요청 시점에 데이터를 가져오는 페이지
   => CSR을 이용하는 것이 Good
```

<br>
<br>

&nbsp;&nbsp;`SSR`
```
서버 측 라우팅

*서버에서 URL 요청을 처리하고 
적절한 페이지를 렌더링하여 클라이언트에 전달

각 URL에 대해 서버는 적절한 핸들러 
또는 컨트롤러를 호출하여 요청을 처리

페이지가 서버에서 사전 렌더링되어 
클라이언트에 전달되기 때문에 
초기 로딩 속도와 검색 엔진 최적화에 유리
```


&nbsp;&nbsp;`언제 사용하면 돼?`
```
서버 측 라우팅

* INDEX 페이지 
* 데이터를 많이 처리하는 페이지에 
   => SSR을 이용하는 것이 Good
```

<br>
<br>


> 사용법

<br>

&nbsp;&nbsp;`pages`
```
기본은 파일 시스템 기반이지만
라우터가 제공하는 기능을 사용하여 구현

pages 디렉토리 내의 파일 구조가 
URL 경로와 일치

각 파일은 해당 경로에 대한 컴포넌트를 정의
```

<br>

&nbsp;&nbsp;`Link`
```
Link 컴포넌트를 사용하여 내부 링크를 처리
```
```javascript
import Link from 'next/link';

<Link href="/about">
  <a>About</a>
</Link>
```
<br>

&nbsp;&nbsp;`useRouter `
```
현재 경로와 쿼리 매개변수를 가져옴
```
```javascript
import { useRouter } from 'next/router';

const MyComponent = () => {
  const router = useRouter();
  
  // 현재 경로 가져오기
  const currentPath = router.pathname;
  
  // 쿼리 매개변수 가져오기
  const query = router.query;

  return (
    <div>
      <p>Current Path: {currentPath}</p>
      <p>Query: {JSON.stringify(query)}</p>
    </div>
  );
};
```