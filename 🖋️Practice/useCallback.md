## 🪵 [React-Hooks] useCallback

<hr>

<br>

> 모두 애플리케이션의 `성능을 최적화`하는 데 사용되는 내장 후크

> 핵심은 그것들을 `적절하고 올바른 장소`에서 사용하는 것

> 후크를 불필요하게 사용하면 잠재적으로 `성능 저하`로 이어질 수 있는 오버헤드가 발생

<br>

> 종속성 중 하나가 변경된 경우에만 변경되는 콜백 함수의 메모화된 버전을 반환

<br>
<hr>

<br>
<br>

### *`# 사용하면 도움되는 경우`*

<br>

```
- 하위 구성 요소에 소품으로 전달되는 함수가 있으며 해당 하위 구성 요소는 PureComponent이거나 React.memo를 사용

- 해당 함수의 정의로 인해 자식 구성 요소가 불필요하게 리렌더링될 때

- 해당 함수의 정의 자체는 계산 비용이 많이 지불 될 때
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

- `자식 구성 요소의 props 변경 최적화` <br>
함수 참조를 유지하여 자식 구성 요소에서 불필요한 다시 렌더링을 방지

```javascript
import React, {useMemo} from 'react';

const ChildComponent = React.memo(({onClick}) => {
    // ...
})

const ParentComponent = () => {
    const handleClick = () => console.log('Clicked');

    const memorizedHandleClick = useCallback(handleClick, []);

    return <ChildComponent onClick={memorizedHandleClick} />
}
```

- 설명
```
부모 컴포넌트가 함수를 
자식 컴포넌트로 전달할 때 
함수가 렌더링할 때마다 
다시 생성되면 자식 컴포넌트는 
실제 데이터가 변경되지 않은 경우에도 
매번 새 소품을 볼 때 리렌더링 

여기에서 useCallback을 사용하여 
렌더링 간에 동일한 함수 참조를 유지하여 
자식 구성 요소에서 불필요한 다시 렌더링을 방지
```


<br>

- `useEffect 의 무한 루프 방지` <br>
useCallback을 사용하면 함수의 참조가 렌더링 간에 동일하게 유지되어 무한 루프를 방지

```javascript
const Component = () => {
    const [count, setCount] = useState(0);

    const incrementCount = () => setCount((c) => c+1);

    const memorizedIncrementCount = useCallback(incrementCount, [setCount]);

    useEffect(()=>{
       memorizedIncrementCount(); 
    },[memorizedIncrementCount])
}
```

- 설명
```
useEffect 후크 내부에서 사용되는 함수가 
컴포넌트 내부에서 정의되면 모든 렌더링에서 
다시 생성되어 useEffect가 다시 실행되고 
잠재적으로 무한 루프로 이어질 수 있음

useCallback을 사용하면 
함수의 참조가 렌더링 간에 
동일하게 유지되어 무한 루프를 방지 가능
```

<br>


<br>

- `큰 리스트에 대한 이벤트 처리기` <br>
useCallback은 함수 ID가 렌더링 간에 동일하게 유지되도록 하는 데 도움

```javascript
const ListItem = ({item, onClick}) => {
    <div onClick={onClick}>{item.name}</div>
}

const ListComponent = ({ items }) => {
    const handleClick = useCallback((item) => {

    }, []);

    return items.map((item) => (
        <ListItem key={item.id} item={item} onClick={() => handleClick(item)}>
    ));
}
```

- 설명
```
큰 목록에 항목의 데이터에 액세스해야 하는 
이벤트 처리기가 있는 경우 렌더링할 때마다 
각 항목에 대해 새 함수를 만들면 
속도가 느려질 가능성 존재 

useCallback은 함수 ID가 렌더링 간에 동일하게 유지되도록 하는 데 도움 가능
```


