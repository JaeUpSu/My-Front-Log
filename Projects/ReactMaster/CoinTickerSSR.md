<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Coin & Ticker info SSR of ReactMaster Project`

<br>


* **정의**
* **기능**

<br>


> 정의

```
ReactMaster 에서
Coin & Ticker info API 를 사용에 있어서
SSR 을 적용

dahydrate 는 재사용

QueryClient 를 선언해
prefetchQuery 를 사용하여 SSR 구현
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp; `SSR`
```javascript
import {
  useQuery,
  QueryClient,
  dehydrate,
  DehydratedState,
} from "@tanstack/react-query";
import { GetServerSidePropsResult } from "next";

...

  const { data: infoData, isLoading: infoLoading } = useQuery(
    ["info", id],
    getCoinInfo,
    {
      onSuccess: (data) => {
        console.log("coin success", data);
      },
    }
  );

  const { data: priceInfoData, isLoading: priceLoading } = useQuery(
    ["ticker", id],
    getCoinTicker,
    {
      refetchInterval: 5000,
    }
  );

...

interface Props {
  params: {
    id: string | null | undefined;
    dehydratedState: DehydratedState | null;
  };
}

export async function getServerSideProps({
  params,
}: Props): Promise<GetServerSidePropsResult<Props>> {
  try {
    // TypeScript 컴파일러에게 params?.id 표현식을 string 유형인 것처럼 처리하도록 지시
    const id = params?.id as string;

    const queryClient = new QueryClient();
    await queryClient.prefetchQuery(["info", id], getCoinInfo);
    await queryClient.prefetchQuery(["ticker", id], getCoinTicker);

    return {
      props: {
        params: {
          id,
          dehydratedState: dehydrate(queryClient),
        },
      },
    };
  } catch (error) {
    // Handle the error
    console.error("Error in Coin SSR", error);
    return <p>Something went wrong...</p>;
  }
}
```