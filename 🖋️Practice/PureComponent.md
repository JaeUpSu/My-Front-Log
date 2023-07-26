## 🪵 [React] PureComponent

<hr>

<br>

> 클래스 구성 요소의 렌더링 프로세스를 최적화

> 불필요한 렌더링을 방지 

> 얕은 소품과 상태 비교로 shouldComponentUpdate를 구현

> state 또는 props에 대한 참조가 변경 사항이 있는지 확인

> 변경 사항이 없으면 구성 요소를 리렌더링 X


<br>
<hr>

<br>
<br>


### *`# 사용하면 도움되는 경우`*

<br>

```
- 큰 애플리케이션

  앱의 초기 로딩 시간이 느려질 수 있어
  코드 분할은 초기 번들 크기를 줄이는 데 도움

--------------------------------------------  

- 항상 필요하지 않는 무거운 컴포넌트

  무겁지만 항상 필요하지 않은 
  컴포넌트가 있는 경우 React.lazy 를 
  사용하여 필요할 때만 로드 가능

--------------------------------------------  

- 경로

  가장 일반적인 사용 -> 라우팅
  특정 경로에 대한 코드가 해당 경로를 방문할때만
  로드되도록 각 경로를 쉽게 코드 분할

--------------------------------------------  

- 큰 타사 라이브러리

  앱에서 초기 렌더링에 필요하지 않은
  큰 타사 라이브러리를 사용하는 
  느리게 로드가 좋음
```


<br>
<br>

### **`✔️ 주의 사항`**

<br>

- `중첩 데이터`
```
상태와 소품에 대한 얕은 비교만 수행하므로 
복잡한 객체나 중첩 데이터가 있는 경우 
중첩 데이터가 변경될 때 포착하지 못할 가능성 존재
```

- `고려사항`
```
최적화를 위한 좋은 도구이지만 묘책 X 
여전히 데이터 구조와 컴포넌트가 설계되는 방식을 고려
```

- `props 또는 state 가 동일할 때`
```
React.PureComponent의 shouldComponentUpdate()는 
props 또는 state가 동일할 때 렌더링을 건너 뜀

변경 가능한 값에 의존할 때 버그가 발생할 수 있으므로 
가능하면 변경 불가능한 값을 사용
```

- `기능적 컴포넌트의 출현 (function)`
```
React의 Hooks 및 기능적 컴포넌트의 출현으로 
React.memo 상위 함수는 PureComponent가 
클래스 컴포넌트에 대해 수행하는 것과 
유사한 기능적 컴포넌트에 대한 목표를 달성
```

<br>
<br>

### < 연습 >

<br>

- `state 또는 props 객체` <br>
객체 자체의 실제 내용이 아니라 state 또는 props 객체에 대한 참조가 변경되었는지 확인

```javascript
import React, { PureComponent } from 'react';

class MyComponent extends PureComponent {
  render() {
    // Your render code here
  }
}
```

<br>
<br>

<hr>

<br>

### Q. PureComponent 라 하면 부모 컴포넌트가 렌더링 하지만 props 랑 state 는 그대로 값이 유지될 때 PureComponent 의 불필요한 렌더링이 안되게 방지하는 거지?

<br>

```
네, 맞습니다! React.PureComponent는 기본적으로 shouldComponentUpdate 메서드를 구현합니다. 이 메서드는 구성 요소의 현재 props 및 state를 다음 props 및 state와 얕은 비교를 수행합니다. 비교 결과 변경 사항이 없는 것으로 나타나면 'React.PureComponent'가 구성 요소가 다시 렌더링되지 않도록 합니다
```