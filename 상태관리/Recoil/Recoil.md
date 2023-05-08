<img src="../../Image/recoil_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `Recoil 알아보자`

<br>


* **정의**
* **환경설정**
* **사용법**
* **최적화**

<br>


> 정의

```
페이스북에서 개발한 
React 상태 관리 라이브러리

단순하고 직관적인 API를 제공
복잡한 상태 관리를 쉽게 할 수 있도록 도움
```
<br>

> 환경설정
```
npm install recoil
```
<br>

```javascript
import React from 'react';
import { RecoilRoot } from 'recoil';
import App from './App';

function Root() {
  return (
    <RecoilRoot>
      <App />
    </RecoilRoot>
  );
}

export default Root;
```

<br>
<br>


> 사용법

- Atom 정의
- 상태 사용
- 상태 읽기

<br>

&nbsp;&nbsp;&nbsp;`Atom 정의`
```javascript
import { atom } from 'recoil';

const counterState = atom({
  key: 'counterState',
  default: 0,
});
```
<br>

&nbsp;&nbsp;&nbsp;`상태 사용`
```javascript
import React from 'react';
import { useRecoilState } from 'recoil';
import { counterState } from './atoms';

function Counter() {
  const [count, setCount] = useRecoilState(counterState);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}
```
<br>

&nbsp;&nbsp;&nbsp;`상태 읽기`
```javascript
import React from 'react';
import { useRecoilValue } from 'recoil';
import { counterState } from './atoms';

function CounterDisplay() {
  const count = useRecoilValue(counterState);

  return <p>Count: {count}</p>;
}
```
<br>
<br>

> 사용법

<br>

- 상태의 원자성 유지
- 상태의 세분화
- 선택적 렌더링
- 비동기 상태 관리
- Devtools 활용

<br>

&nbsp;&nbsp;&nbsp;`상태의 원자성 유지`
```
상태를 작은 단위로 나누어 
원자적인 상태로 관리하는 것이 Good!

상태 간의 의존성이 줄어들어 
병렬로 업데이트가 가능
```
<br>

&nbsp;&nbsp;&nbsp;`상태의 세분화`
```
필요한 컴포넌트에만 
해당 상태를 제공하는 것이 Good!

컴포넌트 간의 결합도가 낮아지고, 
관리가 용이
```
<br>

&nbsp;&nbsp;&nbsp;`선택적 렌더링`
```
상태에 따라 선택적으로 컴포넌트를 렌더링

상태에 따라 컴포넌트의 가시성을 제어하는 방식
유연하고 동적인 UI를 구현
```
<br>


&nbsp;&nbsp;&nbsp;`비동기 상태관리`
```
selector를 사용
비동기 작업의 결과를 상태로 관리

의존하는 상태가 변경될 때만 재계산

상태 간의 의존성을 관리
불필요한 재계산을 방지하여 성능을 향상

비동기 작업의 결과를 처리하는 데 유용
```
<br>

&nbsp;&nbsp;&nbsp;`Devtools 활용`
```
개발자 도구를 제공
상태의 변화를 모니터링하고 디버깅

상태의 변화를 시각적으로 추적
상태의 흐름을 이해하고 최적화
```
<br>