<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `dehydrate 를 알아보자`

<br>


* **정의**
* **순서**
* **코드**

<br>

> 정의

``` 
클라이언트 측에서 
서버에서 미리 가져온 데이터를 재사용하는 것

초기 데이터 요청을 생략

페이지 로딩 속도 ↑
네트워크 요청 ↓
성능 ↑
```

<br>
<br>

> 순서

<br>

## &nbsp;&nbsp;`SSR`
```
서버 사이드 렌더링 기능을 사용하여 
페이지를 서버에서 초기 렌더링

필요한 데이터를 서버에서 
가져와 페이지의 초기 상태로 설정
```
<br>

## &nbsp;&nbsp;`클라이언트 측에서 데이터 재사용`
```
페이지가 서버에서 클라이언트로 전환될 때, 

Next.js는 이전에 렌더링된 페이지의 
상태를 가져와서 클라이언트 측에서 재사용

이를 통해 초기 데이터 요청을 생략하고 
페이지를 더 빠르게 로드
```

<br>
<br>

> 코드

<br>

## &nbsp;&nbsp;`페이지 컴포넌트에서 데이터 가져오기`<br>
```javascript
import { GetServerSideProps, NextPage } from 'next';

type PageProps = {
  data: string;
};

const Page: NextPage<PageProps> = ({ data }) => {
  return (
    <div>
      <h1>Data: {data}</h1>
    </div>
  );
};

export const getServerSideProps: GetServerSideProps<PageProps> = async () => {
  // 서버에서 데이터 가져오는 로직
  const data = 'Hello, World';

  // 데이터를 props로 전달하여 페이지 컴포넌트 렌더링
  return {
    props: {
      data,
    },
  };
};

export default Page;
```


<br>

## &nbsp;&nbsp;`클라이언트에서 데이터 재사용`<br>
```javascript
import { dehydrate } from 'react-query/hydration';
import { QueryClient } from 'react-query';
import { GetServerSidePropsContext, InferGetServerSidePropsType } from 'next';

type PageProps = {
  data: string;
};

const Page = ({ data }: InferGetServerSidePropsType<typeof getServerSideProps>) => {
  return (
    <div>
      <h1>Data: {data}</h1>
    </div>
  );
};

export const getServerSideProps = async (context: GetServerSidePropsContext) => {
  const queryClient = new QueryClient();

  // 서버에서 데이터 가져오는 로직
  const data = 'Hello, World';

  // 데이터를 캐시에 저장
  await queryClient.prefetchQuery('data', async () => data);

  // 데이터를 props로 전달하여 페이지 컴포넌트 렌더링
  return {
    props: {
      data,
      dehydratedState: dehydrate(queryClient),
    },
  };
};

export default Page;
```

```
InferGetServerSidePropsType
 ㄴ> 함수의 반환 형식을 유추하는 데 사용
     이 형식을 사용하면 의 반환 형식을 
     수동으로 지정할 필요없음

GetServerSidePropsContext
 ㄴ> 요청 매개 변수, 헤더, 쿠키 등과 
     같은 요청에 대한 정보가 포함
     
     이 컨텍스트 개체를 사용하면 
     들어오는 요청에 액세스하고 
     서버 쪽 논리를 수행
     
     데이터를 가져오거나 다른 작업을 수행

NextPage
 ㄴ> 페이지 구성 요소가 수신하는 
     props의 유형을 지정할 수 있는 제네릭 유형
```