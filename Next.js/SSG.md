<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `SSG 를 알아보자`

<br>


* **정의**
* **장점**
* **사용법**
* **코드**
* **빌드**

<br>

> 정의

``` 
Static Site Generation

빌드 시점에 페이지를 렌더링하여 
정적인 HTML 파일을 생성하는 방식

서버에 대한 요청 없이 초기 로딩 시 
미리 준비된 정적 콘텐츠를 제공

getStaticProps 를 사용
```

<br>
<br>

> 장점

<br>

## &nbsp;&nbsp;`초기 로딩 속도 개선`
```
사전에 준비된 정적 콘텐츠를 제공
초기 로딩 속도를 개선
```
<br>

## &nbsp;&nbsp;`서버 부하 감소`
```
동일한 콘텐츠에 대한 
반복적인 서버 요청을 피할 수 있음
```
<br>

## &nbsp;&nbsp;`검색 엔진 최적화(SEO)`
```
정적 페이지를 제공하기 때문에 
검색 엔진이 쉽게 색인
```

<br>
<br>


> 사용법

<br>

```
자주 변경되는 콘텐츠에는 적합 X
  (해당 콘텐츠에는 CSR 이 적합)

외부 API 호출 등 비동기 데이터 요청은 
getStaticProps 함수 내에서 처리
```
<br>
<br>


> 코드

<br>

```javascript
// pages/index.js
import React from 'react';

const Home = ({ data }) => {
  return (
    <div>
      <h1>Welcome to my website!</h1>
      <p>{data}</p>
    </div>
  );
};

export async function getStaticProps() {
  // 외부 데이터 소스로부터 데이터를 가져옵니다.
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();

  // 페이지 컴포넌트에 필요한 데이터를 props로 전달합니다.
  return {
    props: {
      data,
    },
  };
}

export default Home;
```
<br>
<br>


> 빌드

<br>

```
next build 명령을 실행
정적 페이지를 생성

이 과정에서 getStaticProps 함수가 실행
데이터를 가져와 정적 페이지에 포함

빌드 타임에서 사전 생성
```

<br>
<br>

📢 자주 변경 안되는 동적 경로를 지원하는 페이지의 경우 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SSG(Static Site Generation)가 많은 경우에 적합<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ex) &nbsp; [id].tsx 
