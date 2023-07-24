<img src="../Image/react_js_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>

## ▶️ useMemo 와 useCallback

---

<br>

### useMemo 는?

> 메모리제이션 값을 반환하는 React Hook

```
useMemo는 메모이제이션된 값을 반환

함수와 배열을 입력으로 받아,
배열 내부의 모든 값이 변경되지 않았다면
이전에 계산했던 값을 재사용

주로 복잡한 계산 결과를 재활용하거나,
참조 동일성이 중요한 값을 메모이제이션할 때 사용

요약 ) 계산 비용이 높은 함수의 리턴 값을 재활용하는데 사용
```

<br>

### 이점

```
useMemo는 또한 렌더링 사이에 객체
또는 배열과 같은 참조 타입의 값을
유지하는 데 사용 가능

이런 용도로 useMemo를 사용하면
자식 컴포넌트가 불필요하게
다시 렌더링되는 것을 피할 수 있음
```

<br>

### 주의 사항

> 너무 많이 사용하면 메모리 사용량이 늘어나며, 메모이제이션 자체도 비용이 들 수 있으므로 신중하게 사용해야 함

<br>

### 사용코드

```javascript
import React, { useMemo } from "react";

function App() {
  const [number, setNumber] = React.useState(0);

  const expensiveComputation = useMemo(() => {
    let result = 0;
    for (let i = 0; i < 1000000000; i++) {
      result += i;
    }
    return result;
  }, [number]); // number가 변경될 때마다 expensiveComputation이 다시 계산됩니다.

  return (
    <div>
      <p>Expensive computation result: {expensiveComputation}</p>
      <p>Number: {number}</p>
      <button onClick={() => setNumber(number + 1)}>Increase Number</button>
    </div>
  );
}

export default App;
```

---

```javascript
const ExampleComponent = ({ list }) => {
  const [filter, setFilter] = useState("");

  const filteredList = useMemo(() => {
    return list.filter((item) => item.includes(filter));
  }, [list, filter]);

  return (
    <div>
      <input onChange={(e) => setFilter(e.target.value)} />
      {filteredList.map((item) => (
        <p>{item}</p>
      ))}
    </div>
  );
};
```

---

<br>

### useCallback 은?

> 함수를 메모이제이션하는 데에 사용하는 React Hook

```
useCallback은 또한 두 개의 인자를 받음

첫 번째는 함수이고,
두 번째는 의존성 배열

useCallback의 반환값은 첫 번째 인자인 함수 그 자체

의존성 배열의 요소가 변경될 때만
첫 번째 인자인 함수를 다시 생성

의존성 배열의 요소가 변경되지 않았다면
이전에 생성한 함수를 재사용

요약 ) 함수를 메모리제이션함으로 불필요한 함수 생성을 피하므로 성능 최적화에 도움
```

<br>

### 이점

```
자식 컴포넌트에 함수를 전달할 때 유용

useCallback 없이 함수를 전달하면
부모 컴포넌트가 렌더링될 때마다
함수가 다시 생성되므로,
자식 컴포넌트가 불필요하게 다시 렌더링
```

<br>

### 주의 사항

> 너무 많이 사용하면 메모리 사용량이 늘어나며, 메모이제이션 자체도 비용이 들 수 있으므로 신중하게 사용해야 함

<br>

### 사용코드

```javascript
import React, { useState, useCallback } from "react";

function App() {
  const [number, setNumber] = useState(0);

  const increment = useCallback(() => {
    setNumber(number + 1);
  }, [number]); // number가 변경될 때마다 increment 함수가 다시 생성됩니다.

  return (
    <div>
      <p>Number: {number}</p>
      <button onClick={increment}>Increase Number</button>
    </div>
  );
}

export default App;
```

---

```javascript
const ChildComponent = React.memo(({ doSomething }) => {
  console.log("ChildComponent re-rendered");
  return <button onClick={doSomething}>Do Something</button>;
});

const ParentComponent = () => {
  const [count, setCount] = useState(0);

  const doSomething = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <ChildComponent doSomething={doSomething} />
    </div>
  );
};
```

<br>

### 총 주의 사항

> useMemo와 useCallback을 사용하면 성능 최적화를 달성할 수 있지만, 이러한 Hook들은 '최적화'를 위한 것이므로, 실제 성능 문제가 발생할 때까지 사용을 보류하는 것이 일반적인 베스트
