<img src="../../Image/redux_logo.png" style="object-fit: cover" width="100%"/>

<br>
<br>

# ⚒️  `Redux 알아보자`

<br>


* **정의**
* **설치**
* **사용예시**
* **주의**

<br>

> 정의
<br>

```
Node.js 모듈
애플리케이션 상태를 관리하는 데 도움
```
<br>

> 설치
<br>

```
npm install redux react-redux
```

<br>

> 규칙
<br>

&nbsp;&nbsp;`Actions`
```
수행할 작업의 종류를 설명하는 
'type' 필드와 추가 정보 또는 데이터를 나타내는 
기타 필드가 있는 일반 JavaScript 개체
```
```javascript
// actions.js
export const increment = () => ({
  type: 'INCREMENT'
});

export const decrement = () => ({
  type: 'DECREMENT'
});
```
<br>

&nbsp;&nbsp;`Reducer`
```
현재 상태와 동작을 취한 다음 
새로운 상태를 반환하는 함수
상태를 직접 변경해야 하는 유일한 위치
```
```javascript
// reducer.js
const initialState = { value: 0 };

function counterReducer(state = initialState, action) {
  switch (action.type) {
    case 'INCREMENT':
      return { value: state.value + 1 };
    case 'DECREMENT':
      return { value: state.value - 1 };
    default:
      return state;
  }
}

export default counterReducer;
```
<br>

&nbsp;&nbsp;`Store`
```
액션과 리듀서를 함께 가져오는 객체
애플리케이션 상태를 유지하고 
상태에 액세스하고 작업을 디스패치하고 
리스너를 등록하는 몇 가지 도우미 메서드를 제공
일반적으로 Redux 앱에는 하나의 스토어만 존재
```
```javascript
// store.js
import { createStore } from 'redux';
import counterReducer from './reducer';

const store = createStore(counterReducer);

export default store;
```
<br>

&nbsp;&nbsp;`App`

```javascript
// App.js
import React from 'react';
import { useSelector, useDispatch } from 'react-redux';
import { increment, decrement } from './actions';

function App() {
  const counter = useSelector(state => state.value);
  const dispatch = useDispatch();

  return (
    <div>
      <p>Counter: {counter}</p>
      <button onClick={() => dispatch(increment())}>Increment</button>
      <button onClick={() => dispatch(decrement())}>Decrement</button>
    </div>
  );
}

export default App;
```

&nbsp;&nbsp;`Index.js`

```javascript
// index.js
import React from 'react';
import ReactDOM from 'react-dom';
import { Provider } from 'react-redux';
import store from './store';
import App from './App';

ReactDOM.render(
  <Provider store={store}>
    <App />
  </Provider>,
  document.getElementById('root')
);
```
<br>

> 주의

<br>

- Redux를 과도하게 사용 X , 앱의 여러 부분에서 필요한 상태 또는 관리하기 복잡한 상태에 사용

- Redux 툴킷 사용,  Redux 코드를 크게 단순화하고 상용구를 줄이기 가능

- 리듀서를 순수하게 유지, 리듀서는 순수 함수여야 하며 부작용 X

- 상태 형태 정규화, 복잡한 데이터를 다룰 때는 상태를 가능한 한 평평하게 유지하는 것을 목표

- 비동기 작업에 미들웨어 사용, redux-thunk 또는 redux-saga와 같은 라이브러리는 Redux 애플리케이션에서 비동기 작업 및 부작용을 처리 가능

- 파생 데이터에 선택기 함수 사용, 선택기를 사용하여 Redux 스토어에서 파생 데이터를 계산 가능

- 리듀서 및 작업 단위 테스트, 리듀서는 순수 함수이므로 단위 테스트가 쉽고 액션 생성자와 선택자를 테스트 해야 함