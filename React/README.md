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

<br>
<br>

> Props Getters Pattern

```
Custom hook pattern이 엄청난 통제권
하지만, 그만큼 컴포넌트를 이용하기 어려움 

Props Getters Pattern은 이런 복잡도를 감싸기 위해 시도
native props를 노출하는 대신 props getters의 목록을 제공

이는 유저가 올바른 JSX요소에 접근할 수 있도록 
의미있는 이름을 사용
```

```javascript
import React from "react";
import { Counter } from "./Counter";
import { useCounter } from "./useCounter";

const MAX_COUNT = 10;

function Usage() {
    const {count, getCounterProps, getIncrementProps, getDecrementProps} = useCounter({ initial:0, max: MAX_COUNT });

    const handleBtn1Clicked = () => {
        console.log("btn 1 clicked");
    }

    return (
        <>
            <Counter {...getCounterProps()}>
                <Counter.Dcrement
                    icon={"minus"}
                    {...getDecrementProps()}
                />
                <Counter.Label>Counter</Counter.Label>
                <Counter.Count />
                <Counter.Increment 
                    icon={"plus"}
                    {...getIncrementProps()}
                />
            </Counter>
            <button {...getIncrementProps({ onClick: handleBtn1Clicked })}>
                Custom increment btn 1
            </button>
            <button {...getIncrementProps({ disabled: count > MAX_COUNT - 2 })}>
                Custom increment btn 2
            </button>
        </>
    )
}

export {Usage}
```

- `장점`

```
사용하기 쉬움

올바른 getter 를 그에 맞는 
JSX 요소에 사용하기만 하면 됨

---

유연함 

유저는 원한다면 props를 오버로드
```

- `단점`

```
불투명 

물론 getters를 통한 추상화는 
컴포넌트를 사용하기 쉽게 만들어주지만 
결국 더 불투명

---

내부 로직에 대한 이해

정확하게 오버라이드하기 위해서는 
getters에 의해 제공된 prop 리스트와 
하나가 바뀔 때 생기는 내부에서의 
로직 변화를 알아야 함
```

<br>
<br>

> State reducer Pattern

```
IoC에 있어서는 최고의 패턴
이 패턴은 유저에게 컴포넌트를 
내부적으로 제어할 수 있는 더 발전된 방법을 제시

코드는 Custom Hook Pattern과 비슷해보이지만, 
더 나아가 유저가 Hook을 통해 전달된 reducer를 정의
이 reducer는 컴포넌트 내의 모든 action들을 오버로드
```

```javascript
import React from "react";
import { Counter } from "./Counter";
import { useCounter } from "./useCounter";

const MAX_COUNT = 10;

function Usage() {
    const reducer = (state, action) => {
        switch (action.type) {
            case "decrement" :
                return {
                    count : Math.max(0, state.count - 2)
                };
            default :
                return useCounter.reducer(state, action);
        }
    }

    const { count, handleDecrement, handleIncrement } = useCounter(
        { initial: 0, max: 10 },
        reducer
    );

    return (
        <>
            <Counter value={count}>
               <Counter.Decrement icon={"minus"} onClick={handleDecrement} />
               <Counter.Label>Counter</Counter.Label>
               <Counter.Count />
               <Counter.Increment icon={"plus"} onClick={handleIncrement} />
            </Counter>
            <button onClick={handleIncrement} disabled={count === MAX_COUNT}>
              Custom increment btn 1
            </button>
        </>
    )
}

export {Usage}
```

- `장점`

```
더 많은 통제권

엄청나게 복잡한 경우에서 
state reducer를 사용하는 것은 
유저에게 통제권을 남겨주는 최고의 방법

모든 내부 action들은 
이제 외부에서 접근가능하며 오버라이드
```

- `단점`

```
이 패턴은 확실히 유저와 
개발자 모두에게 가장 복잡한 패턴

reducer의 액션이 바뀔 수 있기 때문에, 
컴포넌트 내부 로직에 대한 깊은 이해가 필요
```

<br>
<br>
<br>

> 큰 힘에는 큰 책임이 따른다

<br>

# Summary

<br>

> Compound Components Pattern

```
# 설명

불필요한 prop drilling 없이 
task를 수행하기 위해 다 같이 함께 
작동하는 컴포넌트를 생성

각각의 prop 을 때려넣고 자식 컴포넌트에
주는 것 보다 각각의 서브 컴포넌트에 넣는 방법
------------------------------------------
# prop drilling

props를 오로지 하위 컴포넌트로 전달하는 용도

------------------------------------------
# 사용 

select, dropdown 컴포넌트 또는 메뉴 
아이템들에서 이러한 형태

------------------------------------------
# 장단점

장 - 자유도 높음
단 - 예상치 못한 행동 유발 가능
```

<br>

> Control Props Pattern

```
# 설명

유저로 하여금 커스텀 로직을 삽입 가능
component의 상태를 제어할 수 있는 컴포넌트
------------------------------------------
# 사용 

Form, Toggle, Input 컴포넌트
------------------------------------------
# 장단점

장 - 더 많은 통제권
단 - JSX, useState, handleChange 세 곳 모두를 체크
```
<br>

> Custom Hook Pattern

```
# 설명

Hook은 State, Handler와 같은 내부 로직들을 
포함하며 유저에게 더 많은 통제권
------------------------------------------
# 사용 

Form, Toggle, Input 컴포넌트
------------------------------------------
# 장단점

장 - 더 많은 통제권
단 - JSX, useState, handleChange 세 곳 모두를 체크
```
<br>
<br>
<br>
<br>

> Framework 선정 이유

- React

```
=> 페이스북이나 인스타그램과 유사한 대규모 소셜 네트워킹 플랫폼을 구축

높은 수준의 유연성과 사용자 지정 가능성이 필요한 경우.
복잡한 상태의 대규모 애플리케이션을 구축하려는 경우.
대규모 커뮤니티, 풍부한 리소스 및 타사 라이브러리의 혜택을 받고 싶을 때.
팀이 JavaScript 및 함수형 프로그래밍에 익숙한 경우.
```

- Vue

```
=> 지나치게 복잡하지 않은 전자 상거래 플랫폼을 구축하고자 
   하지만 여전히 정교하고 현대적이며 대화형 사용자 인터페이스를 원하는 중소기업

이해하기 쉽고 시작하기 쉬운 프레임워크가 필요할 때.
가이드 프레임워크와 유연성 간의 균형을 원하는 경우.
응용 프로그램이 복잡하지 않고 더 빠른 렌더링과 더 가벼운 무게를 원하는 경우.
명확하고 포괄적인 문서를 원할 때.
```

- Angular

```
=> 다양한 다른 소프트웨어 및 시스템과 통합해야 하고 
   대규모 개발자 팀에 의해 유지 관리

코드를 구성하는 방법을 안내하는 완전하고 독단적인 프레임워크를 원할 때.
대규모 엔터프라이즈급 애플리케이션을 구축하는 경우.
팀이 TypeScript 및 객체 지향 프로그래밍에 익숙한 경우.
종속성 주입, 국제화(i18n) 등과 같은 즉시 사용 가능한 기능을 원하는 경우
```