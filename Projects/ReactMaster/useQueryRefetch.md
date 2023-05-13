<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Styled-Components of ReactMaster Project`

<br>


* **정의**
* **사용코드**
* **기능**

<br>


> 정의

```
Next.js 에서 
Styled-Components 를 사용한다면

SSR(서버 쪽 렌더링) 중에 스타일이 
지정된 각 구성 요소에 고유한 해시를 
자동으로 추가하기 때문에 발생

 => Prop `className` did not match.
```
<br>
<br>

> 사용코드

```javascript
const { data, isLoading } = useQuery(["ohlcv", coinId], getCoinHistory, {
  refetchInterval: 10000,
});
```

<br>

> 기능

<br>

## &nbsp;&nbsp; `자동 refetch`
```javascript
const { data, refetch } = useQuery("myData", fetchMyData, {
  refetchInterval: 5000, // 5초마다 자동 refetch
});
```

<br>

## &nbsp;&nbsp; `수동 refetch`
```javascript
const { data, refetch } = useQuery("myData", fetchMyData);

const handleButtonClick = () => {
  refetch(); // 버튼 클릭 시 수동 refetch
};
```
<br>

## &nbsp;&nbsp; `외부요소 refetch`
```javascript
const { data } = useQuery("myData", fetchMyData);

// 다른 컴포넌트에서 refetch 함수를 받아서 사용
<OtherComponent refetch={refetch} />

// OtherComponent 내부에서 refetch 함수 호출
const { refetch } = props;
const handleButtonClick = () => {
  refetch(); // 외부 요소에서 refetch
};
```