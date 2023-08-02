<img src="../Image/react_js_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>

## ▶️ Pattern 과 Framework 선정

---

<br>

```
Q. 어떻게 하면 재사용가능한 컴포넌트를 
   각각 다른 use case들에 맞도록 만들 수 있을까?

Q. 어떻게 하면 컴포넌트를 
   간단한 API로 쓰기 쉽게 만들 수 있을까?

Q. 어떻게 하면 UI와 기능성의 측면에서 
   확장 가능한 컴포넌트를 만들 수 있을까?
```

<br>

### Pattern 는?

<br>

> Compound Components Pattern

```
이 패턴은 불필요한 prop drilling 없이 
Expressive 하고 Declarative 한 컴포넌트를 
만들 수 있게 도움 

만약 좀 더 customizable 하고 관심사를 
분리하도록 하고 싶다면 이 패턴을 고려
```

- `prop drilling`

```
App 컴포넌트에서 
C컴포넌트에게 데이터를 주고 싶을 때, 
A와 B에는 필요없지만 C 컴포넌트에게 
데이터를 주고 싶을 때, 상위 컴포넌트에서 
프로퍼티를 아래로 내려 꽂듯이 데이터를 전달해주는 것
```

```javascript
import React from "react";
import { Counter } from "./Counter";

function Usage() {
    const handleChangeCounter = (count) => {
        console.log("count", count);
    }

    return (
        <Counter onChange={handleChangeCounter}>
            <Counter.Decrement icon='minus' />
            <Counter.Label>Counter</Counter.Label>
            <Counter.Count max={10} />
            <Counter.Increment icon='plus' />
        </Counter>
    )
}

export { Usage };
```

- `장점`

```
API 복잡도가 낮음
하나의 거대한 부모 컴포넌트에 
모든 prop을 때려넣고 자식 컴포넌트에 
꽂아주는 방법보다 각각의 prop이 
각각의 서브컴포넌트에 붙어있는 방법이 더 좋음
```

- `비교`

```javascript
// 이렇게 쓰는 것보다
return (
  <Counter
    label="label"
    max={10}
    iconDecrement="minus"
    iconIncrement="plus"
    onChange={handleChangeCounter}
  />
);

// 이렇게 쓰는게 낫다!
return (
  <Counter onChange={handleChangeCounter}>
    <Counter.Decrement icon={"minus"} />
    <Counter.Label>Counter</Counter.Label>
    <Counter.Count max={10} />
    <Counter.Increment icon={"plus"} />
  </Counter>
);
```

- `사용`

```javascript

// [- Counter 0 +]
<Counter>
    <Counter.Decrement />
    <Counter.Label>Counter</Counter.Label>
    <Counter.Count />
    <Counter.Increment />
</Counter>

// [- + Counter 0]
<Counter>
    <Counter.Decrement />
    <Counter.Increment />
    <Counter.Label>Counter</Counter.Label>
    <Counter.Count />
</Counter>

// [- +]
<Counter>
    <Counter.Decrement />
    <Counter.Increment />
</Counter>
```

- `장 ) 컴포넌트 자유도 ↑↑↑`

- `단 ) 너무 높은 자유도, 예상치 못한 행동 유발 가능`


<br>
<br>

> Control Props Pattern

```
이 패턴은 컴포넌트를 controlled component로 바꿔줌 
외부 상태는 single source of truth, SSOT로 사용되어 
유저로 하여금 커스텀 로직을 삽입 가능
```

- `Controlled component`

```
component의 상태를 제어할 수 있는 컴포넌트를 의미
```

- `SSOT`

```
단일 진실 공급원이라고도 번역되는데, 
이는 모든 데이터 요소를 한 곳에서만 제어, 
편집하도록 하는 것
```

```javascript
import React, { useState } from "react";
import { Counter } from "./Counter";

function Usage() {
    // 1
    const [count, setCount] = useState(0);

    // 2
    const handleChangeCounter = (newCount) => {
        setCount(newCount);
    }

    return (
     // 3
     <Counter value={count} onChange={handleChangeCounter}>
        <Counter.Decrement icon={"minus"} />
        <Counter.Label>Counter</Counter.Label>
        <Counter.Count max={10} />
        <Counter.Increment icon={"plus"} />
     </Counter>
    )
}

export { Usage };
```

- `장점`

```
더 많은 통제권
```

- `단점`

```
JSX, useState, handleChange 세 곳 모두를 체크
```


<br>
<br>

> Custom Hook Pattern

```
좀 더 IoC에 집중
메인 로직은 이제 custom hook으로 들어감 

Hook은 State, Handler와 같은 내부 로직들을 
포함하며 유저에게 더 많은 통제권을 줌
```

```javascript
import React from "react";
import { Counter } from "./Counter";
import { useCounter } from "./useCounter";

function Usage() {
    const {count, handleIncrement, handleDecrement} = useCounter(0);
    const MAX_COUNT = 10;

    const handleClickIncrement = () => {
        if (count < MAX_COUNT) {
            handleIncrement();
        }
    }

    return (
        <>
            <Counter value={count}>
                <Counter.Dcrement
                    icon={"minus"}
                    onClick={handleDecrement}
                    disabled={count === 0}
                />
                <Counter.Label>Counter</Counter.Label>
                <Counter.Count />
                <Counter.Increment 
                    icon={"plus"}
                    onClick={handleClickIncrement}
                    disabled={count === MAX_COUNT}
                />
            </Counter>
            <button onClick={handleClickIncrement} disabled={count === MAX_COUNT}>
            Custom increment btn 1
            </button>
        </>
    )
}

export {Usage}
```

- `장점`

```
더 많은 제어권
hook과 JSX 사이에 자신만의 로직 삽입 가능
```

- `단점`

```
올바르게 사용하기 위해서는 컴포넌트가 
어떻게 동작하는지 알아야할 필요
```

