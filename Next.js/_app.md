<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `_app.tsx 를 알아보자`

<br>


* **정의**
* **기능**
* **최적화**
* **코드**

<br>

> 정의

``` 
Next.js 애플리케이션의 
최상위 컴포넌트로 사용되는 파일

이 파일을 사용하여 
모든 페이지에 대한 공통 레이아웃, 
상태 관리, 글로벌 스타일링 등을 설정
```

<br>
<br>

> 기능

<br>

## &nbsp;&nbsp;`페이지 레이아웃 설정`
```
모든 페이지의 최상위 컴포넌트로 사용

여기에서 페이지 레이아웃을 설정 가능 

예를 들어, 네비게이션 바, 푸터, 공통 
스타일링 등을 포함 가능 

이를 통해 페이지 간에 
공통된 레이아웃을 유지하고 
코드 중복을 피하기 가능
```
<br>

## &nbsp;&nbsp;`글로벌 상태 관리`
```
상태 관리 라이브러리를 초기화하고 
상태를 관리

Redux나 Recoil과 
같은 상태 관리 라이브러리를 사용하여 
전역 상태를 관리 가능
```
<br>

## &nbsp;&nbsp;`글로벌 스타일링`
```
CSS-in-JS 라이브러리인 styled-components 
또는 emotion을 사용하여 글로벌 스타일을 정의 가능 

이를 통해 애플리케이션 전체에 일관된 스타일을 적용
```

<br>
<br>


> 최적화

<br>

## &nbsp;&nbsp;`필요한 최소한의 외부 종속성 사용`
```
불필요한 외부 종속성은 
번들 크기를 증가시키고 
초기 로딩 속도를 저하
```
<br>

## &nbsp;&nbsp;`코드 스플리팅`
```
페이지에 따라 필요한 코드만 로드하여 
초기 로딩 속도를 최적화

Next.js는 자동으로 코드 스플리팅을 지원, 
필요한 설정만 적절히 해야 함
```
<br>

## &nbsp;&nbsp;`SSR 사용`
```
_app.tsx 파일에서 
서버 사이드 렌더링을 설정 가능 

SSR을 사용하면 
초기 로딩 속도와 검색 엔진 최적화에 도움

페이지가 서버에서 완전히 렌더링된 상태로 
클라이언트에 전달

이를 통해 사용자가 페이지를 빠르게 볼 수 있으며,
검색 엔진에서도 페이지의 콘텐츠를 인덱싱 가능
```
<br>
<br>



> 코드

<br>

&nbsp;&nbsp;&nbsp; Recoil 이랑 react-query 사용할 때
```javascript
import { AppProps } from 'next/app';
import { QueryClient, QueryClientProvider } from 'react-query';
import { RecoilRoot } from 'recoil';
import GlobalStyles from '../styles/GlobalStyles';

const queryClient = new QueryClient();

function MyApp({ Component, pageProps }: AppProps) {
  return (
    <QueryClientProvider client={queryClient}>
      <RecoilRoot>
        <GlobalStyles />
        <Component {...pageProps} />
      </RecoilRoot>
    </QueryClientProvider>
  );
}

export default MyApp;
```
<br>

📢  SSR은 필요한 경우에만 사용하는 것이 좋습니다. 
<br>모든 페이지에 SSR을 적용하면 <br>
서버 부하가 증가할 수 있으므로, <br><br>SSR이 필요한 페이지에만 getServerSideProps를 <br>사용하는 것이 좋음

<br><br>
📢  일반적인 정적 컨텐츠를 렌더링하는 페이지의 경우, <br>정적 생성(Static Generation)을 사용하여 <br>초기 로딩 속도와 성능을 향상