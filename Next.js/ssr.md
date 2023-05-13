<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `SSR 를 알아보자`

<br>


* **정의**
* **장점**
* **사용법**
* **코드**
* **CSR / SSG 비교**

<br>

> 정의

``` 
서버 사이드 렌더링( SSR )을 지원
웹 페이지를 렌더링하는 방식 중 하나

getServerSideProps 를 사용
```

<br>
<br>

> 장점

<br>

## &nbsp;&nbsp;`검색 엔진 최적화(SEO)`
```
서버 측에서 렌더링된 HTML을 제공
 
 => 검색 엔진 크롤러가 페이지의 콘텐츠를 
    이해하고 색인하기 쉬움
```
<br>

## &nbsp;&nbsp;`초기 로딩 속도 개선`
```
클라이언트에서 자바스크립트를 다운로드 후
실행하는 대신 서버에서 완성된 HTML을 제공

 => 초기 로딩 속도가 향상
```
<br>

## &nbsp;&nbsp;`사용자 경험 개선`
```
서버에서 페이지를 렌더링

 => 사용자는 초기 페이지 로딩 이후에도 
    즉시 콘텐츠를 볼 수 있음 
    
 => 자바스크립트가 로드되는 동안 발생할 수 있는   
    깜박임 현상이나 로딩 딜레이를 최소화
```

<br>
<br>


> 사용법

<br>

```
pages 디렉토리에 위치한 페이지 컴포넌트에서 
getServerSideProps 함수를 사용하고 
필요한 데이터를 가져오는 로직을 작성

서버에서 요청이 있을 때마다 
해당 함수가 실행

데이터를 가져와 페이지를 렌더링 
이를 통해 SSR을 간편하게 구현
```
<br>
<br>


> 코드

<br>

```javascript
import React from 'react';

function MyPage({ data }) {
  return (
    <div>
      {/* 페이지 컨텐츠 */}
      <h1>{data.title}</h1>
      <p>{data.description}</p>
    </div>
  );
}

export async function getServerSideProps() {
  // 서버에서 데이터를 가져오는 비동기 로직
  const res = await fetch('https://api.example.com/data');
  const data = await res.json();

  return {
    props: {
      data, // 페이지 컴포넌트에 전달할 데이터
    },
  };
}

export default MyPage;
```
<br>
<br>


> CSR / SSG 비교

<br>

## &nbsp;&nbsp;`CSR`
```
Client-Side Rendering

클라이언트 측에서 자바스크립트를 사용
페이지를 동적으로 렌더링

초기 로딩 시 클라이언트에게 
"비어있는 HTML을 전송"

자바스크립트가 로드되면 
데이터를 가져와서 페이지를 렌더링

"사용자 상호작용이 많은 애플리케이션에 적합"

서버 부하를 줄임
```

<br>

## &nbsp;&nbsp;`SSG`
```
Static Site Generation

빌드 시점에 페이지를 사전에 렌더링
정적인 HTML 파일을 생성

이렇게 생성된 HTML 파일은 
서버에 미리 저장

클라이언트 요청 시 
"해당 정적 파일을 제공"

SSG는 페이지의 
"데이터가 자주 변경되지 않거나 
동적인 요소가 적은 경우에 적합"

빠른 로딩 속도와 SEO 향상을 위해 사용
```


<br>

## &nbsp;&nbsp;`비교`
```
SSR과 CSR 및 SSG를 적절하게 조합하여 사용 가능

SSR
  ㄴ> 초기로딩 속도 떄문에
     *동적인 페이지나 *데이터를 필요로 하는 경우에 사용

      ex) 실시간 채팅, 주식 시세 업데이트, 
          사용자 맞춤 콘텐츠 등

CSR
  ㄴ> 상호작용이 많은 부분이나 *동적으로 변경되는 
      데이터가 있는 경우에 사용 (*대량 Data)

      ex) 소셜 미디어 피드, 대시보드, 게임 등

SSG
  ㄴ> *정적인 페이지나 *데이터를 사용하는 경우에 적합
      초기 로딩 속도와 SEO 향상을 위해 활용

      ex) 블로그, 제품 목록, 문서 페이지 등
```