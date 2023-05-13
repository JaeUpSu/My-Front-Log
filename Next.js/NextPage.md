<img src="../Image/next_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `NextPage 를 알아보자`

<br>


* **정의**
* **설명**
* **장점**
* **코드**

<br>

> 정의

```javascript
type NextPage<P = {}, IP = P> = NextComponentType<NextPageContext, IP, P>;
```

```
P: 페이지 컴포넌트의 속성(props) 타입

IP: 초기 속성(initial props) 타입

초기 속성은 SSR 시에 
페이지 컴포넌트에 전달되는 데이터
```

<br>
<br>

> 설명

``` 
Next.js에서 제공하는 제네릭 타입 중 하나
페이지 컴포넌트를 정의할 때 사용

기본적으로 React.FC (함수형 컴포넌트)의 확장
Next.js의 라우팅 및 SSR 과 관련된 기능을 지원
```

<br>
<br>

> 장점

<br>

&nbsp;&nbsp;다양한 기능을 손쉽게 활용할 수 있고, <br>&nbsp;&nbsp;더욱 간결하고 타입 안정성이 높은 코드를 작성

<br>

## &nbsp;&nbsp;`라우팅 지원`
``` 
Next.js의 내장된 라우팅 시스템을 활용
페이지 간의 이동을 간편하게 처리
```
<br>

## &nbsp;&nbsp;`SSR 지원`
``` 
서버 사이드 렌더링을 위한 
초기 속성 데이터(getInitialProps)를 
처리하는 기능을 내장

SSR을 쉽게 구현
```
<br>

## &nbsp;&nbsp;`SSG 지원`
``` 
정적 사이트 생성 기능과 함께 
NextPage를 사용하면 정적인 페이지를 생성
```
<br>

## &nbsp;&nbsp;`TypeScript 지원`
``` 
TypeScript를 완벽하게 지원하며, 

타입 안정성을 제공하여 
개발자의 실수를 줄일 수 있음
```

<br>
<br>


> 코드

<br>

```javascript
import { NextPage } from 'next';

type Props = {
  name: string;
};

const MyPage: NextPage<Props> = ({ name }) => {
  return <div>Hello, {name}!</div>;
};

export default MyPage;
```