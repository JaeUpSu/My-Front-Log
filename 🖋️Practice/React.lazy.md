## 🪵 [React] lazy - Loading

<hr>

<br>

> 동적 가져오기를 일반 컴포넌트로 렌더링할 수 있는 방법

> 특히 대형 애플리케이션의 번들 크기를 줄이고 초기 로드 시간을 개선


> 사용자가 응용 프로그램과 상호 작용하는 동안 필요에 따라 또는 병렬로 로드 가능

> 다양한 청크로 코드를 분할하는 것

> 코드 분할로 성능 최적화


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

> 서버 측 렌더링에서 사용할 수 없음
    => next.js 는 dynamic 사용

> 지연로딩 (lazy-loading)

> 소형 ​​앱에서는 부적합

> 높은 대화형 컴포넌트(탐색 메뉴, 버튼 또는 입력 양식에서) 부적합

<br>
<br>

### < 연습 >

<br>

- `Suspense` <br>
Suspense 컴포넌트로 lazy 컴포넌트를 감싸고 <br>
lazy 컴포넌트가 로드되길 기다리는 동안 <br>
스피너와 같은 예비 컨텐츠 보여주기 가능

```javascript
import React, { lazy, Suspense } from 'react';

// 기존 import 방식
import Header from '../components/Header';
import Footer from '../components/Footer';

// 레이지 로딩 적용
const AudioWrite = lazy(() => import('../pages/AudioWrite'));
const Book = lazy(() => import('../pages/Book'));
const BookDetail = lazy(() => import('../pages/BookDetail'));

function App() {
    return (
        <React.Fragment className="App">
            <ConnectedRouter history={history}>
                <Header />
                <Wrap>
                    <Suspense fallback={<Spinner />}>
                        <Route path='/audioWrite' exact component={AudioWrite} />
                        <Route path='/audioWrite/:category/:bookId' exact component={AudioWrite} />
                        <Route path='/book/' exact component={Book} />
                        <Route path='/book/:category' exact component={Book} />
                        <Route path='/bookDetail/:category/:bookId' exact component={BookDetail} />
                    </Suspense>
                </Wrap>
            </ConnectedRouter>
        </React.Fragment>
    );
}

const Wrap = styled.div`
    min-height: calc(100vh - 300px);
`

export default App;
```

- 설명
```
큰 애플리케이션은 일반적으로 많은 컴포넌트와 
유틸리티 메서드 및 타사 라이브러리 구성되는데 

필요할 때만 애플리케이션의 
다른 부분을 로드하려고 노력하지 않으면
사용자가 첫 페이지를 로드하는 즉시 
대규모 단일 JavaScript 번들이 사용자에게 전송

이러한 비효율적인 작업이 반복되면 성능에 영향
보이는 페이지만 로드한 후 다른 페이지에 접속했을 때
그곳의 데이터를 로드해오는 작업을 해주는 것
```

<br><br>

### `선정 방법`

```
'React.lazy'는 기본 페이지에 
즉시 필요하지 않은 컴포넌트나 사용자가 앱과 상호 작용할 때 
대화식으로 로드되는 컴포넌트에 탁월한 선택

여기에는 모달, 특정 대화 상자, 일부 양식, 
보조 보기 및 사용자 인터페이스의 초기 렌더링에 
중요하지 않은 앱의 기타 부분과 같은 컴포넌트가 포함
```
