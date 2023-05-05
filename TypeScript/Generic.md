<img src="../Image/ts.png" style="object-fit: cover" width="100%"/>

<br>
<br>


# ⚒️  `제네릭을 알아보자`

<br>


* **정의**
* **사용이유**
* **장점**
* **기능**
* **Generic &nbsp; vs &nbsp; Any**

<br>

> 정의


```
[Generic] 

구문은 꺾쇠 괄호 <>를 사용
그 안에 Generic Type 매개변수를 지정하는 것


예를 들어, 
다음은 제네릭 유형 T를 사용하는 간단한 함수
'T' 유형의 인수를 취하고 동일한 유형을 반환

[CODE]

function identity<T>(arg: T): T {
  return arg;
}
```

<br>

> 사용이유

```
여러 유형에서 작동할 수 있는 
재사용 가능한 코드를 작성 가능 

제네릭을 사용하면 하나의 특정 유형이 아닌 
모든 데이터 유형과 함께 작동할 수 있는 
유형 또는 함수를 정의
```

<br>

> 장점

```
[재사용성]

    여러 데이터 유형과 함께 
    사용할 수 있는 코드를 작성할 수 있으므로 
    중복 코드의 필요성이 줄어듬
    
[유형 안전성] 
    
    TypeScript가 사용 중인 
    데이터의 유형을 유추하고 확인하여 
    오류 위험을 줄이기

[유연성] 
    
    다양한 상황과 요구 사항에 맞게 
    조정할 수 있는 함수 또는 유형을 만들기 가능



📢 단점

잠재적인 단점 중 하나는 
특히 개념에 익숙하지 않은 개발자의 경우 
코드를 더 복잡하고 이해하기 어렵게 만들 수 있다는 것

배열은 모든 유형의 데이터를 
포함할 수 있기 때문에 유형 안전성을 제공 X
```
<br>

> 기능

<br>

- 함수 & 컴포넌트
- 기본값 설정

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`함수 & 컴포넌트`

```
🎚️ [함수]

타입이 정해지지 않은 배열을 받아 
첫 번째 요소를 반환하는 함수를 작성

function getFirstElement<T>(array: T[]): T | null {
    return array.length > 0 ? array[0] : null;
}


🧱 [컴포넌트]

리스트를 렌더링하는 React 컴포넌트가 있다고 가정
다양한 타입의 아이템을 받아 처리 가능

interface ListProps<T> {
    items: T[];
    renderItem: (item: T) => React.ReactNode;
}

function List<T>(props: ListProps<T>) {
    return (
        <ul>
            {props.items.map((item, index) => (
                <li key={index}>{props.renderItem(item)}</li>
            ))}
        </ul>
    )
}

const numbers = [1, 2, 3];
const strings = ['a', 'b', 'c'];

function App() {
    return (
    <div>
        <List items={numbers} renderItem={(item) => <span>{item * 2}</span>} />
        <List items={strings} renderItem={(item) => <strong>{item.toUpperCase()}</strong>} />
    </div>
    );
}
```

<br>

&nbsp;&nbsp;&nbsp;&nbsp;`기본값 설정` 
```
function example<T = string>(param: T) {...}
```
<br>


<br>

> Generic &nbsp; vs &nbsp; Any

<br>

```
[중요한 차이점]
    
제네릭을 사용하면 코드를 사용할 때 
특정 유형으로 대체할 수 있는 
자리 표시자 유형을 지정 가능

유형 안전성을 희생하지 않고 
다양한 데이터 유형으로 작동하는 
유형 안전 코드를 작성 가능 


📢 변수가 any로 선언되면 본질적으로 TS 무시
    TypeScript 컴파일러에 해당 변수에 대한 유형 
    검사를 해제하도록 지시
    
    변수에 모든 유형의 데이터가 포함될 수 있어 
    유형 오류 및 버그가 발생할 수 있음을 의미
        
    제네릭을 사용하여 반환 유형을 지정하면 
    함수가 보다 유형 안전하고 재사용 가능

    - 공통점 : 제네릭과 any는 여러 데이터 유형에서 작동하는 코드를 작성하는 데 사용 가능 
    - 차이점 : 제네릭은 유형 안전성을 제공하고 더 많은 재사용 가능한 코드를 작성가능 
              any 유형은 유형 안전성을 희생하므로 드물게 사용

```