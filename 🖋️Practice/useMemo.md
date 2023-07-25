## 🪵 [React-Hooks] useMemo

<hr>

<br>

> 모두 애플리케이션의 `성능을 최적화`하는 데 사용되는 내장 후크

> 핵심은 그것들을 `적절하고 올바른 장소`에서 사용하는 것

> 후크를 불필요하게 사용하면 잠재적으로 `성능 저하`로 이어질 수 있는 오버헤드가 발생

<br>

<hr>

<br>
<br>

### *`# 사용하면 도움되는 경우`*

<br>

```
- 값을 반환하고 특히 계산 비용이 많이 드는 함수

- props/state 를 기반으로 하는 비용이 많이 드는 계산에서 파생된 값이 있으며 모든 렌더링에서 해당 값을 다시 계산하고 싶지 않을 때
```

<br>
<br>

### **`✔️ 주의 사항`**

<br>

> 최적화하기 전에 항상 성능을 측정할 것

> lighthouse 같은 툴을 이용할 것


<br>
<br>

### < 연습 >

<br>

- `복잡한 계산` <br>
복잡한 계산을 수행하는 함수가 있고 함수가 특정 값(props, state)에 의존하는 경우 useMemo가 편리

```javascript
import React, {useMemo} from 'react';

const ComplextComponent = ({list}) => {
    const sortedList = useMemo(() => {
        return list.sort((a,b) => a-b);
    }, [list])

    return (
        <div>
            {sortedList.map((item, idx) => <div key={idx}>{item}</div>)}
        </div>
    )
}

export default ComplextComponent;
```

- 설명
```
컴포넌트가 리렌더링될 때마다 정렬 작업을
다시 실행하지 않도록 useMemo 를 사용

list 에서 변화가 감지되는 경우에만
다시 실행 => Memorization
```


<br>

- `참조 동등성` <br>
경우에 따라 props 또는 state 에서 파생된 값이 있고 종속성이 변경되지 않는 한 렌더링 간에 동일하게 유지

```javascript
import React, {useMemo} from 'react';

const ParentComponent = ({a, b}) => {
    const childProp = useMemo(() => {
        return {a, b};
    }, [a, b])

    return (
        <ChildComponent prop={childProp} />
    )
}

const ChildComponent = React.memo({prop}) => {
    return <div>{prop.a} - {prop.b}</div>
}

export default ParentComponent;
```

- 설명
```
useMemo 는 a 또는 b 가 변경되지 않는 한
prop 객체가 ParentComponent 의 렌더링에서
참조 ID 를 유지하도록 하는 데 사용

ChildComponent 는 메모된 구성 요소이므로
prop 을 생성하기 위해 useMemo 를 사용하지 
않으면 ParentComponent 가 리렌더링될 때마다
불필요하게 리렌더링 됨

그래서, useMemo를 사용하여 prop이 모든 렌더링이 아니라 a 또는 b가 변경될 때만 변경되도록 하여 ChildComponent의 불필요한 리렌더링을 방지
```

<br>
<br>

### < useMemo 와 React.memo > 

<br>

- 둘은 다르며 다른 용도로 사용됨

<hr>

- useMemo 는 렌더링 때마다 비용이 많이 드는
계산을 피하기 위해 기능적 구성 요소에서 할 수 있는 React 후크

<hr>

- React.memo 는 상위 컴포넌트
- props 가 변경된 경우에만 컴포넌트를 리렌더링
- props 가 변경되지 않는 경우 마지막 렌더링 결과를 재사용
- 부모 컴포넌트가 렌더링 되지만 props 가 그대로 유지될 때 불필요한 렌더링을 피하기 위해 사용

```javascript
import React from "react";

const MyComponent = React.memo(function MyComponent(props) {
  /* render using props */
});
```
- 추가설명
```
특정 구성 요소가 불필요한 재 렌더링으로 인해 
성능 문제를 일으키고 구성 요소의 소품이 깊게 중첩된 개체 
또는 배열이 아닌 경우 'React.memo'를 사용하는 것이 좋습니다. 
일반적으로 모든 컴포넌트에 무조건 
React.memo를 사용하는 것은 좋지 않습니다.
```