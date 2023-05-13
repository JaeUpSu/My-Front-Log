<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Coin SSR of ReactMaster Project`

<br>


* **정의**
* **기능**

<br>


> 정의

```
ReactMaster 에서
Coin API 를 사용에 있어서
SSR 을 적용

dahydrate 는 재사용

QueryClient 를 선언해
prefetchQuery 를 사용하여 SSR 구현
```
<br>
<br>

> 기능

<br>

## &nbsp;&nbsp; `Data 사용중인 컴포넌트`
```javascript
export default function Home() {
  const { data: coins, isLoading } = useQuery(["coins"], getAllCoins);
  return (
    <Container>
      <Seo title="Home" />
      <Header>
        <Title>코인</Title>
      </Header>
      <CoinList>
        {!isLoading &&
          coins?.map((coin: ICoin) => (
            <Coin key={coin.id}>
              <Link href={`/${coin.id}`}>{coin.name} &rarr;</Link>
            </Coin>
          ))}
      </CoinList>
    </Container>
  );
}
```

<br>

## &nbsp;&nbsp; `SSR`
```javascript
interface Props {
  dehydratedState: DehydratedState | null;
  data: ICoin[] | null | undefined;
}

export async function getServerSideProps(): Promise<
  GetServerSidePropsResult<Props>
> {
  try {
    const queryClient = new QueryClient();
    await queryClient.prefetchQuery(["coins"], getAllCoins);

    return {
      props: {
        dehydratedState: dehydrate(queryClient),
        data: queryClient.getQueryData(["coins"]),
      },
    };
  } catch (e) {
    console.log("Error in coins ssr func", e);

    return {
      props: {
        dehydratedState: null,
        data: null,
      },
    };
  }
}
```
<br>