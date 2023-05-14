<img src="../../Image/frontend-dev.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `useMatch of ReactMaster Project`

<br>


* **정의**
* **코드**

<br>


> 정의

```
useMatch는 주로 라우팅 로직에서 사용

예를 들어, 특정 경로에 대한 
조건부 렌더링이나 활성화된 
메뉴 항목 표시 등을 
구현할 때 유용
```
<br>
<br>

> 코드

<br>

## &nbsp;&nbsp; `예시코드`
```javascript
import { useMatch } from 'react-router-dom';

function MyPage() {
  const match = useMatch('/mypage');

  if (match) {
    return <div>내 페이지 컴포넌트</div>;
  } else {
    return <div>다른 페이지 컴포넌트</div>;
  }
}
```

<br>

## &nbsp;&nbsp; `실전코드`
```javascript
  const homeMatch = useMatch("/");
  const tvMatch = useMatch("/tv");
  ...

          <Items>
          <Item>
            <Link to="/">Home {homeMatch && <Circle layoutId="circle" />}</Link>
          </Item>
          <Item>
            <Link to="/tv">
              Tv Shows {tvMatch && <Circle layoutId="circle" />}
            </Link>
          </Item>
        </Items>
```
<br>